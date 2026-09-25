# PLACEMENT – Session 12: Logical Reasoning
## Date: 24th September 2026

### Q1. Write a C program to check whether a number is strong number or not.

**What is a Strong Number?**
A number is called a **Strong Number** if the sum of the factorial of its digits equals the number itself.

**Ex:**
```
Input  : 145
Output : 145 is a Strong Number
         (1! + 4! + 5! = 1 + 24 + 120 = 145)

Input  : 123
Output : 123 is not a Strong Number
         (1! + 2! + 3! = 1 + 2 + 6 = 9)
```

**Code:**

```c
#include <stdio.h>

int main() {
    int n, temp, digit, fact, i, sum = 0;

    printf("Input : ");
    scanf("%d", &n);

    temp = n;   // Keep a copy of n, since we destroy temp digit by digit

    while (temp > 0) {
        digit = temp % 10;      // Extract the last digit

        fact = 1;               // Compute factorial of that digit
        for (i = 1; i <= digit; i++) {
            fact = fact * i;
        }

        sum = sum + fact;       // Add it to the running total
        temp = temp / 10;       // Drop the last digit
    }

    if (sum == n)
        printf("Output : %d is a Strong Number\n", n);
    else
        printf("Output : %d is not a Strong Number\n", n);

    return 0;
}
```

**Line-by-Line Explanation:**

| Line | What it does |
|---|---|
| `int n, temp, digit, fact, i, sum = 0;` | `sum` accumulates the factorial-sum of digits; `temp` is a working copy of `n`. |
| `scanf("%d", &n);` | Reads the number to check. |
| `temp = n;` | Copies `n` into `temp` so the original value stays available for the final comparison. |
| `while (temp > 0)` | Loops until every digit of `temp` has been extracted. |
| `digit = temp % 10;` | Isolates the last digit of `temp`. |
| `fact = 1; for (i = 1; i <= digit; i++)` | Computes `digit!` from scratch each iteration (0! = 1 is handled naturally since the loop body never runs for digit = 0). |
| `sum = sum + fact;` | Adds this digit's factorial to the running sum. |
| `temp = temp / 10;` | Integer-divides by 10, chopping off the digit just processed. |
| `if (sum == n)` | The strong-number test: the digit-factorial sum must exactly equal the original number. |

**Trace (n = 145):**

| Step | temp | digit | fact (digit!) | sum |
|---|---|---|---|---|
| 1 | 145 | 5 | 120 | 120 |
| 2 | 14 | 4 | 24 | 144 |
| 3 | 1 | 1 | 1 | 145 |
| 4 | 0 | — loop ends — | | |

`sum (145) == n (145)` → strong number.

**Output:** `145 is a Strong Number`

---

### Q2. Write a C program to print the Nth position of prime number.

**Ex:**
```
Input  : n = 1      Output : 2      (1st prime)
Input  : n = 5      Output : 11     (2, 3, 5, 7, 11)
Input  : n = 10     Output : 29     (2, 3, 5, 7, 11, 13, 17, 19, 23, 29)
```

**Code:**

```c
#include <stdio.h>

int main() {
    int n, count = 0, num = 2, i, isPrime;

    printf("Input : n = ");
    scanf("%d", &n);

    while (count < n) {
        isPrime = 1;    // Assume num is prime until proven otherwise

        // Trial division: only need to check up to sqrt(num)
        for (i = 2; i * i <= num; i++) {
            if (num % i == 0) {
                isPrime = 0;    // Found a divisor -> not prime
                break;
            }
        }

        if (isPrime) {
            count++;            // One more prime found
            if (count == n) {   // Reached the Nth one
                printf("Output : %d\n", num);
                return 0;
            }
        }

        num++;  // Move on to the next candidate
    }
    return 0;
}
```

**Line-by-Line Explanation:**

| Line | What it does |
|---|---|
| `int count = 0, num = 2;` | `count` tracks how many primes have been found so far; `num` is the current candidate, starting from 2 (the first prime). |
| `while (count < n)` | Keeps searching until the Nth prime is located. |
| `isPrime = 1;` | Optimistic assumption: treat `num` as prime unless a divisor is found. |
| `for (i = 2; i * i <= num; i++)` | Trial division up to √num — if `num` had any divisor larger than its root, the paired factor would already have been found below it. |
| `if (num % i == 0) { isPrime = 0; break; }` | The moment a divisor is found, the number is composite — no need to keep checking. |
| `count++;` | A confirmed prime increments the found-prime counter. |
| `if (count == n) { printf(...); return 0; }` | The instant the Nth prime is confirmed, print it and exit — no further numbers are tested. |
| `num++;` | Advances to the next candidate integer. |

**Trace (n = 5):**

| num | Divisor found? | Prime? | count |
|---|---|---|---|
| 2 | no | yes | 1 |
| 3 | no | yes | 2 |
| 4 | 2 | no | 1 |
| 5 | no | yes | 3 |
| 6 | 2 | no | 3 |
| 7 | no | yes | 4 |
| 8 | 2 | no | 4 |
| 9 | 3 | no | 4 |
| 10 | 2 | no | 4 |
| 11 | no | yes | **5 = n → print 11** |

**Output:** `11`

---
---

<div align="center"> <h1 style="font-weight: bold;">@PSCodersHub</h1> </div>