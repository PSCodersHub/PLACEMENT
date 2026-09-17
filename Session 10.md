# PLACEMENT – Session 10: Logical Reasoning
## Date: 17th September 2026

> **Note:** This session mainly covers the fundamentals of **Functions** and **Recursion** in C. It's largely conceptual/foundational and is **not very significant from a direct placement-exam point of view**, but it builds the base needed for recursion-heavy DSA problems later.

---

## Function Declaration

Function declaration is also known as **function prototype**, and it informs the compiler about the following 3 things:

a. Name of the function.  
b. Number and type of arguments received by the function.  
c. Type of value returned by the function.

**Syntax:**

```
return_type function_name ( parameter list );
```

**Example:**

```
int sum ( int , int );
```

Here, the prototype identifies to the compiler that `sum` is a function which takes two arguments of integer type and returns an integer value.

**N.B.**

- In the argument list we can **omit the variable names**, but data type must be specified.
- Prototype can be declared in local or global section.

---

## Function Definition

It consists of the whole description and code of a function. It tells what the function is doing and what are its input and output. It consists of 2 parts:

i. Function Header.  
ii. Function Body.

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/80.jpg" alt="Function Definition Syntax" width="500">
</div>

---

## Function Call

A function is called by its name followed by the argument lists.

**Syntax:**

```
Function_name (arg1,arg2.........);
```

**Ex:**

```
sum (num1,num2);
```

- Even if there is no arguments, the function call should have the empty parentheses.  
**Ex.** `Sum();`
- The function name, type and number of variables listed in the function call statement must match with that of the function declaration statement and the header of the function definition.

---

### Ex-1 : Factorial of a Number using a User-Defined Function (Call by Value)

**Code:**

```c
#include<stdio.h>

long int fact(int);          // Prototype

int main()
{
    long int f;
    f = fact(5);              // function call

    printf("%ld", f);
}

long int fact(int n)          // Function header
{
    long int fa = 1;
    while (n > 0)
    {
        fa = fa * n;
        n--;
    }
    return (fa);
}
```

**Line-by-Line Explanation:**

| Line                             | What it does                                                                                     |
| -------------------------------- | -------------------------------------------------------------------------------------------------- |
| `long int fact(int);`            | Function prototype — tells the compiler `fact` takes an `int` and returns a `long int`.            |
| `f = fact(5);`                   | Function call — passes `5` as the argument and stores the returned result in `f`.                  |
| `long int fact(int n)`           | Function header/definition — receives the argument as `n`.                                         |
| `long int fa = 1;`               | Accumulator initialized to 1 (multiplicative identity).                                            |
| `while(n > 0) { fa = fa*n; n--;}`| Multiplies `fa` by `n` and decrements `n` until it reaches 0, building up the factorial.            |
| `return(fa);`                    | Returns the computed factorial back to `main`.                                                     |

**Output (for n = 5):** `120`

---

### Ex-2 : Swap Two Numbers using a Function (Call by Value)

**Code:**

```c
#include<stdio.h>

void swap(int a, int b)
{
    int temp;
    temp = a;
    a = b;
    b = temp;
    printf("After swapping value of A and B: %d %d", a, b);
}

int main()
{
    int x, y;
    printf("Enter value for A and B: ");
    scanf("%d %d", &x, &y);
    swap(x, y);
}
```

**Line-by-Line Explanation:**

| Line                          | What it does                                                                                      |
| ----------------------------- | --------------------------------------------------------------------------------------------------- |
| `void swap(int a, int b)`     | Receives copies of `x` and `y` as `a` and `b` (call by value).                                     |
| `temp = a; a = b; b = temp;`  | Standard 3-variable swap using a temporary variable.                                                |
| `printf(...)` inside `swap`   | Prints the swapped values from *inside* the function, since the swap only affects the local copies. |
| `swap(x, y);`                 | Calls `swap` with the values entered by the user.                                                   |

**Note:** Because this is **call by value**, only the local copies `a` and `b` inside `swap` are swapped — `x` and `y` in `main` remain unchanged. That's why the confirmation is printed from inside `swap` itself, not from `main`.

**Trace (Input: A = 45, B = 96):**

```
Enter value for A and B: 45 96
After swapping value of A and B: 96 45
```

**Output:** `96 45`

---

## Different Aspects of Function Calling

A function may or may not accept any argument. It may or may not return any value. Based on these facts, there are four different aspects of function calls:

1. Functions with no arguments and no return value. **(No Input, No Return)**
2. Functions with no arguments and a return value. **(No Input, with Return)**
3. Functions with arguments and no return value. **(Input, but No Return)**
4. Functions with arguments and a return value. **(Input, with Return)**

---

## What is Recursion?

- The process in which a function calls itself is called **recursion**, and the corresponding function is called a **recursive function**.
- In recursion, the calling function and the called function are same.
- In recursion, the solution to the base case is provided, and the solution of the bigger problem is expressed *in terms of smaller problems*.

---

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/81.jpg" alt="Working of Recursion" width="500">
</div>

`main()` calls `recurse()`, and `recurse()` calls itself again from within its own body — each call stacks on top of the previous one until a base/stopping condition is reached.

---

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/82.jpg" alt="Factorial of a Number using Recursion Example" width="500">
</div>

**Manual Trace (For user input: 5):**

| Call        | Calculation      |
| ----------- | ---------------- |
| `5 * f(4)`  | `5 * 24 = 120`   |
| `4 * f(3)`  | `4 * 6 = 24`     |
| `3 * f(2)`  | `3 * 2 = 6`      |
| `2 * f(1)`  | `2 * 1 = 2`      |

**Final Result:** `120`

---

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/83.jpg" alt="Power of a Number using Recursion Example" width="500">
</div>

**Line-by-Line Explanation:**

| Line                          | What it does                                                              |
| ----------------------------- | -------------------------------------------------------------------------- |
| `if (n == 0) return(1);`      | Base case — anything raised to the power 0 is 1.                          |
| `return(a * power(a, n-1));`  | Recursive case — multiplies `a` by the result of the smaller subproblem `a^(n-1)`. |

---

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/84.jpg" alt="Print Fibonacci Series using Recursion Example" width="500">
</div>

**Line-by-Line Explanation:**

| Line                                     | What it does                                                                 |
| ----------------------------------------- | ----------------------------------------------------------------------------- |
| `if (n == 0 \|\| n == 1) return(1);`      | Base case — both the 0th and 1st terms return 1 in this convention.          |
| `return(fibo(n-2) + fibo(n-1));`          | Recursive case — each term is the sum of the two smaller subproblems.        |

> **Note:** This slide's base case returns `1` for both `n = 0` and `n = 1`. This is a different indexing convention from Session 9's iterative Fibonacci (where the 1st term = `0`, 2nd term = `1`) — worth keeping in mind if comparing the two approaches.

> ---
> ---

<h1 align="center">Practice Questions</h1>
<p align="center"><em>C Programming — Recursion</em></p>

### Q1. W.A.C.P to print n to 1 using recursion.

**Code:**

```c
#include<stdio.h>

void printNto1(int n)
{
    if (n == 0)
        return;

    printf("%d ", n);
    printNto1(n - 1);
}

int main()
{
    int n;
    printf("Input : n = ");
    scanf("%d", &n);

    printf("Output : ");
    printNto1(n);

    return 0;
}
```

**Line-by-Line Explanation:**

| Line                              | What it does                                                                 |
| ---------------------------------- | ----------------------------------------------------------------------------- |
| `if (n == 0) return;`              | Base case — stops the recursion once `n` reaches 0.                          |
| `printf("%d ", n);`                | Prints the current value of `n` **before** recursing further.                |
| `printNto1(n - 1);`                | Recursive call with the next smaller value, continuing the countdown.        |

**Trace (n = 5):** `printNto1(5)` prints `5`, then calls `printNto1(4)` which prints `4`, and so on down to `printNto1(1)` which prints `1`, then `printNto1(0)` hits the base case and returns.

**Output:** `5 4 3 2 1`

---

### Q2. W.A.C.P to print all natural numbers between 1 to n using recursion.

**Code:**

```c
#include<stdio.h>

void print1toN(int n)
{
    if (n == 0)
        return;

    print1toN(n - 1);
    printf("%d ", n);
}

int main()
{
    int n;
    printf("Input : n = ");
    scanf("%d", &n);

    printf("Output : ");
    print1toN(n);

    return 0;
}
```

**Line-by-Line Explanation:**

| Line                              | What it does                                                                                          |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------- |
| `if (n == 0) return;`              | Base case — stops recursing once `n` reaches 0.                                                          |
| `print1toN(n - 1);`                | Recursive call happens **before** the print, so the call stack unwinds from smallest to largest.         |
| `printf("%d ", n);`                | Prints `n` **after** the recursive call returns — this is what flips the order to ascending.             |

**Trace (n = 5):** Calls stack up as `print1toN(5)→(4)→(3)→(2)→(1)→(0)`. The base case at `0` returns first, so printing happens in reverse call order: `1, 2, 3, 4, 5`.

**Output:** `1 2 3 4 5`

---

### Q3. W.A.C.P to find sum of all natural numbers between 1 to n using recursion.

**Code:**

```c
#include<stdio.h>

int sumOfN(int n)
{
    if (n == 0)
        return 0;

    return n + sumOfN(n - 1);
}

int main()
{
    int n;
    printf("Input : n = ");
    scanf("%d", &n);

    printf("Output : %d\n", sumOfN(n));

    return 0;
}
```

**Line-by-Line Explanation:**

| Line                              | What it does                                                                       |
| ---------------------------------- | ------------------------------------------------------------------------------------- |
| `if (n == 0) return 0;`            | Base case — sum of 0 numbers is 0.                                                    |
| `return n + sumOfN(n - 1);`        | Adds `n` to the sum of all natural numbers smaller than it (the smaller subproblem).  |

**Trace (n = 5):** `sumOfN(5) = 5 + sumOfN(4) = 5 + (4 + sumOfN(3)) = 5+4+3+2+1+0 = 15`

**Output:** `15`

---

### Q4. W.A.C.P to find sum of digits of a given number using recursion.

**Code:**

```c
#include<stdio.h>

int sumOfDigits(int n)
{
    if (n == 0)
        return 0;

    return (n % 10) + sumOfDigits(n / 10);
}

int main()
{
    int n;
    printf("Input : n = ");
    scanf("%d", &n);

    printf("Output : %d\n", sumOfDigits(n));

    return 0;
}
```

**Line-by-Line Explanation:**

| Line                                  | What it does                                                                       |
| --------------------------------------- | ------------------------------------------------------------------------------------- |
| `if (n == 0) return 0;`                 | Base case — no digits left to add.                                                   |
| `(n % 10)`                              | Extracts the last digit of `n`.                                                      |
| `sumOfDigits(n / 10)`                   | Recurses on `n` with its last digit removed, reducing the problem size.              |
| `return (n % 10) + sumOfDigits(n / 10);`| Adds the extracted digit to the sum of the remaining digits.                         |

**Trace (n = 1234):** `sumOfDigits(1234) = 4 + sumOfDigits(123) = 4+3+2+1 = 10`

**Output:** `10`

---

### Q5. W.A.C.P to find reverse of any number using recursion.

**Code:**

```c
#include<stdio.h>

int reverseNumber(int n, int rev)
{
    if (n == 0)
        return rev;

    return reverseNumber(n / 10, rev * 10 + (n % 10));
}

int main()
{
    int n;
    printf("Input : n = ");
    scanf("%d", &n);

    printf("Output : %d\n", reverseNumber(n, 0));

    return 0;
}
```

**Line-by-Line Explanation:**

| Line                                             | What it does                                                                                     |
| --------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| `int reverseNumber(int n, int rev)`                 | Takes the number to reverse `n`, and an accumulator `rev` that carries the reversed digits so far.  |
| `if (n == 0) return rev;`                           | Base case — once all digits are consumed, `rev` holds the fully reversed number.                    |
| `rev * 10 + (n % 10)`                               | Shifts the accumulated digits one place left and appends the last digit of `n`.                     |
| `reverseNumber(n / 10, ...)`                        | Recurses with `n` shortened by one digit, carrying the updated `rev` forward.                       |

**Trace (n = 1234):**

| Call                     | n   | rev  |
| ------------------------ | --- | ---- |
| `reverseNumber(1234, 0)` | 123 | 4    |
| `reverseNumber(123, 4)`  | 12  | 43   |
| `reverseNumber(12, 43)`  | 1   | 432  |
| `reverseNumber(1, 432)`  | 0   | 4321 |

**Output:** `4321`

---

### Q6. W.A.C.P to find GCD (HCF) of two numbers using recursion.

**Code:**

```c
#include<stdio.h>

int gcd(int a, int b)
{
    if (b == 0)
        return a;

    return gcd(b, a % b);
}

int main()
{
    int a, b;
    printf("Input : a, b = ");
    scanf("%d %d", &a, &b);

    printf("Output : %d\n", gcd(a, b));

    return 0;
}
```

**Line-by-Line Explanation:**

| Line                          | What it does                                                                                       |
| ----------------------------- | ------------------------------------------------------------------------------------------------------ |
| `if (b == 0) return a;`       | Base case of the Euclidean algorithm — when `b` becomes 0, `a` is the GCD.                            |
| `return gcd(b, a % b);`       | Recursive case — replaces `(a, b)` with `(b, a % b)`, shrinking the problem each time.                 |

**Trace (a = 36, b = 24):**

| Call             | Result                    |
| ---------------- | -------------------------- |
| `gcd(36, 24)`     | `gcd(24, 36 % 24)` → `gcd(24, 12)` |
| `gcd(24, 12)`     | `gcd(12, 24 % 12)` → `gcd(12, 0)`  |
| `gcd(12, 0)`      | `b == 0` → returns `12`            |

**Output:** `12`

---
---

<div align="center"> <h1 style="font-weight: bold;">@PSCodersHub</h1> </div>