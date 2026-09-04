# PLACEMENT – Session 7: Logical Reasoning
## Date: 3rd September 2026

### Q1. Pattern-1

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/56.jpg" alt="Pattern-1" width="500">
</div>

**Code:**

```c
#include <stdio.h>
int main()
{
    int i, j, n = 4;
    for(i = 1; i <= n; i++)
    {
        if(i % 2 == 0)
            printf("%2d ", i + 1);
        for(j = 1; j <= 6; j++)
            printf("%2d ", i);
        if(i % 2 != 0)
            printf("%2d ", i + 1);
        printf("\n");
    }
    return 0;
}
```

> **Explanation:**

- The row number `i` repeats as the main block of the row, printed `6` times via the fixed inner loop.
- A single boundary value `i + 1` is attached to one side of that block — placed as a **prefix** on even rows (`i % 2 == 0`) and as a **suffix** on odd rows — with modulo arithmetic deciding which side it lands on.

> **How we get there (rule-based):**

1. **Divide**: Rows run from `1` to `n`.
2. **Label**: Row index = `i`. Column index = `j`.
3. **Relationship**: Every row contains repeating values of `i`, bounded by one `i + 1`.
4. **Change**: The boundary number `i + 1` shifts position based on row parity.
5. **Formula**: Check `i % 2 == 0` for prefix printing, and `i % 2 != 0` for suffix printing.
6. **Generalize**: Wrap the constant inner loop with these modular conditions to alternate seamlessly.

---

### Q2. Pattern-2

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/57.jpg" alt="Pattern-2" width="500">
</div>

**Code:**

```c
#include <stdio.h>
#include <stdlib.h>
int main()
{
    int i, j, s = 3, n = 4;
    for(i = -n; i <= n; i++)
    {
        if(i != 0)
        {
            for(j = 1; j <= n - abs(i) + 1; j++)
                printf("%d", s + n - abs(i));
            printf("\n");
        }
    }
    return 0;
}
```

> **Explanation:**

- This utilizes the **Golden Loop** (`-n` to `n`) to generate a vertically mirrored structure without writing two separate loops.
- The sequence mathematically binds the starting value `s` to the absolute distance from the center.

> **How we get there (rule-based):**

1. **Divide**: A mirrored grid running from `-n` to `n`.
2. **Label**: Row index = `i` (signed).
3. **Relationship**: The printed value and column count both depend symmetrically on the distance from `0`.
4. **Change**: Row width shrinks as `abs(i)` grows.
5. **Formula**: Columns = `n - abs(i) + 1`; Value = `s + n - abs(i)`.
6. **Generalize**: Use `if(i != 0)` to skip the zero index, seamlessly joining the expanding top and shrinking bottom.

---

### Q3. Pattern-3

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/58.jpg" alt="Pattern-3" width="500">
</div>

**Code:**

```c
#include <stdio.h>
#include <stdlib.h>
int main() {
    int i, j, st, v, n = 4;
    for(i = -n; i <= n; i++)
    {
        if(i != 0)
        {
            v = n - abs(i) + 1;
            st = v * (v - 1) / 2;
            for(j = 1; j < v; j++)
                printf("%d*", st + j);
            printf("%d\n", st + j);
        }
    }
    return 0;
}
```

> **Explanation:**

- The arithmetic sum formula `v * (v - 1) / 2` gives the base offset `st`, from which the sequence `st + 1, st + 2, ... st + v` is generated for each row.
- Asterisks `*` are printed between numbers by terminating the inner loop one step early and printing the final number outside it.

> **How we get there (rule-based):**

1. **Divide**: Mirrored rows `-n` to `n`.
2. **Label**: Target row depth = `v`.
3. **Relationship**: The sequence continues incrementing through the structure.
4. **Change**: The starting number `st` offsets based on the cumulative count of previous row elements.
5. **Formula**: Calculate depth `v = n - abs(i) + 1`, then base `st = v * (v - 1) / 2`.
6. **Generalize**: Iterate `j` to generate the sequence `st + j`, utilizing the Golden Loop for symmetry.

---

### Q4. Pattern-4

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/59.jpg" alt="Pattern-4" width="500">
</div>

**Code:**

```c
#include <stdio.h>
int main()
{
    int i, j, n = 4, c = 1, end;
    for(i = 1; i <= n; i++)
    {
        end = c + i - 1;
        for(j = 1; j <= i; j++)
        {
            if(i % 2 != 0)
                printf("%d", c++);
            else
            {
                printf("%d", end--);
                c++;
            }
            if(j < i)
                printf("*");
        }
        printf("\n");
    }
    return 0;
}
```

> **Explanation:**

- A continuous counter `c` tracks the overall numeric sequence.
- Odd rows print the counter normally from left to right.
- Even rows calculate the end value of that row (`c + i - 1`) and print backwards, while still incrementing the main counter in the background.

> **How we get there (rule-based):**

1. **Divide**: `n` rows, where the `i`-th row has exactly `i` elements.
2. **Label**: Row index = `i`, Column index = `j`.
3. **Relationship**: Numbers are contiguous sequentially, but the printing direction reverses on alternating rows.
4. **Change**: Row 1 prints forward, Row 2 prints backward, Row 3 prints forward. The direction flips based on `i % 2`.
5. **Formula**: Left-to-right uses `c++`. Right-to-left uses a temporary `end` variable decremented, while advancing `c` behind the scenes.
6. **Generalize**: Wrap the inner loop with an `if(i % 2 != 0)` condition to toggle the print direction, keeping the `*` separator logic completely consistent across both states.

---

### Q5. Pattern-5

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/60.jpg" alt="Pattern-5" width="500">
</div>

**Code:**

```c
#include <stdio.h>
int main()
{
    int i, j, n = 4, st;

    // Print odd rows (1, 3, 5...)
    for(i = 1; i <= n; i += 2)
    {
        st = (i - 1) * n + 1;
        for(j = 1; j < n; j++)
            printf("%d*", st++);
        printf("%d\n", st);
    }

    // Print even rows (highest even down to 2)
    int start = (n % 2 == 0) ? n : n - 1;
    for(i = start; i >= 2; i -= 2)
    {
        st = (i - 1) * n + 1;
        for(j = 1; j < n; j++)
            printf("%d*", st++);
        printf("%d\n", st);
    }
    return 0;
}
```

> **Explanation:**

- The pattern visually shuffles rows. For `n = 4`, it prints all odd-numbered original rows (1, 3) first, traversing top-to-bottom.
- It then prints all even-numbered original rows (4, 2) in reverse order, traversing bottom-to-top.
- The starting number of any row is mathematically fixed to `(i - 1) * n + 1`.

> **How we get there (rule-based):**

1. **Divide**: `n` rows of exactly `n` columns each.
2. **Label**: Original row index = `i`, Column index = `j`.
3. **Relationship**: The grid is conceptually filled linearly from `1` to `n*n`, but the rows are rendered out of numerical sequence.
4. **Change**: Odd rows cluster at the top in ascending order; even rows cluster at the bottom in descending order.
5. **Formula**: Row start value = `(i - 1) * n + 1`.
6. **Generalize**: Break the outer loop into two separate loops: one incrementing `i += 2` starting from 1, and the other decrementing `i -= 2` starting from the maximum even row. Re-use the exact same inner loop logic for both.

> ---
> ---

<h1 align="center">Practice Questions</h1>
<p align="center"><em>C Programming — Loops, Numbers &amp; Patterns</em></p>

> **A note before you start:** Programs that work digit-by-digit (sum of digits, reverse, palindrome, Armstrong, Strong number) assume the input is a **non-negative** whole number. In C, `%` and `/` behave inconsistently with negative numbers, so entering something like `-121` won't reverse or check cleanly. This isn't a mistake in the code below — it's just a boundary these simple versions don't handle, and it's good to know about before it surprises you later.

---

## Question 1
**Question:** W.A.C.P to print all natural numbers from 1 to n.

**Code:**
```c
#include <stdio.h>
int main() {
    int n, i;
    printf("Enter n: ");
    scanf("%d", &n);

    for (i = 1; i <= n; i++) {
        printf("%d ", i);
    }
    return 0;
}
```

**Line-by-line breakdown:**
- `#include <stdio.h>` — gives us `printf`/`scanf`.
- `int n, i;` — `n` holds the limit, `i` is the loop counter.
- `scanf("%d", &n);` — reads the limit into `n`. The `&` gives `scanf` the *address* of `n` so it can write into it.
- `for (i = 1; i <= n; i++)` — three parts: **start** (`i = 1`), **condition** (`i <= n`, checked before every pass), **step** (`i++`, runs after every pass).
- `printf("%d ", i);` — prints the current `i` followed by a space.

**Concept & Pattern:**
This is the "start, condition, step" skeleton that almost every question below builds on. Once this feels automatic, you can adapt it to count differently, skip numbers, or track a running total — which is exactly what the rest of this set does.

**Output:**
```
Enter n: 5
1 2 3 4 5 
```

---

## Question 2
**Question:** W.A.C.P to print all natural numbers in reverse (from n to 1).

**Code:**
```c
#include <stdio.h>
int main() {
    int n, i;
    printf("Enter n: ");
    scanf("%d", &n);

    for (i = n; i >= 1; i--) {
        printf("%d ", i);
    }
    return 0;
}
```

**Line-by-line breakdown:**
- `for (i = n; i >= 1; i--)` — starts at `n` instead of 1, keeps going while `i` is still `>= 1`, and **decreases** by 1 each pass (`i--`).
- Everything else is identical to Question 1 — same `printf`, same idea, just running backward.

**Concept & Pattern:**
To count down, flip three things: the start value, the comparison direction, and the step direction. The body of the loop (what you print) doesn't need to change at all.

**Output:**
```
Enter n: 5
5 4 3 2 1 
```

---

## Question 3
**Question:** W.A.C.P to print all even numbers between 1 to 100.

**Code:**
```c
#include <stdio.h>
int main() {
    int i;
    for (i = 2; i <= 100; i += 2) {
        printf("%d ", i);
    }
    return 0;
}
```

**Line-by-line breakdown:**
- `for (i = 2; i <= 100; i += 2)` — starts at 2 (first even number), runs through 100, and steps by 2 each time (`i += 2` means "add 2 to i").
- Because every step lands exactly on an even number, there's no need for an `if` check at all.

**Concept & Pattern:**
Changing the *step size* is often better than looping over every number and filtering with `if`. This version never even looks at odd numbers — it's both simpler and faster than checking `i % 2 == 0`.

**Output:**
```
2 4 6 8 10 ... 98 100
```

---

## Question 4
**Question:** W.A.C.P to print all odd numbers between 1 to 100.

**Code:**
```c
#include <stdio.h>
int main() {
    int i;
    for (i = 1; i <= 100; i += 2) {
        printf("%d ", i);
    }
    return 0;
}
```

**Line-by-line breakdown:**
- `for (i = 1; i <= 100; i += 2)` — same stepping trick as Question 3, just shifted by starting at 1 instead of 2.

**Concept & Pattern:**
Odd and even numbers are the same "skip by 2" pattern, just offset by one starting value. Recognizing that Questions 3 and 4 are the same loop with one number changed is the real lesson here.

**Output:**
```
1 3 5 7 9 ... 97 99
```

---

## Question 5
**Question:** W.A.C.P to find sum of all natural numbers between 1 to n.

**Code:**
```c
#include <stdio.h>
int main() {
    int n, i, sum = 0;
    printf("Enter n: ");
    scanf("%d", &n);

    for (i = 1; i <= n; i++) {
        sum = sum + i;
    }
    printf("Sum = %d", sum);
    return 0;
}
```

**Line-by-line breakdown:**
- `int n, i, sum = 0;` — `sum` **must** start at 0, since it's about to collect a running total.
- `sum = sum + i;` — takes whatever `sum` currently is and adds the current `i` to it. This line runs once per loop pass.
- After the loop ends, `sum` holds the total of every number that passed through.

**Concept & Pattern:**
This is the **accumulator pattern** — a variable that starts at a "neutral" value (0 for addition, 1 for multiplication) and updates itself once per iteration. You'll reuse this exact idea in nearly every question from here on.

**Output:**
```
Enter n: 5
Sum = 15
```

---

## Question 6
**Question:** W.A.C.P to find sum of all even numbers between 1 to n.

**Code:**
```c
#include <stdio.h>
int main() {
    int n, i, sum = 0;
    printf("Enter n: ");
    scanf("%d", &n);

    for (i = 2; i <= n; i += 2) {
        sum = sum + i;
    }
    printf("Sum of even numbers = %d", sum);
    return 0;
}
```

**Line-by-line breakdown:**
- `for (i = 2; i <= n; i += 2)` — the "start at 2, step by 2" trick from Question 3.
- `sum = sum + i;` — the accumulator from Question 5.

**Concept & Pattern:**
Two patterns you already know (skip-stepping + accumulating) combined into one program. This is how most "harder" questions are built — not new ideas, just familiar pieces stacked together.

**Output:**
```
Enter n: 10
Sum of even numbers = 30
```

---

## Question 7
**Question:** W.A.C.P to print multiplication table of any number.

**Code:**
```c
#include <stdio.h>
int main() {
    int n, i;
    printf("Enter a number: ");
    scanf("%d", &n);

    for (i = 1; i <= 10; i++) {
        printf("%d x %d = %d\n", n, i, n * i);
    }
    return 0;
}
```

**Line-by-line breakdown:**
- `for (i = 1; i <= 10; i++)` — always runs exactly 10 times, regardless of `n`. `i` is the multiplier, not the number being tabled.
- `printf("%d x %d = %d\n", n, i, n * i);` — three values plugged into one format string: `n`, `i`, and the product `n * i`, followed by `\n` to start a new line each time.

**Concept & Pattern:**
Note that `n` (the value the user typed) stays fixed throughout, while `i` is the thing that changes. Mixing up which variable should move and which should stay fixed is a very common beginner bug — always ask "what actually changes each pass?"

**Output:**
```
Enter a number: 5
5 x 1 = 5
5 x 2 = 10
5 x 3 = 15
...
5 x 10 = 50
```

---

## Question 8
**Question:** W.A.C.P to find all factors of a number.

**Code:**
```c
#include <stdio.h>
int main() {
    int n, i;
    printf("Enter a number: ");
    scanf("%d", &n);

    for (i = 1; i <= n; i++) {
        if (n % i == 0) {
            printf("%d ", i);
        }
    }
    return 0;
}
```

**Line-by-line breakdown:**
- `for (i = 1; i <= n; i++)` — tests every candidate number from 1 to `n`.
- `if (n % i == 0)` — `%` gives the **remainder** of `n ÷ i`. A remainder of 0 means `i` divides `n` exactly, so `i` is a factor.
- `printf("%d ", i);` — only runs when the `if` condition is true.

**Concept & Pattern:**
`%` (modulo) is the single most useful operator for these number-theory questions — it's how you test "does this divide evenly?" You'll see it again and again below.

**Output:**
```
Enter a number: 12
1 2 3 4 6 12 
```

---

## Question 9
**Question:** W.A.C.P to count number of factors of a given number.

**Code:**
```c
#include <stdio.h>
int main() {
    int n, i, count = 0;
    printf("Enter a number: ");
    scanf("%d", &n);

    for (i = 1; i <= n; i++) {
        if (n % i == 0) {
            count++;
        }
    }
    printf("Number of factors = %d", count);
    return 0;
}
```

**Line-by-line breakdown:**
- Same factor-detection `if` as Question 8.
- `count++;` — short for `count = count + 1`. Runs only when a factor is found.

**Concept & Pattern:**
This is the **counting pattern**: instead of printing each match, you just tally how many matches occurred. It's the accumulator pattern's sibling — accumulate a *count* instead of a *sum*.

**Output:**
```
Enter a number: 12
Number of factors = 6
```

---

## Question 10
**Question:** W.A.C.P to check whether a number is Prime number or not.

**Code:**
```c
#include <stdio.h>
int main() {
    int n, i, isPrime = 1;
    printf("Enter a number: ");
    scanf("%d", &n);

    if (n <= 1) {
        isPrime = 0;
    } else {
        for (i = 2; i <= n / 2; i++) {
            if (n % i == 0) {
                isPrime = 0;
                break;
            }
        }
    }

    if (isPrime)
        printf("%d is a Prime number", n);
    else
        printf("%d is NOT a Prime number", n);
    return 0;
}
```

**Line-by-line breakdown:**
- `int isPrime = 1;` — a **flag variable**: starts by *assuming* the number is prime.
- `if (n <= 1) isPrime = 0;` — 0 and 1 (and negatives) are never prime, handled up front as a special case.
- `for (i = 2; i <= n / 2; i++)` — no factor of `n` can be larger than `n/2` (other than `n` itself), so we don't need to check past that point.
- `if (n % i == 0) { isPrime = 0; break; }` — the moment a factor is found, the number can't be prime, so we flip the flag **and immediately `break`** out of the loop — no point checking further.

**Concept & Pattern:**
This introduces two important ideas together: the **flag variable** (a yes/no answer built up across a loop) and `break` (leaving a loop early once you already have your answer). Checking only up to `n/2` instead of `n` is a small but real efficiency habit worth keeping.

**Output:**
```
Enter a number: 7
7 is a Prime number
```

---

## Question 11
**Question:** W.A.C.P to check whether a number is Perfect number or not.

**Code:**
```c
#include <stdio.h>
int main() {
    int n, i, sum = 0;
    printf("Enter a number: ");
    scanf("%d", &n);

    for (i = 1; i < n; i++) {
        if (n % i == 0) {
            sum = sum + i;
        }
    }

    if (sum == n)
        printf("%d is a Perfect number", n);
    else
        printf("%d is NOT a Perfect number", n);
    return 0;
}
```

**Line-by-line breakdown:**
- `for (i = 1; i < n; i++)` — notice `i < n`, **not** `i <= n`. This deliberately excludes `n` itself from being counted as its own factor.
- `sum = sum + i;` — the accumulator pattern again, this time collecting only proper factors.
- `if (sum == n)` — a perfect number is exactly equal to the sum of its own (proper) factors, e.g. 6 = 1+2+3.

**Concept & Pattern:**
A one-character difference (`<` vs `<=`) completely changes what a loop computes. Always double-check loop boundaries against what the definition actually requires.

**Output:**
```
Enter a number: 6
6 is a Perfect number
```

---

## Question 12
**Question:** W.A.C.P to calculate factorial of a number.

**Code:**
```c
#include <stdio.h>
int main() {
    int n, i;
    long long fact = 1;
    printf("Enter a number: ");
    scanf("%d", &n);

    for (i = 1; i <= n; i++) {
        fact = fact * i;
    }
    printf("Factorial = %lld", fact);
    return 0;
}
```

**Line-by-line breakdown:**
- `long long fact = 1;` — starts at **1**, not 0 (multiplying by 0 would zero everything out forever). `long long` gives extra range because factorials grow explosively fast (13! already overflows a normal `int`).
- `fact = fact * i;` — the multiplication version of the accumulator pattern.
- `printf("Factorial = %lld", fact);` — `%lld` is the correct format specifier for `long long`; using `%d` here would print garbage.

**Concept & Pattern:**
Same accumulator idea as sum, but for multiplication. The two things to get right every time: the correct starting value (0 for `+`, 1 for `*`) and a data type large enough to hold the result.

**Output:**
```
Enter a number: 5
Factorial = 120
```

---

## Question 13
**Question:** W.A.C.P to find power of a number.

**Code:**
```c
#include <stdio.h>
int main() {
    int base, exp, i;
    long long result = 1;
    printf("Enter base and exponent: ");
    scanf("%d %d", &base, &exp);

    for (i = 1; i <= exp; i++) {
        result = result * base;
    }
    printf("%d ^ %d = %lld", base, exp, result);
    return 0;
}
```

**Line-by-line breakdown:**
- `scanf("%d %d", &base, &exp);` — one `scanf` call can read two values separated by a space.
- `result = result * base;` — multiplies `result` by `base`, repeated `exp` times by the loop.
- If `exp` is 0, the loop body never runs, and `result` correctly stays 1 (anything to the power 0 is 1).

**Concept & Pattern:**
Same multiplication-accumulator as factorial, just multiplying by a fixed `base` each time instead of a changing `i`.

**Output:**
```
Enter base and exponent: 2 5
2 ^ 5 = 32
```

---

## Question 14
**Question:** W.A.C.P to count number of digits in a number.

**Code:**
```c
#include <stdio.h>
int main() {
    int n, count = 0;
    printf("Enter a number: ");
    scanf("%d", &n);

    if (n == 0) count = 1;

    while (n != 0) {
        n = n / 10;
        count++;
    }
    printf("Number of digits = %d", count);
    return 0;
}
```

**Line-by-line breakdown:**
- `if (n == 0) count = 1;` — special case: 0 has one digit, but the `while` loop below would never run for `n == 0`, so this line catches it separately.
- `while (n != 0)` — a `while` loop is used (instead of `for`) because we don't know in advance how many digits there are.
- `n = n / 10;` — integer division in C **drops** the remainder, so dividing by 10 chops off the last digit (`12345 / 10` becomes `1234`).
- `count++;` — one digit removed = one digit counted.

**Concept & Pattern:**
This is the first "digit extraction" question — the `/ 10` trick to peel off digits one at a time is the foundation for sum-of-digits, reverse, palindrome, and Armstrong checks that follow. `for` vs `while`: use `for` when you know the number of repetitions up front, `while` when the loop should stop based on a changing condition instead.

**Output:**
```
Enter a number: 12345
Number of digits = 5
```

---

## Question 15
**Question:** W.A.C.P to calculate sum of digits of a number.

**Code:**
```c
#include <stdio.h>
int main() {
    int n, digit, sum = 0;
    printf("Enter a number: ");
    scanf("%d", &n);

    while (n != 0) {
        digit = n % 10;
        sum = sum + digit;
        n = n / 10;
    }
    printf("Sum of digits = %d", sum);
    return 0;
}
```

**Line-by-line breakdown:**
- `digit = n % 10;` — `% 10` gives the **last** digit of `n` (the remainder when dividing by 10).
- `sum = sum + digit;` — accumulator pattern, collecting digits instead of whole numbers.
- `n = n / 10;` — removes that last digit (from Question 14), so the next loop pass sees the next digit.

**Concept & Pattern:**
"Grab last digit with `% 10` → use it → remove it with `/ 10`" is a three-step rhythm that visits every digit exactly once, from right to left. Memorize this rhythm — it's reused directly in the next several questions.

**Output:**
```
Enter a number: 123
Sum of digits = 6
```

---

## Question 16
**Question:** W.A.C.P to enter a number and print its reverse.

**Code:**
```c
#include <stdio.h>
int main() {
    int n, digit, reverse = 0;
    printf("Enter a number: ");
    scanf("%d", &n);

    while (n != 0) {
        digit = n % 10;
        reverse = reverse * 10 + digit;
        n = n / 10;
    }
    printf("Reversed number = %d", reverse);
    return 0;
}
```

**Line-by-line breakdown:**
- `digit = n % 10;` — same digit extraction as Question 15.
- `reverse = reverse * 10 + digit;` — the key new line: `reverse * 10` shifts every digit already collected one place to the *left* (making room), then `+ digit` drops the new digit into the now-empty units place.
- `n = n / 10;` — removes the digit we just used.

**Concept & Pattern:**
Instead of adding digits together (Question 15), we're now **building a new number** out of them, one digit at a time, from the right end. The `x * 10 + digit` trick for "append a digit" is worth remembering on its own — it shows up anywhere you're constructing a number digit-by-digit.

**Output:**
```
Enter a number: 123
Reversed number = 321
```

---

## Question 17
**Question:** W.A.C.P to check whether a number is palindrome or not. (Ex: 121)

**Code:**
```c
#include <stdio.h>
int main() {
    int n, original, digit, reverse = 0;
    printf("Enter a number: ");
    scanf("%d", &n);
    original = n;

    while (n != 0) {
        digit = n % 10;
        reverse = reverse * 10 + digit;
        n = n / 10;
    }

    if (original == reverse)
        printf("%d is a Palindrome", original);
    else
        printf("%d is NOT a Palindrome", original);
    return 0;
}
```

**Line-by-line breakdown:**
- `original = n;` — **critical line**: saves a copy of the input *before* the reversing loop destroys `n`.
- The `while` loop is identical to Question 16 — it reverses `n` into `reverse`.
- `if (original == reverse)` — a palindrome reads the same both directions, so if the reversed version matches the saved original, it's a palindrome.

**Concept & Pattern:**
Whenever a loop is going to consume/modify a variable you still need later for comparison, save a copy first. Forgetting this line is one of the most common beginner mistakes in exactly this kind of problem.

**Output:**
```
Enter a number: 121
121 is a Palindrome
```

---

## Question 18
**Question:** W.A.C.P to check whether a number is Armstrong number or not (for 3 digit number). Ex: 153, 370, 371, 407

**Code:**
```c
#include <stdio.h>
int main() {
    int n, original, digit, sum = 0;
    printf("Enter a 3-digit number: ");
    scanf("%d", &n);
    original = n;

    while (n != 0) {
        digit = n % 10;
        sum = sum + (digit * digit * digit);
        n = n / 10;
    }

    if (sum == original)
        printf("%d is an Armstrong number", original);
    else
        printf("%d is NOT an Armstrong number", original);
    return 0;
}
```

**Line-by-line breakdown:**
- `original = n;` — same "save before destroying" habit as Question 17.
- `digit = n % 10;` then `n = n / 10;` — the usual digit-extraction rhythm.
- `sum = sum + (digit * digit * digit);` — instead of adding the digit itself, we add its **cube**.

**Concept & Pattern:**
A 3-digit Armstrong number equals the sum of the cubes of its own digits (153 = 1³+5³+3³). Notice this is exactly the "sum of digits" pattern from Question 15, with one line changed (`digit` → `digit³`). Most of these "special number" checks are the same skeleton with one transformation swapped in.

**Output:**
```
Enter a 3-digit number: 153
153 is an Armstrong number
```

---

## Question 19
**Question:** Check Armstrong number of N digit. Ex: 1, ..., 9, 153, 370, 371, 407, 1634, 8208

**Code:**
```c
#include <stdio.h>
#include <math.h>
int main() {
    int n, original, digit, numDigits = 0, temp;
    long long sum = 0;
    printf("Enter a number: ");
    scanf("%d", &n);
    original = n;

    // Step 1: count digits
    temp = n;
    while (temp != 0) {
        temp = temp / 10;
        numDigits++;
    }

    // Step 2: sum of (each digit ^ numDigits)
    temp = n;
    while (temp != 0) {
        digit = temp % 10;
        sum = sum + (long long)pow(digit, numDigits);
        temp = temp / 10;
    }

    if (sum == original)
        printf("%d is an Armstrong number", original);
    else
        printf("%d is NOT an Armstrong number", original);
    return 0;
}
```

**Line-by-line breakdown:**
- `#include <math.h>` — required for `pow()`.
- `temp = n;` (before Step 1) — a working copy, so the digit-counting loop doesn't disturb `n`, which we still need for Step 2.
- **Step 1's** `while` loop counts digits exactly like Question 14.
- `temp = n;` again before Step 2 — resets the working copy since Step 1's loop drained it to 0.
- `sum = sum + (long long)pow(digit, numDigits);` — raises `digit` to the power `numDigits` and adds it to `sum`.

**Concept & Pattern:**
This generalizes Question 18 from exactly-3-digits to *any* number of digits — the exponent is no longer hardcoded as 3, it's computed from the number itself. Two passes are needed because you must know the total digit count *before* you can raise each digit to that power.

> ⚠️ **A real bug to watch out for:** `pow()` works with `double`s, and floating-point math isn't perfectly exact. For example, `pow(4, 3)` can sometimes come out as `63.999999...` instead of `64`, and casting that to `(long long)` truncates it down to `63` — silently giving the wrong answer. For small digits (0–9) and small exponents this is rare in practice, but if you ever see a "should-be-Armstrong" number fail the check, this is the first thing to suspect. The safer fix is to write your own integer power function instead of using `pow()` — see the bonus snippet at the end of this document.

**Output:**
```
Enter a number: 1634
1634 is an Armstrong number
```

---

## Question 20
**Question:** W.A.C.P to print Fibonacci series up to n terms.

**Code:**
```c
#include <stdio.h>
int main() {
    int n, i, a = 0, b = 1, next;
    printf("Enter number of terms: ");
    scanf("%d", &n);

    for (i = 1; i <= n; i++) {
        printf("%d ", a);
        next = a + b;
        a = b;
        b = next;
    }
    return 0;
}
```

**Line-by-line breakdown:**
- `int a = 0, b = 1, next;` — `a` is the "current" term, `b` is the "next" term waiting in line.
- `printf("%d ", a);` — print the current term **before** updating anything.
- `next = a + b;` — compute the term that comes after `b`.
- `a = b; b = next;` — slide the window forward by one step: what was "next" becomes "current," and the newly computed value becomes the new "next."

**Concept & Pattern:**
This is the **sliding-window** pattern: keep only as many variables as you need to compute the next value, and shift them forward each iteration, rather than storing the entire sequence in an array.

**Output:**
```
Enter number of terms: 7
0 1 1 2 3 5 8 
```

---

## Question 21
**Question:** W.A.C.P to print n'th Fibonacci term.

**Code:**
```c
#include <stdio.h>
int main() {
    int n, i, a = 0, b = 1, next;
    printf("Enter n: ");
    scanf("%d", &n);

    if (n == 1) {
        printf("Fibonacci term = %d", a);
        return 0;
    }

    for (i = 3; i <= n; i++) {
        next = a + b;
        a = b;
        b = next;
    }
    printf("Fibonacci term = %d", b);
    return 0;
}
```

**Line-by-line breakdown:**
- `if (n == 1) { ... return 0; }` — special case, since the loop below starts from `i = 3` and would never fire for `n == 1`.
- `for (i = 3; i <= n; i++)` — before the loop, `a` already holds term 1 and `b` already holds term 2, so the loop only needs to run for terms 3 through `n`. Starting the loop at `i = 2` instead (an easy mistake to make) would slide the window one step too far and give the *wrong* term — always check a loop bound like this against a small example by hand.
- The loop body uses the exact same sliding-window update as Question 20 — it's just not printing every step, only computing forward.
- `printf("Fibonacci term = %d", b);` — after the loop, `b` (not `a`) holds the most recently computed term, which is the answer. When `n == 2`, the loop body never runs at all, and `b` correctly stays at its initial value of 1 — no separate case needed for `n == 2`.

**Concept & Pattern:**
When you only need the *final* result of a repeated process (not every intermediate step), you can reuse the same loop logic and simply drop the `printf` from inside it, printing once at the end instead.

**Output:**
```
Enter n: 7
Fibonacci term = 8
```

---

## Question 22
**Question:** W.A.C.P to print sum of n different numbers / values.

**Code:**
```c
#include <stdio.h>
int main() {
    int n, i, num, sum = 0;
    printf("Enter how many numbers: ");
    scanf("%d", &n);

    for (i = 1; i <= n; i++) {
        printf("Enter number %d: ", i);
        scanf("%d", &num);
        sum = sum + num;
    }
    printf("Sum = %d", sum);
    return 0;
}
```

**Line-by-line breakdown:**
- `scanf("%d", &n);` — first asks *how many* numbers are coming, so the loop knows when to stop.
- Inside the loop: prompt, then `scanf` reads one value into `num` each pass.
- `sum = sum + num;` — same accumulator pattern as Question 5, but now the numbers come from the user instead of being `1, 2, 3, ...` automatically.

**Concept & Pattern:**
Compare this to Question 5: there, the loop counter itself *was* the data being summed. Here, the loop counter only controls *how many times to ask* — the actual data (`num`) is separate and typed in fresh each time.

**Output:**
```
Enter how many numbers: 3
Enter number 1: 10
Enter number 2: 20
Enter number 3: 5
Sum = 35
```

---

## Question 23
**Question:** W.A.C.P to print Sum of the Positive and Negative numbers from given set of numbers. (until pressed zero)

**Code:**
```c
#include <stdio.h>
int main() {
    int num, posSum = 0, negSum = 0;

    do {
        printf("Enter a number (0 to stop): ");
        scanf("%d", &num);

        if (num > 0)
            posSum = posSum + num;
        else if (num < 0)
            negSum = negSum + num;

    } while (num != 0);

    printf("Sum of positive numbers = %d\n", posSum);
    printf("Sum of negative numbers = %d\n", negSum);
    return 0;
}
```

**Line-by-line breakdown:**
- `do { ... } while (num != 0);` — a **do-while** loop runs its body *first*, then checks the condition. That's a natural fit here: we must read at least one number before we can decide whether to stop.
- `if (num > 0) ... else if (num < 0) ...` — sorts each entry into the positive or negative bucket. (A plain `0` matches neither branch, and also ends the loop via the `while` condition.)
- Because prompting and reading live inside the loop body, there's no need to duplicate the `scanf` call outside the loop — a `do-while` naturally handles "read once, then keep reading until a condition is met" in a single block.

**Concept & Pattern:**
Choose `do-while` over a plain `while` specifically when the loop body must run at least once *before* there's anything to check — like reading the very first input. It also tends to avoid repeating the same "read" code both before and inside the loop.

**Output:**
```
Enter a number (0 to stop): 5
Enter a number (0 to stop): -3
Enter a number (0 to stop): 10
Enter a number (0 to stop): -7
Enter a number (0 to stop): 0
Sum of positive numbers = 15
Sum of negative numbers = -10
```

---

## Question 24
**Question:** W.A.C.P to find the Largest of N numbers.

**Code:**
```c
#include <stdio.h>
int main() {
    int n, i, num, largest;
    printf("Enter how many numbers: ");
    scanf("%d", &n);

    printf("Enter number 1: ");
    scanf("%d", &largest);

    for (i = 2; i <= n; i++) {
        printf("Enter number %d: ", i);
        scanf("%d", &num);
        if (num > largest) {
            largest = num;
        }
    }
    printf("Largest number = %d", largest);
    return 0;
}
```

**Line-by-line breakdown:**
- The **first** number is read directly into `largest`, treating it as the best guess so far.
- `for (i = 2; ...)` — the loop starts from the *second* number, since the first is already accounted for.
- `if (num > largest) largest = num;` — every time a bigger number shows up, it replaces the current champion.

**Concept & Pattern:**
This is the classic **running-maximum** pattern: seed with the first real value (never an arbitrary guess like 0, which would break for all-negative input), then compare-and-replace on every subsequent value.

**Output:**
```
Enter how many numbers: 4
Enter number 1: 12
Enter number 2: 45
Enter number 3: 7
Enter number 4: 30
Largest number = 45
```

---

## Question 25
**Question:** W.A.C.P to find Second Largest number from N numbers.

**Code:**
```c
#include <stdio.h>
int main() {
    int n, i, num, largest, secondLargest;
    printf("Enter how many numbers: ");
    scanf("%d", &n);

    printf("Enter number 1: ");
    scanf("%d", &largest);
    secondLargest = -999999; // very small placeholder

    for (i = 2; i <= n; i++) {
        printf("Enter number %d: ", i);
        scanf("%d", &num);

        if (num > largest) {
            secondLargest = largest;
            largest = num;
        } else if (num > secondLargest && num != largest) {
            secondLargest = num;
        }
    }
    printf("Second Largest number = %d", secondLargest);
    return 0;
}
```

**Line-by-line breakdown:**
- `secondLargest = -999999;` — a placeholder small enough that any realistic input will beat it. (For very negative real-world data you'd want an even smaller placeholder — worth keeping in mind.)
- `if (num > largest)` — a **new overall largest** was found: the *old* largest gets demoted to `secondLargest` before `largest` is overwritten. Order matters here — demote first, then update.
- `else if (num > secondLargest && num != largest)` — otherwise, if it still beats the current second place (and isn't just a duplicate of the largest), it becomes the new `secondLargest`.

**Concept & Pattern:**
An extension of Question 24's running-maximum, now tracking *two* ranks at once. This "demote, then promote" order in the `if` branch is the part beginners most often get backwards — always save the value that's about to be overwritten before overwriting it. Note this version assumes the input values are distinct; duplicate values need extra handling not covered here.

**Output:**
```
Enter how many numbers: 4
Enter number 1: 12
Enter number 2: 45
Enter number 3: 7
Enter number 4: 30
Second Largest number = 30
```

---

## Question 26
**Question:** W.A.C.P to find HCF (GCD) of two numbers.

**Code:**
```c
#include <stdio.h>
int main() {
    int a, b, temp, x, y;
    printf("Enter two numbers: ");
    scanf("%d %d", &a, &b);

    x = a;
    y = b;
    while (y != 0) {
        temp = y;
        y = x % y;
        x = temp;
    }
    printf("HCF = %d", x);
    return 0;
}
```

**Line-by-line breakdown:**
- `x = a; y = b;` — working copies, so the original inputs `a` and `b` stay untouched (useful if you need to print them later).
- `while (y != 0)` — keep going as long as `y` isn't zero.
- `temp = y; y = x % y; x = temp;` — this is the **Euclidean Algorithm**: replace the pair `(x, y)` with `(y, x % y)`, over and over.
- When `y` finally becomes 0, `x` holds the answer.

**Concept & Pattern:**
The Euclidean Algorithm is dramatically faster than checking every number from 1 up to the smaller input — it typically finishes in a handful of steps even for huge numbers, because it shrinks the problem quickly using division instead of counting one by one. Worth learning properly, since it reappears throughout number theory and cryptography.

**Output:**
```
Enter two numbers: 12 18
HCF = 6
```

---

## Question 27
**Question:** W.A.C.P to find LCM (Least Common Multiple) of two numbers.

**Code:**
```c
#include <stdio.h>
int main() {
    int a, b, x, y, temp, hcf;
    printf("Enter two numbers: ");
    scanf("%d %d", &a, &b);

    x = a; y = b;
    while (y != 0) {
        temp = y;
        y = x % y;
        x = temp;
    }
    hcf = x;

    printf("LCM = %d", (a * b) / hcf);
    return 0;
}
```

**Line-by-line breakdown:**
- The `while` loop is exactly the Euclidean Algorithm from Question 26, computing `hcf`.
- `printf("LCM = %d", (a * b) / hcf);` — uses the identity **LCM(a, b) = (a × b) ÷ HCF(a, b)** to get the answer directly, with no separate searching loop needed.

**Concept & Pattern:**
Rather than hunting for the LCM by testing candidate multiples one at a time, this reuses a result you already know how to compute (HCF) and plugs it into a formula. Recognizing relationships like this — turning one problem into a quick calculation from another — is a big part of writing efficient code.

> Note: for large `a` and `b`, `a * b` can overflow a plain `int` before the division happens. If you expect large inputs, compute it as `((long long)a * b) / hcf` instead.

**Output:**
```
Enter two numbers: 4 6
LCM = 12
```

---

## Question 28
**Question:** W.A.C.P to print all Palindrome numbers between 1 to n.

**Code:**
```c
#include <stdio.h>
int main() {
    int n, num, original, digit, reverse, temp;
    printf("Enter n: ");
    scanf("%d", &n);

    for (num = 1; num <= n; num++) {
        original = num;
        reverse = 0;
        temp = num;

        while (temp != 0) {
            digit = temp % 10;
            reverse = reverse * 10 + digit;
            temp = temp / 10;
        }

        if (original == reverse) {
            printf("%d ", original);
        }
    }
    return 0;
}
```

**Line-by-line breakdown:**
- `for (num = 1; num <= n; num++)` — the **outer** loop tries every candidate from 1 to `n`.
- `temp = num;` — a fresh working copy for *each* candidate, so `original` stays intact for the final comparison.
- The **inner** `while` loop reverses `temp` — identical logic to Question 16, just running once per candidate instead of once total.
- `if (original == reverse)` — the single-number check from Question 17, reused inside the loop.

**Concept & Pattern:**
This is a **nested-loop pattern**: take a check you already wrote for *one* number (Question 17) and wrap it inside an outer loop that runs it for *every* number in a range. You'll see this exact structure repeated for Armstrong (Q30), Strong (Q31), Perfect (Q32), and Prime (Q33) numbers below — same skeleton, different inner check.

**Output:**
```
Enter n: 150
1 2 3 4 5 6 7 8 9 11 22 33 44 55 66 77 88 99 101 111 121 131 141 
```

---

## Question 29
**Question:** W.A.C.P to check whether a number is Strong number or not.

**Code:**
```c
#include <stdio.h>
int main() {
    int n, original, digit, sum = 0, fact, i;
    printf("Enter a number: ");
    scanf("%d", &n);
    original = n;

    while (n != 0) {
        digit = n % 10;

        fact = 1;
        for (i = 1; i <= digit; i++) {
            fact = fact * i;
        }

        sum = sum + fact;
        n = n / 10;
    }

    if (sum == original)
        printf("%d is a Strong number", original);
    else
        printf("%d is NOT a Strong number", original);
    return 0;
}
```

**Line-by-line breakdown:**
- Outer `while` loop: the usual digit-extraction rhythm (`% 10`, then `/ 10`).
- `fact = 1; for (i = 1; i <= digit; i++) fact = fact * i;` — a small **inner loop** computing the factorial of just that one digit, using the exact factorial logic from Question 12.
- `sum = sum + fact;` — adds that digit's factorial into the running total.

**Concept & Pattern:**
A Strong number equals the sum of the factorials of its own digits (145 = 1! + 4! + 5! = 1 + 24 + 120). This nests one earlier pattern (factorial) inside another (digit extraction) — a good example of composing small, already-understood pieces into something new, rather than writing new logic from scratch.

**Output:**
```
Enter a number: 145
145 is a Strong number
```

---

## Question 30
**Question:** W.A.C.P to print all Armstrong numbers between 1 to n.

**Code:**
```c
#include <stdio.h>
#include <math.h>
int main() {
    int n, num, temp, digit, numDigits, original;
    long long sum;
    printf("Enter n: ");
    scanf("%d", &n);

    for (num = 1; num <= n; num++) {
        original = num;
        numDigits = 0;
        temp = num;
        while (temp != 0) {
            temp = temp / 10;
            numDigits++;
        }

        temp = num;
        sum = 0;
        while (temp != 0) {
            digit = temp % 10;
            sum = sum + (long long)pow(digit, numDigits);
            temp = temp / 10;
        }

        if (sum == original) {
            printf("%d ", original);
        }
    }
    return 0;
}
```

**Line-by-line breakdown:**
- `for (num = 1; num <= n; num++)` — outer loop trying every candidate.
- The two `while` loops per candidate are exactly the "count digits, then sum digit^count" logic from Question 19 — just run fresh for every `num`.
- `if (sum == original)` — prints the candidate only if it passes the Armstrong test.

**Concept & Pattern:**
Same nested-loop pattern as Question 28, now wrapping the *general* Armstrong check (Q19) instead of the palindrome check.

> ⚠️ Same `pow()` floating-point caution from Question 19 applies here — see the bonus integer-power snippet at the end if you need this to be bulletproof for larger ranges.

**Output:**
```
Enter n: 500
1 2 3 4 5 6 7 8 9 153 370 371 407 
```

---

## Question 31
**Question:** W.A.C.P to print all Strong numbers between 1 to n.

**Code:**
```c
#include <stdio.h>
int main() {
    int n, num, temp, digit, fact, i, sum;
    printf("Enter n: ");
    scanf("%d", &n);

    for (num = 1; num <= n; num++) {
        temp = num;
        sum = 0;

        while (temp != 0) {
            digit = temp % 10;
            fact = 1;
            for (i = 1; i <= digit; i++) {
                fact = fact * i;
            }
            sum = sum + fact;
            temp = temp / 10;
        }

        if (sum == num) {
            printf("%d ", num);
        }
    }
    return 0;
}
```

**Line-by-line breakdown:**
- Outer `for` loop over candidates, exactly like Q28/Q30.
- The `while` + inner `for` combo is the single-number Strong-number check from Question 29, run once per candidate.

**Concept & Pattern:**
Same nested-loop wrapper as before, this time around Question 29's check. Once you can spot "outer loop over candidates + inner single-number check" as its own pattern, questions like this stop feeling new.

**Output:**
```
Enter n: 200
1 2 145 
```

---

## Question 32
**Question:** W.A.C.P to print all Perfect numbers between 1 to n.

**Code:**
```c
#include <stdio.h>
int main() {
    int n, num, i, sum;
    printf("Enter n: ");
    scanf("%d", &n);

    for (num = 1; num <= n; num++) {
        sum = 0;
        for (i = 1; i < num; i++) {
            if (num % i == 0) {
                sum = sum + i;
            }
        }
        if (sum == num) {
            printf("%d ", num);
        }
    }
    return 0;
}
```

**Line-by-line breakdown:**
- Outer `for (num = 1; ...)` — candidates from 1 to `n`.
- Inner `for (i = 1; i < num; i++)` — Question 11's proper-factor-summing logic, run fresh for each candidate.
- `if (sum == num)` — prints the candidate if it's perfect.

**Concept & Pattern:**
This one is genuinely slow for large `n` (it's checking every possible factor of every possible number — roughly n² work), which is worth noticing as your first real encounter with a program that "obviously works but doesn't scale." That trade-off (simple code vs. fast code) is a theme you'll meet constantly as problems get bigger.

**Output:**
```
Enter n: 10000
6 28 496 8128 
```

---

## Question 33
**Question:** W.A.C.P to print all Prime numbers between 1 to n.

**Code:**
```c
#include <stdio.h>
int main() {
    int n, num, i, isPrime;
    printf("Enter n: ");
    scanf("%d", &n);

    for (num = 2; num <= n; num++) {
        isPrime = 1;
        for (i = 2; i <= num / 2; i++) {
            if (num % i == 0) {
                isPrime = 0;
                break;
            }
        }
        if (isPrime) {
            printf("%d ", num);
        }
    }
    return 0;
}
```

**Line-by-line breakdown:**
- `for (num = 2; ...)` — starts at 2, since 0 and 1 are never prime.
- Inner loop and flag/`break` logic — identical to Question 10, just run once per candidate.
- `if (isPrime)` — prints the candidate if the flag survived the inner loop untouched.

**Concept & Pattern:**
The nested-loop wrapper pattern one more time, this time around Question 10's prime check. Notice the `break` inside the inner loop still only exits the *inner* loop — the outer loop moves on to the next candidate normally.

**Output:**
```
Enter n: 50
2 3 5 7 11 13 17 19 23 29 31 37 41 43 47 
```

---

## Question 34
**Question:** W.A.C.P to find all prime factors of a number.

**Code:**
```c
#include <stdio.h>
int main() {
    int n, i;
    printf("Enter a number: ");
    scanf("%d", &n);

    printf("Prime factors: ");
    for (i = 2; i <= n; i++) {
        while (n % i == 0) {
            printf("%d ", i);
            n = n / i;
        }
    }
    return 0;
}
```

**Line-by-line breakdown:**
- `for (i = 2; i <= n; i++)` — tries each possible factor starting from 2. Note `n` itself **shrinks** during the program, so this loop effectively covers fewer and fewer candidates as it goes.
- `while (n % i == 0) { printf...; n = n / i; }` — as long as `i` divides `n` evenly, keep dividing it out and printing `i` again. This automatically handles **repeated** factors (like the two 2's in 60 = 2×2×3×5).
- Once `i` no longer divides `n`, the `while` loop stops and the outer `for` moves to the next `i`.

**Concept & Pattern:**
Because we always try the *smallest* possible factor first and fully remove it before moving on, every number this loop prints is guaranteed to already be prime — there's no need for a separate prime-checking step. This is a subtle but important idea: sometimes the *order* in which you do things (smallest factors first) is what makes a check unnecessary.

**Output:**
```
Enter a number: 60
Prime factors: 2 2 3 5 
```

---

## Bonus: overflow-safe integer power (avoiding the `pow()` pitfall)

Questions 19 and 30 use `pow()` from `<math.h>`, which works with `double`s and can occasionally round incorrectly for integer powers (see the warning under Question 19). If you want a version that's guaranteed exact for integers, use this instead:

```c
long long ipow(int base, int exp) {
    long long result = 1;
    for (int i = 0; i < exp; i++) {
        result = result * base;
    }
    return result;
}
```

Then replace `(long long)pow(digit, numDigits)` with `ipow(digit, numDigits)` in Questions 19 and 30. No `<math.h>` needed, and no floating-point rounding risk — it's the same repeated-multiplication accumulator you already learned in Question 13.

---
---

<div align="center"> <h1 style="font-weight: bold;">@PSCodersHub</h1> </div>