The determinant is a **special number** that can be calculated from a [matrix](https://www.mathsisfun.com/algebra/matrix-introduction.html).

The matrix has to be square (same number of rows and columns) like this one:

|     | $$\begin{bmatrix} 3 & 8 \\ 4 & 6 \end{bmatrix}$$ |
| --- | ------------------------------------------------ |

A Matrix  
(This one has 2 Rows and 2 Columns)


Let us calculate the determinant of that matrix:
$$
3×6 − 8×4  
= 18 − 32  
= −14
$$
Easy, hey? Here is another example:

### Example:

B =
$$B=\begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}$$


The **symbol** for determinant is two vertical lines either side like this:

$$|B| = 1×4 − 2×3  
= 4 − 6  
= −2$$

(Note: it is the same symbol as [absolute value](https://www.mathsisfun.com/numbers/absolute-value.html).)

## What is it for?

The determinant helps us find the [inverse of a matrix](https://www.mathsisfun.com/algebra/matrix-inverse-minors-cofactors-adjugate.html), tells us things about the matrix that are useful in [systems of linear equations](https://www.mathsisfun.com/algebra/systems-linear-equations.html), [calculus](https://www.mathsisfun.com/calculus/index.html) and more.

## Calculating the Determinant

First of all the matrix must be **square** (i.e. have the same number of rows as columns). Then it is just arithmetic.

## For a 2×2 Matrix

For a 2×2 matrix (2 rows and 2 columns):
$$
|A|=\begin{bmatrix} a & b \\ c & d \end{bmatrix}
$$
The determinant is:

$|A| = ad − bc$ 

_"The determinant of A equals a times d minus b times c"_

|   |   |   |
|---|---|---|
|It is easy to remember when you think of a cross:<br><br>- Blue is positive (+ad),<br>- Red is negative (−bc)||![a by d, b by c](https://www.mathsisfun.com/algebra/images/matrix-2x2-det.svg)|


## For a 3×3 Matrix

For a 3×3 matrix (3 rows and 3 columns):

$$
|A|=\begin{bmatrix} a & b& c\\ d & e&f\\ g&h&i \end{bmatrix}
$$
The determinant is:

$$
|A| = a(ei − fh) − b(di − fg) + c(dh − eg)  
$$
_"The determinant of A equals ... etc"_

It may look complicated, but **there is a pattern**:

![multiply pattern](https://www.mathsisfun.com/algebra/images/matrix-3x3-det.svg)

To work out the determinant of a **3×3** matrix:

- Multiply **a** by the **determinant of the 2×2 matrix** that is **not in a**'s row or column.
- Likewise for **b**, and for **c**
- Sum them up, but remember the minus in front of the **b**

As a formula _(remember the vertical bars_ || _mean "determinant of")_:

![A Matrix](https://www.mathsisfun.com/algebra/images/matrix-3x3-det-latex.gif)  
_"The determinant of A equals a times the determinant of ... etc"_

### Example:
$$
D =\begin{bmatrix} 6 &1&1\\ 4 & -2&5\\ 2&8&7 \end{bmatrix}
$$

$$|D|= 6×(−2×7 − 5×8) − 1×(4×7 − 5×2) + 1×(4×8 − (−2×2))
$$
$$
 <=>6×(−54) − 1×(18) + 1×(36)

 <=> −306
 $$

## For 4×4 Matrices and Higher

The pattern continues for 4×4 matrices:

- **plus** **a** times the determinant of the matrix that is **not** in **a**'s row or column,
- **minus b** times the determinant of the matrix that is **not** in **b**'s row or column,
- **plus c** times the determinant of the matrix that is **not** in **c**'s row or column,
- **minus d** times the determinant of the matrix that is **not** in **d**'s row or column,

![multiply pattern](https://www.mathsisfun.com/algebra/images/matrix-4x4-det.svg)

As a formula:

![4x4 determinant formula](https://www.mathsisfun.com/algebra/images/matrix-4x4-det-latex.gif)

Notice the **+−+−** pattern (+a... −b... +c... −d...). This is important to remember.