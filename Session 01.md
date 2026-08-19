# PLACEMENT – Session 1: Logical Reasoning
## Date: 13th August 2026

### Question 1

**Pseudocode:**

```c
if ( 5 + 3 * 6 )
    printf ( " ok " ) ;
else
    printf ( " Wrong " ) ;

```

**Full code:**

```c
#include <stdio.h>

int main() {
    if ( 5 + 3 * 6 )
        printf ( " ok " ) ;
    else
        printf ( " Wrong " ) ;
    
    return 0;
}

```

**Explanation of the code:**

* **Step 1:** The program evaluates the expression inside the `if` condition: `5 + 3 * 6`.
* **Step 2:** According to C operator precedence, multiplication (`*`) is evaluated before addition (`+`). Thus, `3 * 6` is calculated first, resulting in 18.
* **Step 3:** Next, the addition is performed: `5 + 18`, which equals 23.
* **Step 4:** The `if` condition now effectively reads `if (23)`. Since 23 is a non-zero integer, it is treated as a boolean `true` in C.
* **Step 5:** Because the condition is true, the `printf(" ok ");` statement executes.

**Final output:**
`ok`

---

> [!IMPORTANT]
>
> ## Operator Categories
>
> A useful way to remember the major categories of C operators is:
>
> **P U A S R E B L T A C**
>
> * **P = Postfix / Primary expressions** — `()`, `[]`, `.`, `->`, function calls, postfix `++` and `--`
> * **U = Unary operators** — prefix `++`, `--`, `+`, `-`, `!`, `~`, `*`, `&`, `sizeof`, type cast, etc.
> * **A = Arithmetic operators** — `*`, `/`, `%`, `+`, `-`
> * **S = Shift operators** — `<<`, `>>`
> * **R = Relational operators** — `<`, `>`, `<=`, `>=`
> * **E = Equality operators** — `==`, `!=`
> * **B = Bitwise operators** — `&`, `^`, `|`
> * **L = Logical operators** — `&&`, `||`
> * **T = Ternary / Conditional operator** — `?:`
> * **A = Assignment operators** — `=`, `+=`, `-=`, `*=`, `/=`, `%=` and others
> * **C = Comma operator** — `,`
>
> ---
>
> ## ⚡ Operator Precedence
>
> In C, operator precedence determines how an expression is **grouped**. Operators with higher precedence are grouped before operators with lower precedence.
>
> ### 🥇 Highest → Lowest
>
> > **[ HIGHEST PRECEDENCE ⬆️ ]**
>
> | Priority            | Operator Category                       | Operators                                                  |
> | ------------------- | --------------------------------------- | ---------------------------------------------------------- |
> | 🟥 **15 — HIGHEST** | **Postfix / Primary**                   | `()`, `[]`, `.`, `->`, function calls, `x++`, `x--`        |
> | 🟧 **14**           | **Unary**                               | `++x`, `--x`, `+x`, `-x`, `!x`, `~x`, `*x`, `&x`, `sizeof` |
> | 🟨 **13**           | **Multiplication / Division / Modulus** | `*`, `/`, `%`                                              |
> | 🟨 **12**           | **Addition / Subtraction**              | `+`, `-`                                                   |
> | 🟩 **11**           | **Shift**                               | `<<`, `>>`                                                 |
> | 🟩 **10**           | **Relational**                          | `<`, `<=`, `>`, `>=`                                       |
> | 🟦 **9**            | **Equality**                            | `==`, `!=`                                                 |
> | 🟦 **8**            | **Bitwise AND**                         | `&`                                                        |
> | 🟪 **7**            | **Bitwise XOR**                         | `^`                                                        |
> | 🟪 **6**            | **Bitwise OR**                          | `\|`                                                       |
> | 🟪 **5**            | **Logical AND**                         | `&&`                                                       |
> | 🟪 **4**            | **Logical OR**                          | `\|\|`                                                     |
> | 🟫 **3**            | **Conditional / Ternary**               | `?:`                                                       |
> | ⬛ **2**             | **Assignment**                          | `=`, `+=`, `-=`, `*=`, `/=`, `%=` and others               |
> | ⬜ **1 — LOWEST**    | **Comma**                               | `,`                                                        |
>
> > **[ ⬇️ LOWEST PRECEDENCE ]**
>
> ### 🏷️ Quick Priority Badge
>
> **🥇 HIGHEST**
>
> `Postfix → Unary → Multiplication/Division/Modulus → Addition/Subtraction → Shift → Relational → Equality → Bitwise AND → Bitwise XOR → Bitwise OR → Logical AND → Logical OR → Conditional → Assignment → Comma`
>
> **⬇️ LOWEST**
>
> ---
>
> ### 🔄 Associativity
>
> **Precedence** tells us **which operator group has priority**.
>
> **Associativity** tells us **which direction to group operators when they have the same precedence**.
>
> For example:
>
> ```c
> 5 / 2 * 6
> ```
>
> Both `/` and `*` have the **same precedence** and use **left-to-right associativity**:
>
> ```text
> (5 / 2) * 6
> ```
>
> Therefore:
>
> ```text
> 5 / 2 = 2
> 2 * 6 = 12
> ```
>
> ---
>
> **📌 NOTE:** Precedence determines how an expression is grouped, while **associativity** determines the direction in which operators of the same precedence are grouped. For example, `*`, `/`, and `%` have the same precedence and are **grouped left-to-right**, while assignment operators are **grouped right-to-left**.
>
> **📌 IMPORTANT:** **Operator precedence is not the same as order of evaluation.** Precedence determines the grammatical grouping of an expression; it does not by itself determine when each operand is evaluated.
>
> **📌 REMEMBER:** Do **not** use a generic **BODMAS/BADMAS rule** for C expressions. Instead, use the **C operator precedence table**, followed by **associativity** when operators have equal precedence.
>
> These operator categories and precedence rules are applied throughout **Questions 4, 5, 6, 9, and 14** in this session.

---

### Question 2

**Pseudocode:**

```c
int num = 20 ;
if ( num == 10 ) ;
    printf(" Ten ") ;

```

**Full code:**

```c
#include <stdio.h>

int main() {
    int num = 20 ;
    if ( num == 10 ) ;
        printf(" Ten ") ;
        
    return 0;
}

```

**Explanation of the code:**

* **Step 1:** An integer variable `num` is declared and initialized to 20.
* **Step 2:** The `if` statement checks the condition `num == 10`. Since 20 is not equal to 10, this evaluates to false.
* **Step 3:** Notice the semicolon `;` immediately following the `if` condition. In C, this acts as an empty statement (or null statement) representing the body of the `if` block.
* **Step 4:** Because the condition is false, the program skips this empty statement.
* **Step 5:** Because there are no braces `{}`, the `if` controls only the immediately following statement. The `printf(" Ten ");` statement is therefore executed independently.

**Final output:**
`Ten`

---

### Question 3

**Pseudocode:**

```c
int num = 20 ;
if ( num == 10 )
    ;
printf(" Ten ") ;

```

**Full code:**

```c
#include <stdio.h>

int main() {
    int num = 20 ;
    if ( num == 10 )
        ;
    printf(" Ten ") ;
    
    return 0;
}

```

**Explanation of the code:**

* **Step 1:** An integer variable `num` is initialized to 20.
* **Step 2:** The program evaluates `if ( num == 10 )`, which is false.
* **Step 3:** The line immediately below the `if` statement contains only a semicolon `;`. This behaves exactly like Question 2; it is a null statement serving as the body of the `if` block.
* **Step 4:** Because the condition is false, the null statement is ignored.
* **Step 5:** Because there are no braces `{}`, the `if` controls only the immediately following statement. The `printf(" Ten ");` statement is therefore executed independently.

**Final output:**
`Ten`

---

### Question 4

**Pseudocode:**

```c
int main()
{
    int a=5,b=10;
    if(++a && ++b)
        printf("%d %d",a,b);
    else
        printf("Bhubaneswar");
}

```

**Full code:**

```c
#include <stdio.h>

int main() {
    int a=5,b=10;
    if(++a && ++b)
        printf("%d %d",a,b);
    else
        printf("Bhubaneswar");
        
    return 0;
}

```

**Explanation of the code:**

* **Step 1:** Integers `a` and `b` are initialized to 5 and 10, respectively.
* **Step 2:** The `if` statement contains a logical AND (`&&`) condition. C evaluates the left side first: `++a`. This is a pre-increment operator, so `a` immediately becomes 6.
* **Step 3:** Because 6 is non-zero (true), the program must evaluate the right side to determine the final truth value of the AND operation.
* **Step 4:** It evaluates `++b`. `b` immediately becomes 11. Since 11 is also non-zero (true), the entire condition is true (true && true).
* **Step 5:** The `if` block executes, printing the updated values of `a` and `b`.

**Final output:**
`6 11`

---

### Question 5

**Pseudocode:**

```c
int main()
{
    int movie=1;
    switch(movie << 2 + movie)
    {
        default: printf ("3 Idiots");
        case 4: printf (" Ghajini");
        case 5: printf (" Krrish");
        case 8: printf (" Race");
    }
}

```

**Full code:**

```c
#include <stdio.h>

int main() {
    int movie=1;
    switch(movie << 2 + movie)
    {
        default: printf ("3 Idiots");
        case 4: printf (" Ghajini");
        case 5: printf (" Krrish");
        case 8: printf (" Race");
    }
    
    return 0;
}

```

**Explanation of the code:**

* **Step 1:** The integer `movie` is initialized to 1.
* **Step 2:** The `switch` statement evaluates the expression `movie << 2 + movie`.
* **Step 3:** In C, the addition operator `+` has higher precedence than the bitwise left-shift operator `<<`. So, it evaluates as `movie << (2 + movie)`.
* **Step 4:** Substituting the value of `movie`, we get `1 << (2 + 1)`, which simplifies to `1 << 3`.
* **Step 5:** Left-shifting the binary value 1 by 3 places yields 8 (1 * 2³ = 8).
* **Step 6:** The `switch` expression evaluates to `8`, so control transfers to `case 8:` and executes the corresponding `printf`. (Note: Since there are no break statements and case 8 is the last case, it simply prints and exits the switch).

**Final output:**
` Race`

---

### Question 6

**Pseudocode:**

```c
void main()
{
    int k,num=30;
    k=(num>5? (num<=10?100:200):500);
    printf("%d",k);
}

```

**Full code:**

```c
#include <stdio.h>

int main() {
    int k,num=30;
    k=(num>5? (num<=10?100:200):500);
    printf("%d",k);
    
    return 0;
}

```

**Explanation of the code:**

* **Step 1:** The variable `num` is initialized to 30.
* **Step 2:** The code evaluates a nested ternary operator structure. It begins with the outermost condition: `num > 5`.
* **Step 3:** Since 30 > 5 is true, the code evaluates the expression immediately following the first `?`, which is the inner ternary operation: `(num <= 10 ? 100 : 200)`. (The `: 500` is completely ignored).
* **Step 4:** It evaluates the inner condition: `num <= 10`. Since 30 <= 10 is false, it selects the value after the inner colon `:`.
* **Step 5:** The value 200 is selected and assigned to the variable `k`.
* **Step 6:** `printf` outputs the value of `k`.

**Final output:**
`200`

---

### Question 7

**Pseudocode:**

```c
int main()
{
    switch (5/2*6+3.0) {
        case 3: printf("Amir");
                break;
        case 15: printf("Salman");
                break;
        case 0: printf("Akhaya");
                break;
        default: printf("Sanjay");
    }
}

```

**Full code:**

```c
#include <stdio.h>

int main() {
    switch (5/2*6+3.0) { 
        case 3: printf("Amir");
                break;
        case 15: printf("Salman");
                break;
        case 0: printf("Akhaya");
                break;
        default: printf("Sanjay");
    }
    
    return 0;
}

```

**Explanation of the code:**

* **Step 1:** The program attempts to evaluate the expression inside the `switch` statement: `5 / 2 * 6 + 3.0`.
* **Step 2:** `5 / 2` performs integer division, yielding 2.
* **Step 3:** `2 * 6` is evaluated next, yielding 12.
* **Step 4:** `12 + 3.0` is evaluated. Because `3.0` is a floating-point literal, the integer 12 is implicitly cast to a `double`, resulting in `15.0`.
* **Step 5:** The C standard mandates that the controlling expression of a `switch` statement must have an integer type. Since the result is a `double`, the compiler throws an error.

**Final output:**
`Compilation Error`

---

### Question 8

**Pseudocode:**

```c
int main()
{
    int check=2;
    switch(check)
    {
        case 1: printf("Gandhiji");
        case 2: printf(" SubasBose");
        case 3: printf(" Nehru");
        default: printf(" Patel");
    }
}

```

**Full code:**

```c
#include <stdio.h>

int main() {
    int check=2;
    switch(check)
    {
        case 1: printf("Gandhiji");
        case 2: printf(" SubasBose");
        case 3: printf(" Nehru");
        default: printf(" Patel");
    }
    
    return 0;
}

```

**Explanation of the code:**

* **Step 1:** The variable `check` is initialized to 2.
* **Step 2:** The `switch` statement matches the value of `check` and jumps execution directly to `case 2:`.
* **Step 3:** It executes the corresponding statement, printing `" SubasBose"`.
* **Step 4:** Crucially, there is no `break;` statement at the end of `case 2:`. This causes a phenomenon known as "fallthrough".
* **Step 5:** Program execution falls through to the next case (`case 3:`), printing `" Nehru"`.
* **Step 6:** It falls through again into the `default:` block, printing `" Patel"`.

**Final output:**
` SubasBose Nehru Patel`

---

### Question 9

**Pseudocode:**

```c
int main()
{
    int a=5,b=10;
    if(++a || ++b)
        printf("%d %d",a,b);
    else
        printf("Bhubaneswar");
}

```

**Full code:**

```c
#include <stdio.h>

int main() {
    int a=5,b=10;
    if(++a || ++b)
        printf("%d %d",a,b);
    else
        printf("Bhubaneswar");
        
    return 0;
}

```

**Explanation of the code:**

* **Step 1:** Variables `a` and `b` are initialized to 5 and 10.
* **Step 2:** The `if` statement uses the logical OR (`||`) operator. Evaluation starts on the left side: `++a`.
* **Step 3:** `a` is pre-incremented, updating its value to 6.
* **Step 4:** Because 6 is a non-zero (true) value, and the operator is a logical OR, the entire condition is guaranteed to be true regardless of the right side.
* **Step 5:** C utilizes "short-circuit evaluation" for `||`. Because the left side is true, it skips evaluating the right side entirely. `++b` is never executed, so `b` remains 10.
* **Step 6:** The `if` block executes, printing the values of `a` and `b`.

**Final output:**
`6 10`

---

### Question 10

**Pseudocode:**

```c
int main()
{
    int a=300,b,c;
    if(a>=400)
        b=300;
        c=200;
    printf("B=%d \n C=%d",b,c);
}

```

**Full code:**

```c
#include <stdio.h>

int main() {
    int a=300,b,c;
    if(a>=400)
        b=300;
        c=200;
    printf("B=%d \n C=%d",b,c);
    
    return 0;
}

```

**Explanation of the code:**

* **Step 1:** Variables `a`, `b`, and `c` are declared, but only `a` is assigned an initial value (300).
* **Step 2:** The `if` condition checks if `a >= 400`. Because 300 is not greater than or equal to 400, this is false.
* **Step 3:** Because there are no curly braces `{}` defining the `if` block, only the immediately following statement (`b=300;`) is considered part of the conditional block. This assignment is skipped.
* **Step 4:** The statement `c=200;` is independent of the `if` block and executes normally.
* **Step 5:** The `printf` attempts to output `b` and `c`. However, `b` was never initialized and its assignment was skipped. It holds an indeterminate garbage value from random memory, leading to undefined behavior.

**Final output:**

```text
B=<Garbage Value> 
C=200

```

*(Note: The exact number for the garbage value will vary every time the program runs).*

---

### Question 11

**Pseudocode:**

```c
int num = 5 ;
if ( num == 5)
    printf(" Five ") ;
else ;
    printf(" Not Five ") ;

```

**Full code:**

```c
#include <stdio.h>

int main() {
    int num = 5 ;
    if ( num == 5)
        printf(" Five ") ;
    else ;
        printf(" Not Five ") ;
        
    return 0;
}

```

**Explanation of the code:**

* **Step 1:** `num` is initialized to 5.
* **Step 2:** The `if` condition `num == 5` is true, so the program prints `" Five "`.
* **Step 3:** Next, the compiler sees the `else` keyword. It looks for the statement to execute for the false condition. The semicolon `;` immediately following `else` acts as an empty statement.
* **Step 4:** The `printf(" Not Five ");` is physically below the `else`, but because of the semicolon terminating the `else` block, it is completely independent of the `if-else` construct.
* **Step 5:** The program sequentially executes this final `printf` statement.

**Final output:**
`Five  Not Five`

---

### Question 12

**Pseudocode:**

```c
int num = 10 ;
if ( num == 10) ;
    printf(" Ten ") ;
else
    printf(" Not Ten ") ;

```

**Full code:**

```c
#include <stdio.h>

int main() {
    int num = 10 ;
    if ( num == 10) ;
        printf(" Ten ") ;
    else
        printf(" Not Ten ") ;
        
    return 0;
}

```

**Explanation of the code:**

* **Step 1:** The `if` statement checks `num == 10`. It is immediately terminated by a semicolon `;`, making the `if` block an empty statement.
* **Step 2:** The `printf(" Ten ");` directly beneath it acts as an independent, unconditional line of code.
* **Step 3:** The compiler then encounters the `else` keyword. However, an `else` statement must immediately follow the block or statement associated with an `if`.
* **Step 4:** Because the independent `printf(" Ten ");` stands between the `if`'s null statement and the `else`, the compiler loses the connection and throws an error indicating an `else` was found without a matching `if`.

**Final output:**
`Compilation Error ('else' without a previous 'if')`

---

### Question 13

**Pseudocode:**

```c
if ( -10 )
    printf ( " ok " ) ;
else
    printf ( " Wrong " ) ;

```

**Full code:**

```c
#include <stdio.h>

int main() {
    if ( -10 )
        printf ( " ok " ) ;
    else
        printf ( " Wrong " ) ;
        
    return 0;
}

```

**Explanation of the code:**

* **Step 1:** The condition inside the `if` statement evaluates the integer `-10`.
* **Step 2:** In the C programming language, there is no strict boolean data type for basic conditional checks. Instead, it evaluates integers: `0` is considered false, and *any* non-zero value (both positive and negative) is considered true.
* **Step 3:** Since `-10` is non-zero, the condition evaluates to true.
* **Step 4:** The statement within the `if` block executes, printing `" ok "`.

**Final output:**
`ok`

---

### Question 14

**Pseudocode:**

```c
int num = 10 ;
if ( num = 5 )
    printf ( " ok " ) ;
else
    printf ( " Wrong " ) ;

```

**Full code:**

```c
#include <stdio.h>

int main() {
    int num = 10 ;
    if ( num = 5 )
        printf ( " ok " ) ;
    else
        printf ( " Wrong " ) ;
        
    return 0;
}

```

**Explanation of the code:**

* **Step 1:** The variable `num` is initially set to 10.
* **Step 2:** The `if` condition uses the single equals sign `=`, which is the assignment operator, not the equality checker (`==`).
* **Step 3:** The expression `num = 5` successfully assigns the value 5 to `num`.
* **Step 4:** The evaluated result of an assignment operation in C is the assigned value itself. Thus, the expression `num = 5` returns 5.
* **Step 5:** The condition effectively becomes `if (5)`. Because 5 is non-zero, the condition evaluates to true.
* **Step 6:** The `if` block executes.

**Final output:**
`ok`

---
---

<div align="center"> <h1 style=font-weight: bold;>@PSCodersHub</h1> </div>
