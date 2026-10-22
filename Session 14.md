# PLACEMENT – Session 14: Logical Reasoning
## Date: 1st October 2026

### Q1. Write a C program to find the sum of all array elements.

**Concept:**
The sum of an array is calculated by adding every element to a running total. Initialize `sum` to `0` before starting the loop.

**Example:**
```
Input  : n = 5
         Elements = 10 20 30 40 50
Output : Sum = 150
```

**Code:**

```c
#include <stdio.h>

#define MAX 100

int main(void) {
    int arr[MAX], n, i;
    long long sum = 0;

    printf("Input : Enter number of elements (1-%d): ", MAX);
    scanf("%d", &n);

    if (n < 1 || n > MAX) {
        printf("Output : Invalid array size\n");
        return 1;
    }

    printf("Input : Enter %d elements: ", n);
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    for (i = 0; i < n; i++) {
        sum = sum + arr[i];
    }

    printf("Output : Sum = %lld\n", sum);
    return 0;
}
```

**Line-by-Line Explanation:**

| Statement | What it does |
|---|---|
| `int arr[MAX], n, i;` | Declares an array that can store up to 100 integers, the number of elements `n`, and the loop variable `i`. |
| `long long sum = 0;` | Initializes the running total to zero. `long long` allows a larger sum than a typical `int`. |
| `scanf("%d", &n);` | Reads how many elements the user wants to enter. |
| `if (n < 1 || n > MAX)` | Rejects an array size that is outside the supported range of 1 to 100. |
| `for (i = 0; i < n; i++)` | Reads each of the `n` elements into the array. |
| `sum = sum + arr[i];` | Adds the current array element to the running total. |
| `printf("Output : Sum = %lld\n", sum);` | Displays the final sum. `%lld` is the format specifier for `long long`. |

**Trace (Elements = 10, 20, 30, 40, 50):**

| Step | `i` | `arr[i]` | `sum` after addition |
|---|---:|---:|---:|
| Initial | — | — | 0 |
| 1 | 0 | 10 | 10 |
| 2 | 1 | 20 | 30 |
| 3 | 2 | 30 | 60 |
| 4 | 3 | 40 | 100 |
| 5 | 4 | 50 | 150 |

**Output:** `Sum = 150`

---

### Q2. Write a C program to count the total number of even and odd elements in an array.

**Concept:**
An integer is **even** if it is divisible by 2, so `arr[i] % 2 == 0`. Otherwise, it is **odd**. Keep separate counters for even and odd elements.

**Example:**
```
Input  : n = 5
         Elements = 10 7 2 9 0
Output : Even elements = 3
         Odd elements  = 2
```

**Code:**

```c
#include <stdio.h>

#define MAX 100

int main(void) {
    int arr[MAX], n, i;
    int even = 0, odd = 0;

    printf("Input : Enter number of elements (1-%d): ", MAX);
    scanf("%d", &n);

    if (n < 1 || n > MAX) {
        printf("Output : Invalid array size\n");
        return 1;
    }

    printf("Input : Enter %d elements: ", n);
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    for (i = 0; i < n; i++) {
        if (arr[i] % 2 == 0) {
            even++;
        } else {
            odd++;
        }
    }

    printf("Output : Even elements = %d\n", even);
    printf("         Odd elements  = %d\n", odd);
    return 0;
}
```

**Line-by-Line Explanation:**

| Statement | What it does |
|---|---|
| `int even = 0, odd = 0;` | Creates and initializes the two counters. |
| `for (i = 0; i < n; i++)` | Visits every element in the array. |
| `if (arr[i] % 2 == 0)` | Checks whether the current element is divisible by 2 without a remainder. |
| `even++;` | Increases the even counter when the condition is true. |
| `else { odd++; }` | Increases the odd counter when the element is not even. Negative odd integers are also counted correctly. |
| The two `printf` statements | Display the total number of even and odd elements. |

**Trace (Elements = 10, 7, 2, 9, 0):**

| Element | Check | Even count | Odd count |
|---:|---|---:|---:|
| 10 | Even | 1 | 0 |
| 7 | Odd | 1 | 1 |
| 2 | Even | 2 | 1 |
| 9 | Odd | 2 | 2 |
| 0 | Even | 3 | 2 |

**Output:**
```
Even elements = 3
Odd elements  = 2
```

---

### Q3. Write a C program to find the maximum and minimum elements in an array.

**Concept:**
Initialize both `max` and `min` with the first array element. Compare every remaining element with them and update the values when a larger maximum or a smaller minimum is found.

**Example:**
```
Input  : n = 5
         Elements = 12 5 33 9 -4
Output : Maximum = 33
         Minimum = -4
```

**Code:**

```c
#include <stdio.h>

#define MAX 100

int main(void) {
    int arr[MAX], n, i;
    int max, min;

    printf("Input : Enter number of elements (1-%d): ", MAX);
    scanf("%d", &n);

    if (n < 1 || n > MAX) {
        printf("Output : Invalid array size\n");
        return 1;
    }

    printf("Input : Enter %d elements: ", n);
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    max = arr[0];
    min = arr[0];

    for (i = 1; i < n; i++) {
        if (arr[i] > max) {
            max = arr[i];
        }
        if (arr[i] < min) {
            min = arr[i];
        }
    }

    printf("Output : Maximum = %d\n", max);
    printf("         Minimum = %d\n", min);
    return 0;
}
```

**Line-by-Line Explanation:**

| Statement | What it does |
|---|---|
| `max = arr[0];` | Uses the first element as the initial maximum candidate. |
| `min = arr[0];` | Uses the first element as the initial minimum candidate. |
| `for (i = 1; i < n; i++)` | Starts from index 1 because index 0 has already initialized `max` and `min`. |
| `if (arr[i] > max)` | Checks whether the current element is larger than the maximum found so far. |
| `max = arr[i];` | Updates the maximum when a larger element is found. |
| `if (arr[i] < min)` | Checks whether the current element is smaller than the minimum found so far. |
| `min = arr[i];` | Updates the minimum when a smaller element is found. |

**Trace (Elements = 12, 5, 33, 9, -4):**

| Current element | `max` after comparison | `min` after comparison |
|---:|---:|---:|
| Initial: 12 | 12 | 12 |
| 5 | 12 | 5 |
| 33 | 33 | 5 |
| 9 | 33 | 5 |
| -4 | 33 | -4 |

**Output:**
```
Maximum = 33
Minimum = -4
```

---

### Q4. Write a C program to find the leader elements in an array.

**What is a Leader Element?**
For this question, a **leader** is an element that is strictly greater than every element to its **right**. The last element is always a leader because there are no elements to its right.

> **Definition note:** The written prompt mentioned elements on the left, but the screenshots compare `arr[i]` with elements at later indices (`j = i + 1`) and state that the last element is a leader. Those details match the standard right-side definition used below. If the intended rule is “greater than every element to its left,” the first element—not the last—would be the default leader.

**Example:**
```
Input  : n = 6
         Elements = 16 17 4 3 5 2
Output : Leaders = 17 5 2
```

**Code:**

```c
#include <stdio.h>

#define MAX 100

int main(void) {
    int arr[MAX], n, i, j;
    int isLeader;

    printf("Input : Enter number of elements (1-%d): ", MAX);
    scanf("%d", &n);

    if (n < 1 || n > MAX) {
        printf("Output : Invalid array size\n");
        return 1;
    }

    printf("Input : Enter %d elements: ", n);
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    printf("Output : Leaders = ");
    for (i = 0; i < n; i++) {
        isLeader = 1;

        for (j = i + 1; j < n; j++) {
            if (arr[i] <= arr[j]) {
                isLeader = 0;
                break;
            }
        }

        if (isLeader == 1) {
            printf("%d ", arr[i]);
        }
    }

    printf("\n");
    return 0;
}
```

**Line-by-Line Explanation:**

| Statement | What it does |
|---|---|
| `for (i = 0; i < n; i++)` | Selects each array element as a possible leader. |
| `isLeader = 1;` | Initially assumes that the current element is a leader. |
| `for (j = i + 1; j < n; j++)` | Checks every element to the right of `arr[i]`. |
| `if (arr[i] <= arr[j])` | Finds an element to the right that is greater than or equal to `arr[i]`; therefore, `arr[i]` is not strictly greater than all elements to its right. |
| `isLeader = 0; break;` | Marks the current element as not a leader and stops checking it. |
| `if (isLeader == 1)` | Prints the current element if no element to its right disqualified it. |
| The inner loop for the last element | Does not execute for the last index, so the last element remains a leader by default. |

**Trace (Elements = 16, 17, 4, 3, 5, 2):**

| Element | Elements to its right | Leader? | Reason |
|---:|---|---|---|
| 16 | 17, 4, 3, 5, 2 | No | 17 is greater than 16. |
| 17 | 4, 3, 5, 2 | Yes | 17 is greater than all elements to its right. |
| 4 | 3, 5, 2 | No | 5 is greater than 4. |
| 3 | 5, 2 | No | 5 is greater than 3. |
| 5 | 2 | Yes | 5 is greater than 2. |
| 2 | None | Yes | The last element is a leader by default. |

**Output:** `Leaders = 17 5 2`

**Complexity:** This nested-loop solution takes up to **O(n²)** time and uses **O(1)** extra space, excluding the input array. The screenshots also show a right-to-left optimized idea using a running `ldr` (leader). That approach can find leaders in **O(n)** time, but printing them in the original left-to-right order requires storing them and printing them in reverse. In the shown attempt, `sum` is uninitialized and its update/return statements are commented out, so that version is incomplete if the goal is to calculate the sum of leaders.

---

### Q5. Predict the output of the following C program.

**Code:**

```c
#include <stdio.h>

int main(void) {
    int a[5] = {5, 1, 15, 20, 25};
    int i, j, m;

    i = ++a[1];
    j = a[1]++;
    m = a[i++];

    printf("%d, %d, %d", i, j, m);
    return 0;
}
```

**Concepts Used:**
- **Pre-increment (`++x`):** Increments the value first, then uses the updated value.
- **Post-increment (`x++`):** Uses the current value first, then increments it.
- **Array indexing:** Array indices start at `0`, so `a[1]` is the second element.

**Dry Run:**

Initial array: `a = {5, 1, 15, 20, 25}`

| Statement | Effect | Values after the statement |
|---|---|---|
| `i = ++a[1];` | Increments `a[1]` from 1 to 2, then assigns 2 to `i`. | `i = 2`, `a[1] = 2` |
| `j = a[1]++;` | Assigns the current value 2 to `j`, then increments `a[1]` to 3. | `j = 2`, `a[1] = 3` |
| `m = a[i++];` | Uses the current `i` (2) to read `a[2]` (15), then increments `i` to 3. | `m = 15`, `i = 3` |
| `printf("%d, %d, %d", i, j, m);` | Prints `i`, then `j`, then `m`. | `3, 2, 15` |

**Output:** `3, 2, 15`

---

### Q6. Predict the output of the following C program.

**Code:**

```c
#include <stdio.h>

int main(void) {
    int p;
    int a[8] = {1, 2, 3, 4, 5, 6, 9, 8};

    p = (a + 1)[3];
    printf("%d", p);

    return 0;
}
```

**Concept:**
In most expressions, an array name such as `a` points to its first element. The expression `(a + 1)` points to `a[1]`. Applying `[3]` to that pointer moves three more elements forward.

**Line-by-Line Explanation:**

| Statement | What it means |
|---|---|
| `int a[8] = {1, 2, 3, 4, 5, 6, 9, 8};` | Creates an integer array. Its indices run from `0` to `7`. |
| `(a + 1)` | Points to `a[1]`, whose value is `2`. |
| `(a + 1)[3]` | Is equivalent to `* ((a + 1) + 3)`, which is `*(a + 4)` and therefore `a[4]`. |
| `p = (a + 1)[3];` | Assigns `a[4]`, which is `5`, to `p`. |
| `printf("%d", p);` | Prints the value of `p`. |

**Trace:**

| Expression | Result |
|---|---:|
| `a + 1` | Address of `a[1]` |
| `(a + 1) + 3` | Address of `a[4]` |
| `a[4]` | 5 |
| `p` | 5 |

**Output:** `5`

**Note:** The slide uses `void main()`, but `int main(void)` is the standard form used in this version.

---
---

<div align="center"> <h1 style="font-weight: bold;">@PSCodersHub</h1> </div>