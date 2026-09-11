# PLACEMENT – Session 9: Logical Reasoning
## Date: 10th September 2026

### Q1. W.A.C.P to print the Nth term in a Fibonacci series.

**Code:**

```c
#include <stdio.h>

int main() {
    int n, i, a = 0, b = 1, next;

    printf("Input : n = ");
    scanf("%d", &n);

    // Handle the first term as a special case
    if (n == 1) {
        printf("Output : %d\n", a);
        return 0;
    }

    // Loop starts from the 3rd term since a and b are already terms 1 and 2
    for (i = 3; i <= n; i++) {
        next = a + b;
        a = b;
        b = next;
    }

    printf("Output : %d\n", b);
    return 0;
}
```

**Line-by-Line Explanation:**

| Line | What it does |
|---|---|
| `int n, i, a = 0, b = 1, next;` | `a` and `b` hold Fibonacci terms 1 and 2 (0 and 1) at all times. `n` is the term the user wants. |
| `scanf("%d", &n);` | Reads which term to print. |
| `if (n == 1) { ... return 0; }` | Term 1 is always `0`, so it's handled separately and the function exits early. |
| `for (i = 3; i <= n; i++)` | Starts the loop from term 3 since terms 1 and 2 are already stored in `a` and `b`. |
| `next = a + b;` | Computes the new term as the sum of the previous two. |
| `a = b; b = next;` | Slides the window forward by one position. |
| `printf("Output : %d\n", b);` | After the loop, `b` holds the Nth term. |

**Example Trace (n = 6):**
Series: `0, 1, 1, 2, 3, 5` → loop runs for i = 3, 4, 5, 6, sliding (a, b) as `(0,1)→(1,1)→(1,2)→(2,3)→(3,5)`

**Output:** `5`

---

### Q2. W.A.C.P to print Non-Fibonacci series up to a given number n.

**Ex:**
```
Input  : 9
Output : 4, 6, 7, 9
```

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/74.jpg" alt="Non-Fibonacci series problem statement" width="500">
</div>

**Code:**

```c
#include <stdio.h>

int main() {
    int n, a = 1, b = 2, next;

    printf("Input : ");
    scanf("%d", &n);
    printf("Output : ");

    while (b <= n) {
        // Print all numbers strictly between a and b
        for (int i = a + 1; i < b; i++) {
            if (i <= n) {
                printf("%d ", i);
            }
        }

        // Slide the Fibonacci window forward
        next = a + b;
        a = b;
        b = next;
    }

    // In case 'n' falls between two Fibonacci numbers
    for (int i = a + 1; i <= n; i++) {
        printf("%d ", i);
    }

    printf("\n");
    return 0;
}
```

**Line-by-Line Explanation:**

| Line | What it does |
|---|---|
| `int a = 1, b = 2;` | Starts with the first two Fibonacci numbers, 1 and 2. |
| `while (b <= n)` | Keeps generating Fibonacci numbers as long as they stay within the limit `n`. |
| `for (int i = a + 1; i < b; i++)` | Walks through the "gap" between consecutive Fibonacci numbers — these gap numbers are the non-Fibonacci ones. |
| `if (i <= n) printf(...)` | Only prints the gap number if it is still within the requested limit. |
| `next = a + b; a = b; b = next;` | Slides the Fibonacci window forward to the next pair. |
| Final `for` loop | Handles the tail-end numbers after the last Fibonacci number ≤ n but before `n` itself, in case `n` sits between two Fibonacci numbers. |

**Trace (n = 9):**
Fibonacci numbers ≤ 9: `1, 2, 3, 5, 8`. Gaps: nothing between 1–2; `3` is skipped(none between 2–3); between 3–5 → `4`; between 5–8 → `6, 7`; after 8, tail loop → `9`.

**Output:** `4, 6, 7, 9`

---

### Q3. Given a positive integer n, print the n'th non-Fibonacci number.

**Ex:**
```
Input : n = 2      Input : n = 5
Output : 6         Output : 10
```

**Code:**

```c
#include <stdio.h>

int main() {
    int n, a = 1, b = 2, next, count = 0;

    printf("Input : n = ");
    scanf("%d", &n);

    while (count < n) {
        for (int i = a + 1; i < b; i++) {
            count++;
            if (count == n) {
                printf("Output : %d\n", i);
                return 0;
            }
        }

        next = a + b;
        a = b;
        b = next;
    }
    return 0;
}
```

**Line-by-Line Explanation:**

| Line | What it does |
|---|---|
| `int count = 0;` | Tracks how many non-Fibonacci numbers have been found so far. |
| `while (count < n)` | Keeps searching until the `n`th non-Fibonacci number is found. |
| `for (int i = a + 1; i < b; i++)` | Walks through the gap numbers between the current Fibonacci pair, exactly as in Q2. |
| `count++;` | Increments the count for every gap number found. |
| `if (count == n) { printf(...); return 0; }` | The moment the count matches `n`, that number is the answer — print and exit immediately. |
| `next = a + b; a = b; b = next;` | If not found yet, slide the Fibonacci window forward and repeat. |

**Trace (n = 5):**
Non-Fibonacci sequence: `4(1st), 6(2nd), 7(3rd), 9(4th), 10(5th)` → matches n=5.

**Output:** `10`

---

### Q4. Thief in Jail (Story Problem)

**Problem Statement:**

A thief is trying to escape from a jail. He has to cross N walls each with varying heights (every height is greater than 0). He climbs X feet every time. But, due to the slippery nature of those walls, every time he slips back by Y feet. Now the task is to calculate the total number of jumps required to cross all walls and escape from the jail.

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/75.jpg" alt="Thief in Jail problem statement" width="500">
</div>

**Examples:**
```
Input-1: heights[] = {11, 11}       X = 10; Y = 1;
Output : 4

Input-2: heights[] = {11, 10, 10, 9}  X = 10; Y = 1;
Output : 5
```

**Solution Logic:**

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/76.jpg" alt="Thief in Jail solution derivation" width="500">
</div>

- Let the height of a wall = `h`.
- To climb the **last** `X` units of a wall = **1 attempt** (he escapes over the top and doesn't slip back).
- To climb the remaining `h - X` units = `(h - X) / (X - Y)` attempts.
- That value can be fractional, so we round up to the next integer using `ceiling((h - X) / (X - Y))`.
- **Total attempts for one wall** = `ceil((h - X) / (float)(X - Y)) + 1`
- For `n` such walls, we sum the attempts across all of them (cumulative attempts).

**Code:**

```c
#include <stdio.h>
#include <math.h>

// Thief in Jail : C Code
// Arguments: Array Name, Array Size, value of X, value of Y
int noOfAttempt(int h[], int l, int x, int y)
{
    float na = 0, a;
    int i;
    for (i = 0; i < l; i++)
    {
        a = ceil((h[i] - x) / (float)(x - y)) + 1;
        na = na + a;
    }
    return na;
}

int main()
{
    int wh[] = {11, 10, 10, 9};
    printf("%d", noOfAttempt(wh, 4, 10, 1));

    return (0);
}
```

**Line-by-Line Explanation:**

| Line | What it does |
|---|---|
| `int noOfAttempt(int h[], int l, int x, int y)` | Takes the array of wall heights `h`, its length `l`, climb distance `x`, and slip distance `y`. |
| `float na = 0, a;` | `na` accumulates the total number of attempts across all walls; `a` holds the attempts for the current wall. |
| `for (i = 0; i < l; i++)` | Loops over every wall in the array. |
| `a = ceil((h[i] - x) / (float)(x - y)) + 1;` | Computes attempts for the current wall: attempts to cover `h[i] - x` (rounded up), plus 1 final attempt to clear the last `x` feet. |
| `na = na + a;` | Adds this wall's attempts to the running total. |
| `return na;` | Returns the cumulative attempt count (implicitly converted to `int` at the call site since `printf` uses `%d`). |
| `int wh[] = {11, 10, 10, 9};` | The wall heights for this test case (matches Input-2). |
| `noOfAttempt(wh, 4, 10, 1)` | Calls the function with 4 walls, climb = 10, slip = 1. |

**Manual Trace (Input-2, X=10, Y=1):**
| Wall height | Calculation | Attempts |
|---|---|---|
| 11 | `ceil(1/9) + 1 = 1 + 1` | 2 |
| 10 | `ceil(0/9) + 1 = 0 + 1` | 1 |
| 10 | same as above | 1 |
| 9  | `ceil(-1/9) + 1 = 0 + 1` | 1 |

Total = `2 + 1 + 1 + 1`

**Output:** `5`

---

### Q5. Interns (Password Authorization)

**Problem Statement:**

A company has N interns, interned from 1 to N. Each intern has been given a device which generates a password (number) everyday that will be used as a password for authorization at the office door every day in the morning. The internship lasts for 50 days, numbered from 0 to 49. Initially, on the first day, the number in the device of the `k`th intern will be `5000 * k`.

From the second day (i.e. `i = 1`) onward, a new number is generated everyday in each device as:

```
Day(i) = Day(i - 1) + 5000 + i
```

**Task:** Find the label of the intern from the given password.

**Input specification:**
- Input-1: `N`, number of interns
- Input-2: `P`, password used

**Output:** Returns the label of the intern for whom the password will be used.

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/77.jpg" alt="Interns problem statement" width="500">
</div>

**Example-1:**
```
Input-1: 2
```

**Solution Logic:**

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/78.jpg" alt="Interns solution derivation" width="500">
</div>

- Day-0 passwords are `5000 * intern_no`, i.e. `5000, 10000, 15000...`
- Day-n password formula: `Day(n) = Day(n-1) + 5000 + day_no`
- Analyzing any Day-n password shows it's always a **multiple of 5000 + sumOfDays**.
  - *Example:* `25000 + 10` is the password of intern-1 on the 4th day.
- `sumOfDays = 10 = (4*5)/2` → general form: `n*(n+1)/2`
- So, `sqrt(2 * sumOfDays)` lies between `n` and `n+1` → the **integer part** of that square root gives the `day_no`.
- Once `day_no` is known, subtracting it out and dividing by 5000 gives the **intern label**.

**Reference table** (Day # → password per intern label):

| Day \ Label | 1 | 2 | 3 | 4 |
|---|---|---|---|---|
| 0 | 5000 | 10000 | 15000 | 20000 |
| 1 | 10001 | 15001 | 20001 | 25001 |
| 2 | 15003 | 20003 | 25003 | 30003 |
| 3 | 20006 | 25006 | 30006 | 35006 |
| 4 | 25010 | 30010 | 35010 | 40010 |

**Code:**

```c
// Q? What is the use of N.

#include <stdio.h>
#include <stdlib.h>
#include <math.h>

int labelIntern(int n, int password)
{
    int sdays, dayno, label;
    sdays = password % 5000;

    dayno = sqrt(sdays * 2 - 1);
    label = (password - sdays - dayno * 5000) / 5000;

    return label;
}

int main()
{
    printf("%d", labelIntern(10, 25003));
    return (0);
}
```

**Line-by-Line Explanation:**

| Line | What it does |
|---|---|
| `int labelIntern(int n, int password)` | Takes total interns `n` (not actually used inside the function — that's the "Q? What is the use of N" comment left by the instructor) and the `password` to decode. |
| `sdays = password % 5000;` | Extracts the cumulative sum-of-days part, since it's always less than 5000 (max possible sum for 50 days is `50*51/2 = 1275`). |
| `dayno = sqrt(sdays * 2 - 1);` | Approximates the day number using the inverse of `n(n+1)/2`; truncation to `int` gives the correct `day_no`. |
| `label = (password - sdays - dayno * 5000) / 5000;` | Removes the `sumOfDays` and `day_no * 5000` parts from the password, leaving only the intern's label component, then divides by 5000 to isolate the label. |
| `return label;` | Returns the decoded intern label. |
| `labelIntern(10, 25003)` | Called with `n = 10` interns and `password = 25003`. |

**Manual Trace (password = 25003):**
- `sdays = 25003 % 5000 = 3`
- `dayno = sqrt(2*3 - 1) = sqrt(5) ≈ 2.236` → truncated to `2`
- `label = (25003 - 3 - 2*5000) / 5000 = 15000 / 5000 = 3`

**Output:** `3`

---

### Q6. W.A.C.P to find the trailing zeros in factorial of n. [AMAZON-CSA (2017) / Mettl]

**Examples:**
```
Ex-1: Input: n = 5     Output: 1     (5! = 120, one trailing 0)
Ex-2: Input: n = 10    Output: 2     (10! = 3628800, two trailing zeroes)
Ex-3: Input: n = 15    Output: 3     (15! = 1307674368000)
Ex-4: Input: n = 100   Output: 24
```

**Code:**

```c
#include <stdio.h>

int main() {
    int n, count = 0, i;

    printf("Input: n = ");
    scanf("%d", &n);

    // Count pairs of 5s in prime factors
    for (i = 5; n / i >= 1; i *= 5) {
        count = count + (n / i);
    }

    printf("Output: %d\n", count);
    return 0;
}
```

**Line-by-Line Explanation:**

| Line | What it does |
|---|---|
| `int n, count = 0, i;` | `count` accumulates the number of trailing zeros. |
| `for (i = 5; n / i >= 1; i *= 5)` | Loops through powers of 5 (5, 25, 125, 625...) as long as `n / i` is at least 1 — i.e., while that power of 5 can still divide into `n!`. |
| `count = count + (n / i);` | Adds how many multiples of the current power of 5 exist up to `n` (this correctly accounts for numbers like 25 or 125 that contribute more than one factor of 5). |
| `printf("Output: %d\n", count);` | Prints the total trailing zero count. |

**Why this works:** A trailing zero comes from a factor of 10 = 2 × 5. In any factorial, factors of 2 vastly outnumber factors of 5, so the count of trailing zeros equals the count of 5s in the prime factorization of `n!`.

**Trace (n = 100):**
- `i = 5`: `100/5 = 20` → count = 20
- `i = 25`: `100/25 = 4` → count = 24
- `i = 125`: `100/125 = 0` → loop stops

**Output:** `24`

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/79.jpg" alt="Trailing zeros examples" width="500">
</div>

---
---

<div align="center"> <h1 style="font-weight: bold;">@PSCodersHub</h1> </div>