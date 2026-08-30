# PLACEMENT – Session 5: Logical Reasoning
## Date: 27th August 2026

### Q1. Pattern-1

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/32.jpg" alt="Pattern-1" width="500">
</div>

**Code:**

```c
#include <stdio.h>

void pattern1(int n)
{
    int i, j;
    for(i = 1; i <= n; i++)
    {
        for(j = 1; j <= i; j++)
            printf("%d ", i);
        printf("\n");
    }
}

int main()
{
    pattern1(5);
    return 0;
}

```

**Explanation:**

- The outer loop `i` runs from 1 to `n` (5), representing the row numbers.
- The inner loop `j` runs from 1 to the current row number `i`, determining how many elements are printed in that row.
- `printf("%d ", i);` prints the row number itself, repeating it `i` times on each line.

---

### Q2. Pattern-2

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/33.jpg" alt="Pattern-2" width="500">
</div>

**Code:**

```c
#include <stdio.h>

void pattern2(int n)
{
    int i, j;
    for(i = n; i >= 1; i--)
    {
        for(j = 1; j <= i; j++)
            printf("%d ", i);
        printf("\n");
    }
}

int main()
{
    pattern2(5);
    return 0;
}

```

**Explanation:**

- The outer loop `i` is inverted, starting from `n` (5) and decrementing down to 1.
- The inner loop `j` still runs from 1 to `i`. Since `i` starts large, the first row prints 5 elements, the second prints 4, and so on.
- It prints the current value of `i`, resulting in decreasing numbers on each subsequent row.

---

### Q3. Pattern-3

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/34.jpg" alt="Pattern-3" width="500">
</div>

**Code:**

```c
#include <stdio.h>
#include <stdlib.h>

void pattern3(int n)
{
    int i, j;
    for(i = -n; i <= n; i++)
    {
        for(j = 1; j <= abs(i); j++)
            printf("%3d", j);
        printf("\n");
    }
}

int main()
{
    pattern3(5);
    return 0;
}

```

**Explanation:**

- This introduces the **Golden Loop**, running from `-n` to `n`.
- The inner loop runs up to the absolute value of `i` (`abs(i)`).
- When `i = 0`, `abs(i)` is `0`, causing the inner loop to skip entirely and leaving an empty line in the middle of the pattern.
- `j` is printed, so the values count upwards starting from 1 on every row.

---

### Q4. Pattern-4

```text
1 2 3 4 5
1 2 3 4
1 2 3
1 2
1
1
1 2
1 2 3
1 2 3 4
1 2 3 4 5

```

**Code:**

```c
#include <stdio.h>
#include <stdlib.h>

void pattern4(int n)
{
    int i, j;
    for(i = -n; i <= n; i++)
    {
        if(i != 0)
        {
            for(j = 1; j <= abs(i); j++)
                printf("%3d", j);
            printf("\n");
        }
    }
}

int main()
{
    pattern4(5);
    return 0;
}

```

**Explanation:**

- This pattern is almost identical to Pattern-3, but it removes the blank line in the middle.
- The `if(i != 0)` condition effectively skips the execution of the zero row, ensuring the two mirrored triangles touch seamlessly.

---

### Q5. Pattern-5

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/35.jpg" alt="Pattern-5" width="500">
</div>

**Code:**

```c
#include <stdio.h>
#include <stdlib.h>

void pattern5(int n)
{
    int i, j;
    for(i = -n; i <= n; i++)
    {
        for(j = 1; j <= n - abs(i) + 1; j++)
            printf("%d ", j);
        printf("\n");
    }
}

int main()
{
    pattern5(5);
    return 0;
}

```

**Explanation:**

- The inner loop condition is inverted mathematically using `n - abs(i) + 1`.
- At the extremes (`i = -5` or `i = 5`), the loop runs `5 - 5 + 1 = 1` time.
- At the center (`i = 0`), the loop runs `5 - 0 + 1 = 6` times. This creates the expanding and contracting diamond/arrow shape.

---

### Q6. Pattern-6

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/36.jpg" alt="Pattern-6" width="500">
</div>

**Code:**

```c
#include <stdio.h>
#include <stdlib.h>

void pattern6(int n)
{
    int i, j;
    for(i = -n; i <= n; i++)
    {
        if(i != 0)
        {
            for(j = 1; j <= n - abs(i) + 1; j++)
                printf("%d ", j);
            printf("\n");
        }
    }
}

int main()
{
    pattern6(5);
    return 0;
}

```

**Explanation:**

- This takes the logic of Pattern-5 but skips the `i = 0` row using the `if(i != 0)` check.
- Because the center row is skipped, the widest point of the pattern (5 elements) duplicates across the `i = 1` and `i = -1` rows, creating a blockier middle.

---

### Q7. Pattern-7

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/37.jpg" alt="Pattern-7" width="500">
</div>

**Code:**

```c
#include <stdio.h>
#include <stdlib.h>

void pattern7(int n)
{
    int i, j;
    for(i = -n; i <= n; i++)
    {
        if(i != 0)
        {
            for(j = 1; j <= n - abs(i); j++)
                printf("  ");

            for(j = 1; j <= abs(i); j++)
                printf("%2d", j);

            printf("\n");
        }
    }
}

int main()
{
    pattern7(5);
    return 0;
}

```

**Explanation:**

- This pattern adds right-alignment by utilizing an extra inner loop to print spaces.
- The first inner loop prints `n - abs(i)` spaces to push the numbers to the right.
- The second inner loop prints the values from 1 up to `abs(i)`.

---

### Q8. Pattern-8 (Numeric Wrapper)

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/38.jpg" alt="Pattern-8" width="500">
</div>

**Code:**

```c
#include <stdio.h>
#include <stdlib.h>

void pattern8(int n)
{
    int i, j;
    for(i = -(n - 1); i <= n - 1; i++)
    {
        for(j = -(n - 1); j <= n - 1; j++)
        {
            if(abs(i) >= abs(j))
                printf("%2d", abs(i) + 1);
            else
                printf("%2d", abs(j) + 1);
        }
        printf("\n");
    }
}

int main()
{
    pattern8(3);
    return 0;
}

```

**Explanation:**

- The pattern is essentially a 2D coordinate system running from `-(n-1)` to `n-1` for both rows and columns.
- It prints concentric squares. The value printed at any coordinate is determined by which "ring" it falls into, which is mathematically evaluated by checking if the absolute row index or column index is larger: `max(abs(i), abs(j)) + 1`.

---

### Q9. Pattern-9 (Butterfly)

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/39.jpg" alt="Pattern-09" width="400">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/40.jpg" alt="Pattern-9" width="400">
</div>

**Code:**

```c
#include <stdio.h>
#include <stdlib.h>

void pattern9(int n)
{
    int i, j;
    for(i = -n; i <= n; i++)
    {
        for(j = -n; j <= n; j++)
        {
            if(abs(i) + abs(j) <= n - 1)
                printf("  ");
            else
                printf("* ");
        }
        printf("\n");
    }
}

int main()
{
    pattern9(8);
    return 0;
}

```

**Explanation:**

- This uses a 2D grid approach again, this time iterating both `i` and `j` from `-n` to `n`.
- The condition `abs(i) + abs(j) <= n - 1` defines a diamond-shaped hollow region in the center. Inside this diamond, spaces are printed. Outside of it, asterisks `*` are printed, creating the butterfly shape.

---

### Q10. Pattern-10 (X Pattern)

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/41.jpg" alt="Pattern-10" width="500">
</div>

**Code:**

```c
#include <stdio.h>
#include <stdlib.h>

void pattern10(int n)
{
    int i, j;
    for(i = -n; i <= n; i++)
    {
        for(j = -n; j <= n; j++)
        {
            if(abs(i) == abs(j))
                printf("X ");
            else
                printf("  ");
        }
        printf("\n");
    }
}

int main()
{
    pattern10(2);
    return 0;
}

```

**Explanation:**

- A perfect 'X' shape is mathematically defined as the coordinates where the absolute value of the row equals the absolute value of the column (`abs(i) == abs(j)`).
- The nested loops check every point on the grid. If the condition is met, an "X" is printed; otherwise, blank space is provided.

---

### Q11. Pattern-11 (X Pattern formed by numbers)

<div align="center">
  <img src="https://github.com/PSCodersHub/PLACEMENT/raw/main/Assets/42.jpg" alt="Pattern-11" width="500">
</div>

**Code:**

```c
#include <stdio.h>
#include <stdlib.h>

void pattern11(int n)
{
    int i, j;
    for(i = -n; i <= n; i++)
    {
        for(j = -n; j <= n; j++)
        {
            if(abs(i) == abs(j))
                printf("%d ", abs(i) + 1);
            else
                printf("  ");
        }
        printf("\n");
    }
}

int main()
{
    pattern11(2);
    return 0;
}

```

**Explanation:**

- This takes the exact structural logic from Pattern-10, relying on `abs(i) == abs(j)` to trace the main diagonals.
- Instead of printing a character, it prints `abs(i) + 1`. This maps the row/column offset into a numeric value, causing the ends of the 'X' to display `3`, while tapering down to `1` at the center coordinate (0,0).

---

### Q12. The Golden Loop (with Zero)

```text
 4  3  2  1  0  1  2  3  4

```

**Code:**

```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int i;
    // The Golden Loop
    for(i = -4; i <= 4; i++)
    {
        printf("%2d ", abs(i));
    }
    printf("\n");
    return 0;
}

```

**Explanation:**

- This program demonstrates the foundation of the **Golden Loop** .
- The `for` loop runs from a negative value `-4` up to `4`.
- By utilizing the `abs()` function, the negative index values are converted to their positive equivalents (`abs(-4) = 4`, `abs(-3) = 3`, etc.).
- This naturally creates a mirrored countdown and count-up sequence pivoting around `0` using only a single loop.

---

### Q13. The Golden Loop (without Zero)

```text
 4  3  2  1  1  2  3  4

```

**Code:**

```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int i;
    // The Golden Loop
    for(i = -4; i <= 4; i++)
    {
        if(i != 0)
        {
            printf("%2d ", abs(i));
        }
    }
    printf("\n");
    return 0;
}

```

**Explanation:**

- This variation uses the exact same Golden Loop logic running from `-4` to `4`.
- An `if (i != 0)` condition is introduced inside the loop body.
- This condition evaluates to false when `i` reaches `0`, causing the loop to skip printing for that specific iteration.
- As a result, the `0` is completely omitted from the center, seamlessly joining the two halves of the sequence.

---
---

<div align="center"> <h1 style="font-weight: bold;">@PSCodersHub</h1> </div>
