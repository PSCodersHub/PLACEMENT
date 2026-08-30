# PLACEMENT – Session 5: Logical Reasoning
## Date: 27th August 2026

## Approach: How to Solve Pattern Printing Problems

1. **Divide** the given pattern into number of rows and columns.
2. **Label** the rows and columns appropriately with serial values.
3.  Try to **Find out relationship** between row and column values in a particular row (say candidate row).
4. Try to **Point out the change** of values in a row, column, and in successive rows & columns.
5. **Establish a mathematical formula** for change of column value or row value.
6. **Generalize**: once you have done for candidate row, then iterate it for other rows and make it generic.

---

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

> **Explanation:**

- The outer loop `i` runs from 1 to `n` (5), representing the row numbers.
- The inner loop `j` runs from 1 to the current row number `i`, determining how many elements are printed in that row.
- `printf("%d ", i);` prints the row number itself, repeating it `i` times on each line.

> **How we get there (rule-based):**

1. **Divide**: Rows `i` from 1 to `n`. Columns `j` from 1 to `i` (row-dependent width).
2. **Label**: Row index = `i`. Column index = `j`.
3. **Candidate row**: Take `i = 3` — it prints `3 3 3` (three columns, all showing the row number).
4. **Track the change**: Column *count* increases by 1 each row (row 1 → 1 col, row 2 → 2 cols...). Column *value* stays fixed at `i` for the whole row.
5. **Formula**: number of columns = `i`; value printed = `i`.
6. **Generalize**: Loop `j` from 1 to `i` for every `i` from 1 to `n` — same rule reused for every row.

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

> **Explanation:**

- The outer loop `i` is inverted, starting from `n` (5) and decrementing down to 1.
- The inner loop `j` still runs from 1 to `i`. Since `i` starts large, the first row prints 5 elements, the second prints 4, and so on.
- It prints the current value of `i`, resulting in decreasing numbers on each subsequent row.

> **How we get there (rule-based):**

1. **Divide**: Rows `i` from `n` down to 1. Columns `j` from 1 to `i`.
2. **Label**: Row index = `i` (descending). Column index = `j`.
3. **Candidate row**: First row (`i = n`) prints `n` columns; last row (`i = 1`) prints 1 column.
4. **Track the change**: Same rule as Pattern-1, just the row order is reversed — `i` decrements instead of increments.
5. **Formula**: number of columns = `i`; value printed = `i` (identical formula to Pattern-1).
6. **Generalize**: Reversing only the outer loop direction (`i--` instead of `i++`) flips the whole shape without touching the inner-loop logic.

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

> **Explanation:**

- This introduces the **Golden Loop**, running from `-n` to `n`.
- The inner loop runs up to the absolute value of `i` (`abs(i)`).
- When `i = 0`, `abs(i)` is `0`, causing the inner loop to skip entirely and leaving an empty line in the middle of the pattern.
- `j` is printed, so the values count upwards starting from 1 on every row.

> **How we get there (rule-based):**

1. **Divide**: Rows `i` from `-n` to `n` (the Golden Loop). Columns `j` from 1 to `abs(i)`.
2. **Label**: Row index = `i` (signed). Column index = `j`.
3. **Candidate row**: `i = 3` and `i = -3` should look identical — both print `1 2 3`. That tells us the column count depends on *distance from 0*, not sign.
4. **Track the change**: Column count grows as `i` moves away from 0 in either direction, and hits 0 exactly at `i = 0`.
5. **Formula**: number of columns = `abs(i)`.
6. **Generalize**: Using `abs(i)` in one loop (`i` from `-n` to `n`) auto-generates both the shrinking top half and growing bottom half — no need for two separate loops.

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

> **Explanation:**

- This pattern is almost identical to Pattern-3, but it removes the blank line in the middle.
- The `if(i != 0)` condition effectively skips the execution of the zero row, ensuring the two mirrored triangles touch seamlessly.

> **How we get there (rule-based):**

1. **Divide**: Same grid as Pattern-3 — rows `-n` to `n`, columns 1 to `abs(i)`.
2. **Label**: Same as Pattern-3.
3. **Candidate row**: Row `i = 0` gives `abs(0) = 0` columns — an empty line splitting the shape.
4. **Track the change**: Every row except `i = 0` behaves normally; only the middle row breaks the pattern (produces a gap).
5. **Formula**: Same as Pattern-3, plus a filter: skip printing when `i == 0`.
6. **Generalize**: Adding `if (i != 0)` around the existing logic removes just the one row that breaks the flow, without changing the formula for any other row.

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

> **Explanation:**

- The inner loop condition is inverted mathematically using `n - abs(i) + 1`.
- At the extremes (`i = -5` or `i = 5`), the loop runs `5 - 5 + 1 = 1` time.
- At the center (`i = 0`), the loop runs `5 - 0 + 1 = 6` times. This creates the expanding and contracting diamond/arrow shape.

> **How we get there (rule-based):**

1. **Divide**: Rows `i` from `-n` to `n`. Columns `j` from 1 up to a row-dependent count.
2. **Label**: Row index = `i` (signed). Column index = `j`.
3. **Candidate row**: Take `i = 0` (middle row) — prints the most columns: `1 2 3 4 5 6`. Take `i = 5` (edge row) — prints only `1`.
4. **Track the change**: As `i` moves away from 0 in either direction, the column count shrinks by 1 each step. Depends only on distance from 0, not sign — signal to use `abs(i)`.
5. **Formula**: number of columns = `n - abs(i) + 1`. Check: at `i=0`, `5-0+1=6` ✓. At `i=5`, `5-5+1=1` ✓.
6. **Generalize**: Since `abs(i)` treats `+i` and `-i` the same, the single loop `for i = -n to n` naturally produces both the growing and shrinking halves — no separate code needed for top and bottom.

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

> **Explanation:**

- This takes the logic of Pattern-5 but skips the `i = 0` row using the `if(i != 0)` check.
- Because the center row is skipped, the widest point of the pattern (5 elements) duplicates across the `i = 1` and `i = -1` rows, creating a blockier middle.

> **How we get there (rule-based):**

1. **Divide**: Same grid as Pattern-5 — rows `-n` to `n`, columns 1 to `n - abs(i) + 1`.
2. **Label**: Same as Pattern-5.
3. **Candidate row**: Row `i = 0` would normally give the widest row (`n+1` columns); rows `i = 1` and `i = -1` give the next-widest (`n` columns).
4. **Track the change**: If `i = 0` is removed, the widest columns now belong to `i = 1` and `i = -1`, which are duplicates of each other — creating a flat/blocky middle instead of a single peak.
5. **Formula**: Same as Pattern-5, plus a filter: skip printing when `i == 0`.
6. **Generalize**: Same `if (i != 0)` trick as Pattern-4 — reused on a different base formula to get a different shape.

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

> **Explanation:**

- This pattern adds right-alignment by utilizing an extra inner loop to print spaces.
- The first inner loop prints `n - abs(i)` spaces to push the numbers to the right.
- The second inner loop prints the values from 1 up to `abs(i)`.

> **How we get there (rule-based):**

1. **Divide**: Rows `i` from `-n` to `n` (skip 0). Each row has two zones: leading spaces, then numbers.
2. **Label**: Row index = `i`. Space-column count = `n - abs(i)`. Number-column count = `abs(i)`.
3. **Candidate row**: Take `i = 5` (edge row, `n=5`) — 0 spaces, then `1 2 3 4 5` (right-aligned, full width). Take `i = 1` — 4 spaces, then just `1`.
4. **Track the change**: As `abs(i)` grows, spaces shrink and numbers grow — they trade off so the total width stays constant, keeping the right edge aligned.
5. **Formula**: spaces = `n - abs(i)`; numbers = `abs(i)`.
6. **Generalize**: Two back-to-back inner loops (space-loop then number-loop) applied to every row `i` produce consistent right-alignment across the whole pattern.

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

> **Explanation:**

- The pattern is essentially a 2D coordinate system running from `-(n-1)` to `n-1` for both rows and columns.
- It prints concentric squares. The value printed at any coordinate is determined by which "ring" it falls into, which is mathematically evaluated by checking if the absolute row index or column index is larger: `max(abs(i), abs(j)) + 1`.

> **How we get there (rule-based):**

1. **Divide**: 2D grid — rows `i` from `-(n-1)` to `n-1`, columns `j` from `-(n-1)` to `n-1`.
2. **Label**: Each cell is `(i, j)`.
3. **Candidate row**: Take `i = 0` (middle row) — values should increase moving outward from `j = 0` toward the edges, forming a ring pattern.
4. **Track the change**: The value at any cell depends on whichever of `abs(i)` or `abs(j)` is *larger* — that's what determines which "ring" (square layer) the cell belongs to.
5. **Formula**: value = `max(abs(i), abs(j)) + 1`.
6. **Generalize**: Checking this per-cell condition across the full `i`/`j` grid automatically draws all concentric square rings, not just the outer or inner one.

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

> **Explanation:**

- This uses a 2D grid approach again, this time iterating both `i` and `j` from `-n` to `n`.
- The condition `abs(i) + abs(j) <= n - 1` defines a diamond-shaped hollow region in the center. Inside this diamond, spaces are printed. Outside of it, asterisks `*` are printed, creating the butterfly shape.

> **How we get there (rule-based):**

1. **Divide**: 2D grid — rows `i` from `-n` to `n`, columns `j` from `-n` to `n`.
2. **Label**: Each cell is `(i, j)`.
3. **Candidate row**: Take `i = 0` (middle row) — cells near `j = 0` should be blank (hollow center), cells far from `j = 0` should be `*`.
4. **Track the change**: As `abs(i)` grows (further row) OR `abs(j)` grows (further column), you move away from the hollow zone toward the star zone — so the boundary depends on the *combined* distance `abs(i) + abs(j)`.
5. **Formula**: if `abs(i) + abs(j) <= n - 1` → blank (hollow diamond); else → `*`.
6. **Generalize**: This single condition, checked for every `(i, j)`, produces the diamond hollow and star border for all four wings of the butterfly at once — no special-casing per quadrant.

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

> **Explanation:**

- A perfect 'X' shape is mathematically defined as the coordinates where the absolute value of the row equals the absolute value of the column (`abs(i) == abs(j)`).
- The nested loops check every point on the grid. If the condition is met, an "X" is printed; otherwise, blank space is provided.

> **How we get there (rule-based):**

1. **Divide**: 2D grid — rows `i` from `-n` to `n`, columns `j` from `-n` to `n`.
2. **Label**: Each cell is `(i, j)`.
3. **Candidate row**: Take `i = 1` — the `X` should appear at `j = 1` and `j = -1`, i.e. where `abs(j)` matches `abs(i)`.
4. **Track the change**: The `X` marks move diagonally as `i` changes — for every row, the matching columns are exactly `j = i` and `j = -i`.
5. **Formula**: if `abs(i) == abs(j)` → print `X`; else → blank.
6. **Generalize**: Checking this condition for every `(i, j)` in the grid draws both diagonals of the X across all rows simultaneously.

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

> **Explanation:**

- This takes the exact structural logic from Pattern-10, relying on `abs(i) == abs(j)` to trace the main diagonals.
- Instead of printing a character, it prints `abs(i) + 1`. This maps the row/column offset into a numeric value, causing the ends of the 'X' to display `3`, while tapering down to `1` at the center coordinate (0,0).

> **How we get there (rule-based):**

1. **Divide**: Same grid as Pattern-10.
2. **Label**: Same as Pattern-10.
3. **Candidate row**: Take `i = 2` (outer row, `n=2`) — the X arms here should show the largest number; center `(0,0)` should show the smallest.
4. **Track the change**: Same diagonal condition as Pattern-10, but now the *value* printed should scale with distance from center — larger `abs(i)` (or `abs(j)`) should mean a larger number.
5. **Formula**: same condition `abs(i) == abs(j)`, but print `abs(i) + 1` instead of a fixed character.
6. **Generalize**: Reusing Pattern-10's diagonal condition but swapping the printed character for a computed value shows how the same structural formula can be reused for a different visual output.

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

> **Explanation:**

- This program demonstrates the foundation of the **Golden Loop** .
- The `for` loop runs from a negative value `-4` up to `4`.
- By utilizing the `abs()` function, the negative index values are converted to their positive equivalents (`abs(-4) = 4`, `abs(-3) = 3`, etc.).
- This naturally creates a mirrored countdown and count-up sequence pivoting around `0` using only a single loop.

> **How we get there (rule-based):**

1. **Divide**: A single row, columns `i` from `-4` to `4`.
2. **Label**: Column index = `i` (signed).
3. **Candidate column**: `i = -4` and `i = 4` should print the same value (`4`), and `i = 0` should print `0`.
4. **Track the change**: Value depends only on distance from 0, not sign — mirrored on both sides of center.
5. **Formula**: value printed = `abs(i)`.
6. **Generalize**: A single loop from `-n` to `n` with `abs(i)` produces the full mirrored countdown-then-countup sequence without writing two separate loops.

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

> **Explanation:**

- This variation uses the exact same Golden Loop logic running from `-4` to `4`.
- An `if (i != 0)` condition is introduced inside the loop body.
- This condition evaluates to false when `i` reaches `0`, causing the loop to skip printing for that specific iteration.
- As a result, the `0` is completely omitted from the center, seamlessly joining the two halves of the sequence.

> **How we get there (rule-based):**

1. **Divide**: Same single row as Q12, columns `i` from `-4` to `4`.
2. **Label**: Same as Q12.
3. **Candidate column**: `i = 0` is the only column that should be skipped; all others follow Q12's rule.
4. **Track the change**: Same mirrored behavior as Q12, except the center point should produce no output at all.
5. **Formula**: Same as Q12 (`abs(i)`), plus a filter: skip when `i == 0`.
6. **Generalize**: Adding `if (i != 0)` around the existing Golden Loop formula removes just the center value, joining both mirrored halves seamlessly — same filter trick used in Patterns 4 and 6.

---
---

<div align="center"> <h1 style="font-weight: bold;">@PSCodersHub</h1> </div>
