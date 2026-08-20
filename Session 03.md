# PLACEMENT – Session 3: Logical Reasoning
## Date: 20th August 2026

### Q1

**Code:**

```c
#include <stdio.h>
void main()
{
    int a = -5;
    int k = (a++, ++a);
    printf("%d\n", k);
}

```

**Explanation:**

* The comma operator `(a++, ++a)` evaluates from left to right and acts as a sequence point.
* First, `a++` (post-increment) evaluates to `-5`, then `a` becomes `-4`.
* Next, `++a` (pre-increment) makes `a` become `-3` and evaluates to `-3`.
* The comma operator returns the value of the rightmost expression, which is `-3`.
* Therefore, `k = -3`.

**Output:**
`-3`

---

### Q2

**Code:**

```c
#include <stdio.h>
void main()
{
    int k = 8;
    int x = 0 == 1 && k++;
    printf("%d%d\n", x, k);
}

```

**Explanation:**

* In the expression `x = 0 == 1 && k++;`, the equality operator `==` has higher precedence than `&&`.
* `0 == 1` evaluates to `0` (False).
* Because of the short-circuit evaluation property of the Logical AND (`&&`) operator, if the left side is false, the right side (`k++`) is completely skipped.
* So, `x = 0` and `k` remains `8`.

**Output:**
`08`

---

### Q3

**Code:**

```c
#include <stdio.h>
void main()
{
    unsigned int x = -5;
    printf("%d", x);
}

```

**Explanation:**

* `unsigned int x = -5;` assigns a negative value to an unsigned integer. In memory, `-5` is stored in its 2's complement form.
* `printf("%d", x);` uses the `%d` format specifier, which explicitly tells the compiler to read the data as a *signed* integer.
* It reads that same 2's complement binary pattern back as a signed integer, resulting in `-5`.

**Output:**
`-5`

> > ---------------- **Expanded Explanation for Q3** ----------------

### 🔎 Step 1: Assigning `-5` to an `unsigned int`
- `unsigned int` cannot represent negative numbers.  
- When you write `unsigned int x = -5;`, the compiler **converts** `-5` into its unsigned equivalent.  
- Conversion rule:  
  $\text{unsigned value} = \text{signed value} + 2^{N}$  
  
  where **N** is the number of bits in `unsigned int` (commonly 16 or 32).  

For a **16-bit unsigned int**:

$-5 + 2^{16} = -5 + 65536 = 65531$

So internally, `x` actually holds **65531**.

### 🔎 Step 2: Printing with `%d`
- `%d` tells `printf` to interpret the bits as a **signed int**.  
- But `x` is unsigned, so the value 65531 is reinterpreted as a signed integer.  
- On a 16-bit system, 65531 corresponds to the two’s complement representation of `-5`.  
- Therefore, `%d` prints **`-5`**.

### 🔎 Step 3: Printing with `%u`
- `%u` tells `printf` to interpret the bits as **unsigned int**.  
- So it prints the raw unsigned value stored in `x`, which is **65531**.

### ✅ Final Explanation
- `unsigned int x = -5;` → stored as **65531** internally.  
- `printf("%d", x);` → interprets those bits as signed → prints **-5**.  
- `printf("%u", x);` → interprets those bits as unsigned → prints **65531**.

---

### Q4

**Code:**

```c
#include <stdio.h>
int main()
{
    int x = 2, y = 1;
    x *= x + y;
    printf("%d\n", x);
    return 0;
}

```

**Explanation:**

* The compound assignment operator `x *= x + y;` expands to `x = x * (x + y);` because assignment operators have the lowest precedence.
* Substituting the values: `x = 2 * (2 + 1)`.
* `x = 2 * 3` which equals `6`.

**Output:**
`6`

---

### Q5

**Code:**

```c
#include <stdio.h>
int main()
{
    int x = 1, y = 0;
    x &&= y;
    printf("%d\n", x);
}

```

**Explanation:**

* The statement `x &&= y;` uses an operator (`&&=`) that does not exist in the C language. C has bitwise assignment operators like `&=`, but no logical assignment operators like `&&=`.
* The compiler will throw a syntax error.

**Output:**
`Compilation Error`

---

### Q6

**Code:**

```c
#include <stdio.h>
void main()
{
    int b = 5 + 7 * 4 - 9 * (3, 2);
    printf("%d", b);
}

```

**Explanation:**

* In the expression `9 * (3, 2)`, the comma operator `(3, 2)` evaluates to its rightmost operand, which is `2`.
* The expression simplifies to: `b = 5 + 7 * 4 - 9 * 2`.
* Applying operator precedence (multiplication first): `b = 5 + 28 - 18`.
* Addition and Subtraction next: `33 - 18 = 15`.

**Output:**
`15`

---

### Q7

**Code:**

```c
#include <stdio.h>
int main()
{
    int x = 2, y = 0;
    int z = (y++) ? y == 1 && x : 0;
    printf("%d\n", z);
    return 0;
}

```

**Explanation:**

* The ternary operator `z = (y++) ? y == 1 && x : 0;` checks the condition `(y++)` first.
* Because it's a post-increment, `(y++)` evaluates to the current value of `y`, which is `0` (False). Then `y` becomes `1`.
* Since the condition is false, the ternary operator skips the middle expression entirely and directly evaluates to the third operand, which is `0`.

**Output:**
`0`

---

### Q8

**Code:**

```c
#include <stdio.h>
void main()
{
    int k = 8;
    int m = 7;
    int z = k < m ? k++ : m++;
    printf("%d", z);
}

```

**Explanation:**

* Condition: `k < m` -> `8 < 7`, which is `0` (False).
* The ternary operator jumps to the false block: `m++`.
* Because `m++` is a post-increment, it returns the current value of `m` (`7`) to `z`, and then `m` updates to `8`.

**Output:**
`7`

---

### Q9

**Code:**

```c
#include <stdio.h>
int main()
{
    int y = 1, x = 0;
    int l = (y++, x++) ? y : x;
    printf("%d\n", l);
}

```

**Explanation:**

* Condition: `(y++, x++)`. The comma operator evaluates left to right.
* `y++` executes (`y` becomes 2). Then `x++` executes, and its result (`0` because it is post-increment) is returned as the final value of the condition. Then `x` becomes 1.
* Condition evaluates to `0` (False).
* The ternary operator jumps to the false block: `x`.
* The current updated value of `x` is `1`.

**Output:**
`1`

---

### Q10

**Code:**

```c
#include <stdio.h>
void main()
{
    if (~0 == 1)
        printf("yes\n");
    else
        printf("no\n");
}

```

**Explanation:**

* `~0` applies a Bitwise NOT to integer `0`. In binary, `0` is all `0`s. Flipping all bits gives all `1`s, which represents `-1` in 2's complement representation.
* Condition: `(-1 == 1)` evaluates to `0` (False).
* The program jumps to the `else` block.

**Output:**
`no`

---

### Q11

**Code:**

```c
#include <stdio.h>
void main()
{
    int y = 0;
    if (1 | (y = 1))
        printf("y is %d\n", y);
    else
        printf("%d\n", y);
}

```

**Explanation:**

* The condition is `if (1 | (y = 1))`. Unlike the logical OR (`||`) which short-circuits, the bitwise OR (`|`) evaluates both operands.
* The left operand is `1`. The right operand `(y = 1)` assigns `1` to `y` and evaluates to `1`.
* `1 | 1` evaluates to `1` (True).
* The `if` block executes. Since `y` was updated to `1` during the condition check, it prints `1`.

**Output:**
`y is 1`

---

### Q12

**Code:**

```c
#include <stdio.h>
void main()
{
    int y = 1;
    if (y & (y = 2))
        printf("true %d\n", y);
    else
        printf("false %d\n", y);
}

```

**Explanation:**

* The condition is `if (y & (y = 2))`. This statement causes **Undefined Behavior** in C because the variable `y` is read and modified within the same expression without a sequence point.
* However, compiling with typical left-to-right evaluation: the first `y` is read as `1`. The second part `(y = 2)` assigns `2` to `y` and evaluates to `2`.
* `1 & 2` evaluates to `0` (False).
* The `else` block executes, printing the modified value of `y` which is `2`.

**Output:**
`false 2` *(Note: Technically Undefined Behavior)*

---

### Q13. WAP a Program to check the number is even or odd .

**Program Code:**

```c
#include <stdio.h>

int main() {
    int num;
    printf("Enter an integer: ");
    scanf("%d", &num);

    if(num % 2 == 0) {
        printf("%d is even.\n", num);
    } else {
        printf("%d is odd.\n", num);
    }

    return 0;
}

```

---

### Q14 – WAP to Print Numbers up to `n`.

<p align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/blob/main/Assets/12.jpg?raw=true" width="32%" />
  <img src="https://github.com/PSCodersHub/PLACEMENT/blob/main/Assets/13.jpg?raw=true" width="32%" />
  <img src="https://github.com/PSCodersHub/PLACEMENT/blob/main/Assets/14.jpg?raw=true" width="32%" />
</p>

---

#### Part 1: Using `for` loop

```c
#include <stdio.h>

int main() {
    int n, i;

    printf("Enter the value of n: ");
    scanf("%d", &n);

    for(i = 1; i <= n; i++) {
        printf("%d ", i);
    }
    printf("\n");

    return 0;
}
```

---

#### Part 2: Using `while` loop

```c
#include <stdio.h>

int main() {
    int n, i;

    printf("Enter the value of n: ");
    scanf("%d", &n);

    i = 1;
    while(i <= n) {
        printf("%d ", i);
        i++;
    }
    printf("\n");

    return 0;
}
```

---

#### Part 3: Using `do-while` loop

```c
#include <stdio.h>

int main() {
    int n, i;

    printf("Enter the value of n: ");
    scanf("%d", &n);

    i = 1;
    if (n >= 1) { // Guard in case user enters 0 or negative
        do {
            printf("%d ", i);
            i++;
        } while(i <= n);
    }
    printf("\n");

    return 0;
}
```

---

### Q15. WAP to check the number is prime or not .

**Program Code:**

```c
#include <stdio.h>

int main() {
    int n, i, isPrime = 1;

    printf("Enter a positive integer: ");
    scanf("%d", &n);

    // 0 and 1 are not prime numbers
    if (n == 0 || n == 1) {
        isPrime = 0;
    }

    // Loop to check for factors
    for (i = 2; i <= n / 2; ++i) {
        if (n % i == 0) {
            isPrime = 0;
            break;
        }
    }

    if (isPrime) {
        printf("%d is a prime number.\n", n);
    } else {
        printf("%d is not a prime number.\n", n);
    }

    return 0;
}

```

---
---

<div align="center"> <h1 style=font-weight: bold;>@PSCodersHub</h1> </div>