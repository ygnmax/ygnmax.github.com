---
title: Linear Algebra Basics
date: 2020-2-22
tags: 
	- Linear Algebra
categories: 
	- Mathematics
	- Algebra
	- Linear Algebra
mathjax: true
---

This note contains basic knowledge and summary of Linear Algebra, including vector, matrix, linear transform etc. The main ideas come from 3Blue1Brown.

# vector

## basis

## transformation

### linear transformation

+ $90^\circ$ counterclockwise rotate

$$
\left[\begin{array}{cc}
0 & -1 \\
1 & 0
\end{array}
\right]
$$

+ $90^\circ$ clockwise rotate

$$
\left[\begin{array}{cc}
0 & 1 \\
-1 & 0
\end{array}
\right]
$$

+ rightward shear

$$
\left[\begin{array}{cc}
1 & 1 \\
0 & 1
\end{array}
\right]
$$

+ leftward shear

$$
\left[\begin{array}{cc}
1 & -1 \\
0 & 1
\end{array}
\right]
$$

+ identical transformation

$$
\left[\begin{array}{cc}
1 & 0 \\
0 & 1
\end{array}
\right]
$$



### linear dependent and independent

## matrix multiplication

+ $2 \times 1$ example

$$
\begin{eqnarray*}
\left[\begin{array}{cc}
a & b \\
c & d
\end{array}\right]
\left[\begin{array}{c}
x \\
y
\end{array}\right] =
x \left[\begin{array}{c}
a \\
b
\end{array}\right] + 
y \left[\begin{array}{c}
c \\
d
\end{array}\right] =
\left[\begin{array}{c}
ax+cy \\
bx+dy
\end{array}\right]
\end{eqnarray*}
$$

+ $2 \times 2$ example

$$
\begin{eqnarray*}
\left[\begin{array}{cc}
a & b \\
c & d
\end{array}\right]
\left[\begin{array}{cc}
e & f \\
g & h
\end{array}\right]=
\left[\begin{array}{cc}
ae+bg & af+bh \\
ce+dg & cf+dh
\end{array}\right]
\end{eqnarray*}
$$

+ $3 \times 1$ example
  $$
  \begin{eqnarray*}
  \left[\begin{array}{ccc}
  0 & 1 & 2 \\
  3 & 4 & 5 \\
  6 & 7 & 8
  \end{array}\right]
  \left[\begin{array}{ccc}
  x \\
  y \\
  z
  \end{array}\right]=
  x \left[\begin{array}{ccc}
  0 \\
  3 \\
  6
  \end{array}\right] + 
  y \left[\begin{array}{ccc}
  1 \\
  4 \\
  7
  \end{array}\right] + 
  z \left[\begin{array}{ccc}
  2 \\
  5 \\
  8
  \end{array}\right]
  \end{eqnarray*}
  $$

+ $3 \times 3$ example

$$
\begin{eqnarray*}
\left[\begin{array}{ccc}
0 & 1 & 2 \\
3 & 4 & 5 \\
6 & 7 & 8
\end{array}\right]
\left[\begin{array}{ccc}
x_1 & x_2 & x_3 \\
y_1 & y_2 & y_3 \\
z_1 & z_2 & z_3
\end{array}\right]=
\left[\begin{array}{ccc}
0x_1+1y_1+2z_1 & 0x_2+1y_2+2z_2 & 0x_3+1y_3+2z_3 \\
3x_1+4y_1+5z_1 & 3x_2+4y_2+5z_2 & 3x_3+4y_3+5z_3 \\
6x_1+7y_1+8z_1 & 6x_2+7y_2+8z_2 & 6x_3+7y_3+8z_3 \\
\end{array}\right]
\end{eqnarray*}
$$

### determinant

$$
\begin{eqnarray*}
\left|\begin{array}{ccc}
0 & 1 & 2 \\
3 & 4 & 5 \\
6 & 7 & 8
\end{array}\right|
=
0 \left|\begin{array}{cc}
4 & 5 \\
7 & 8
\end{array}\right| - 
1 \left|\begin{array}{ccc}
3 & 6 \\
5 & 8
\end{array}\right| + 
2 \left|\begin{array}{ccc}
3 & 4 \\
6 & 7 \\
\end{array}\right|
\end{eqnarray*}
$$



# linear system of equations

Consider a linear system of equation:
$$
\begin{eqnarray*}
0x + 1y + 2z &=& -3 \\
3x + 4y + 5z &=& 0 \\
6x + 7y + 8z &=& 2
\end{eqnarray*}
$$
rewrite them in matrix format:
$$
\begin{eqnarray*}
\left[\begin{array}{ccc}
0 & 1 & 2 \\
3 & 4 & 5 \\
6 & 7 & 8
\end{array}\right]
\left[\begin{array}{ccc}
x \\
y \\
z
\end{array}\right]=
\left[\begin{array}{ccc}
-3 \\
0 \\
2
\end{array}\right]
\end{eqnarray*}
$$
we can abstract them as this:
$$
A \vec x = \vec v
$$
here $A$ is a linear transformation. we need to find  $\vec x$ to match $\vec a$ after the linear transformation.

### inverse matrix

find a transformation inverse the original transformation
$$
A^{-1}A=\left[\begin{array}{cc} 1 & 0 \\ 0 & 1\end{array}\right]
$$

### rank

the number of dimensions in the output of a transformation

### column space

column space is the span of columns （以列为基向量的空间）

The rank is the number of dimensions in the column space. (full rank)

zero vector is always in the column space. 

### null space and kernel

+ For a full rank transformation, __the only vector__ that lands at the origin is the __zero vector itself__.
+ For matrices that aren't full rank, they will be squish to a smaller dimension, which means a series of vectors will land at the origin. 
+ This set of vectors that lands on the origin is called the __null space__ or __kernel of the matrix__.
  + the space of all vectors become null, and they land on the zero vectors.

+ For linear system equations:
  + __When $\vec v$ is a zero vector, then the null space gives you all of the possible solutions__ to the equation.

## non-square matrices

A 3 by 2 matrix means mapping two dimensions to three dimensions
$$
\begin{eqnarray*}
\left[\begin{array}{ccc}
0 & 1 \\
3 & 4 \\
6 & 7
\end{array}\right]
\end{eqnarray*}
$$

+ Two columns indicate that the input space has two basis vectors. 

+ Three rows indicate that the landing spots of each of those basis vectors is described with three separate coordinates.

Similarly,  a 2 by 3 matrix means mapping three dimensions to two dimensions.
$$
\begin{eqnarray*}
\left[\begin{array}{ccc}
0 & 1 & 2 \\
3 & 4 & 5
\end{array}\right]
\end{eqnarray*}
$$
A 1 by 2 matrix means mapping a surface to an axis(number line).
$$
\begin{eqnarray*}
\left[\begin{array}{ccc}
0 & 1
\end{array}\right]
\end{eqnarray*}
$$

# dot product

## rules

+ order doesn't matter.

$$
\begin{eqnarray*}
\vec w \cdot \vec v = 
\left[\begin{array}{cc}
-1 \\
2
\end{array}\right] \cdot
\left[\begin{array}{cc}
5 \\
7
\end{array}\right] =
-1 \times 5 + 2 \times 7 = 9
\end{eqnarray*}
$$

$$
\begin{eqnarray*}
\vec u \cdot \vec v = 
\left[\begin{array}{cc}
u_x & u_y
\end{array}\right] \cdot
\left[\begin{array}{cc}
x \\
y
\end{array}\right] =
u_x\cdot x + u_y\cdot y
\end{eqnarray*}
$$

### projection

$$
\vec u \cdot \vec v >0
$$

$$
\vec u \cdot \vec v = 0
$$

$$
\vec u \cdot \vec v <0
$$



### duality

1 $\times$ 2 matrices and 2d vectors

dot product is corresponding to a unique linear transformation from multiple-dimension space to 1-d space

# cross product

## rules

+ order matters, which should be the same order as basis vector

$$
\vec u \times \vec v = -\vec v \times \vec u
$$

$$
\vec u \times \vec v = 
\left[\begin{array}{cc}
-1 \\
2
\end{array}\right] \times
\left[\begin{array}{cc}
5 \\
7
\end{array}\right] =
\left|\begin{array}{cc}
-1 & 5 \\
2 & 7
\end{array}\right| = 
-7-10 = -17 
$$

### area

the determinant of the matrix combined by two vectors is the ratio of the scaled area

+ more perpendicular -> larger area of cross product

$$

$$

### a new vector

the outcome of cross product is a vector:

+ length is the area of parallelogram
+ direction is perpendicular to the parallelogram based on right-hand rule

$$
\vec v \times \vec w = 
\left[\begin{array}{cc}
v_1 \\
v_2 \\
v_3
\end{array}\right] \times
\left[\begin{array}{cc}
w_1 \\
w_2 \\
w_3
\end{array}\right] =
\left|\begin{array}{cc}
i & v_1 & w_1 \\
j & v_2 & w_2 \\
k & v_3 & w_3
\end{array}\right| = 
i(v_2w_3-v3w2)+j(v_1w_3-v_3w_1)+k(v_1w_2-v_2w_1)
$$

## meaning

Define a linear function
$$
f\left(\left[\begin{array}{cc}
x \\
y \\
z
\end{array}\right]\right) 
=
\left|\begin{array}{cc}
x & v_1 & w_1 \\
y & v_2 & w_2 \\
z & v_3 & w_3
\end{array}\right|
=
\left[\begin{array}{ccc}
p_1 \\
p_2 \\
p_3
\end{array}\right] \cdot
\left[\begin{array}{ccc}
x \\
y \\
z
\end{array}\right]
$$
which is the volume of a parallelepiped

which is also a 3d to 1d linear transformation

# basis transformation

## coordinate system and basis vectors

The ordinary basis vectors under the common coordinate system
$$
i=\left[\begin{array}{cc}
1 \\
0
\end{array}\right],~
j=\left[\begin{array}{cc}
0 \\
1
\end{array}\right]
$$
imagine a new pair of vectors, which are defined by the ordinary basis vectors (or common coordinate system), and they are the basis vectors of a  new coordinate system:
$$
\vec b_1=\left[\begin{array}{cc}
2 \\
1
\end{array}\right],~
\vec b_2=\left[\begin{array}{cc}
-1 \\
1
\end{array}\right]
$$
in the new coordinate system, $\vec b_1$ and $\vec b_2$ are the basis vector.

## vectors in different basis

### from new coordinates to ordinary coordinates

Consider such an example. The $\left[\begin{array}{cc}
-1 \\
2
\end{array}\right]$ is a vector in the new coordinate system (using the new basis $\vec b_1$ and $\vec b_2 $), and $\left[\begin{array}{cc}
-4 \\
1
\end{array}\right]$ is the corresponding (same) vector in the ordinary coordinate system (using the ordinary basis $i$ and $j$).

Now, there are two roles of the transformation matrix:
$$
\left[\begin{array}{cc}
2 & -1 \\
1 & 1
\end{array}\right]
$$
First, __numerically__,  this is the matrix which is used to compute the vector from the new basis to the ordinary basis
$$
\left[\begin{array}{cc}
2 & -1 \\
1 & 1
\end{array}\right]
\left[\begin{array}{cc}
-1 \\
2
\end{array}\right]=
-1\left[\begin{array}{cc}
2 \\
1
\end{array}\right]+
2
\left[\begin{array}{cc}
-1 \\
1
\end{array}\right]=
\left[\begin{array}{cc}
-4 \\
1
\end{array}\right]
$$
but __geometrically__, this matrix can be regarded as a transformation matrix from the ordinary basis to the new basis:
$$
\left[\begin{array}{cc}
2 & -1 \\
1 & 1
\end{array}\right] = \left[\begin{array}{cc}
2 & -1 \\
1 & 1
\end{array}\right]
\left[\begin{array}{cc}
1 & 0 \\
0 & 1
\end{array}\right]
$$
Here, the key point is the vectors shares the same coordinates in the common coordinate system and the new coordinate system are not the same vector. They only share the same signs.

The above is used to compute corresponding vectors using the ordinary basis __if we know a vector in the new coordinate system__. Just take __the new coordinate basis matrix__ and __the coordinate vector__,and do the matrix-vector multiplication:

### from ordinary coordinates to new coordinates

Inversely, if we know a vector (in the common coordinate system) which is $\left[\begin{array}{cc}
3 \\
2
\end{array}\right]$ and we want to compute the corresponding vector in the new coordinate system, which is defined by  $\vec b_1$ and $\vec b_2$ , then we should do the following things:

1. take the inverse of the new basis matrix

$$
\left[\begin{array}{cc}
2 & -1 \\
1 & 1
\end{array}\right]^{-1} =
\left[\begin{array}{cc}
\frac{1}{3} & \frac{1}{3} \\
-\frac{1}{3} & \frac{2}{3}
\end{array}\right]
$$

2. compute the matrix and vector product:
   $$
   \left[\begin{array}{cc}
   \frac{1}{3} & \frac{1}{3} \\
   -\frac{1}{3} & \frac{2}{3}
   \end{array}\right]
   \left[\begin{array}{cc}
   3 \\
   2
   \end{array}\right] = 
   \left[\begin{array}{cc}
   \frac{5}{3} \\
   \frac{1}{3}
   \end{array}\right]
   $$

Then, the corresponding (same) vector in the new coordinate system is $\left[\begin{array}{cc}
\frac{5}{3} \\
\frac{1}{3}
\end{array}\right]$.

### Summary

$A$ is the new basis matrix written in the ordinary coordinates, like $\left[\begin{array}{cc}
2 & -1 \\
1 & 1
\end{array}\right]$,

and $ \vec x $ is a vector written in the new coordinates, like $\left[\begin{array}{cc}
-1 \\
2
\end{array}\right]$,

then $ \vec v$ is the vector written in the ordinary coordinates, like $\left[\begin{array}{cc}
-4 \\
1
\end{array}\right]$:
$$
A\vec x=\vec v
$$
And
$$
\vec x=A^{-1}\vec v
$$

## transformation matrix in different basis

Consider such an example. In the ordinary basis, the $90^\circ$ counterclockwise rotate is 
$$
\left[\begin{array}{cc}
0 & -1 \\
1 & 0
\end{array}
\right]
$$
But in the coordinate system defined by $\vec b_1$ and $\vec b_2$ , the $90^\circ$ counterclockwise rotate should be
$$
\left[\begin{array}{cc}
2 & -1 \\
1 & 1
\end{array}\right]^{-1}
\left[\begin{array}{cc}
0 & -1 \\
1 & 0
\end{array}\right]
\left[\begin{array}{cc}
2 & -1 \\
1 & 1
\end{array}\right] = 
\left[\begin{array}{cc}
\frac{1}{3} & -\frac{2}{3} \\
\frac{5}{3} & -\frac{1}{3}
\end{array}\right]
$$
Therefore, if the $\left[\begin{array}{cc}
1 \\
2
\end{array}\right]$ is a vector in the new coordinate system (using the new basis $\vec b_1$ and $\vec b_2 $), and compute:
$$
\begin{eqnarray}
\left[\begin{array}{cc}
2 & -1 \\
1 & 1
\end{array}\right]^{-1}
\left[\begin{array}{cc}
0 & -1 \\
1 & 0
\end{array}\right]
\left[\begin{array}{cc}
2 & -1 \\
1 & 1
\end{array}\right]
\left[\begin{array}{cc}
1 \\
2
\end{array}\right] = 
\left[\begin{array}{cc}
\frac{1}{3} & -\frac{2}{3} \\
\frac{5}{3} & -\frac{1}{3}
\end{array}\right]
\left[\begin{array}{cc}
1 \\
2
\end{array}\right] = 
\left[\begin{array}{cc}
-1 \\
1
\end{array}\right]
\end{eqnarray}
$$
then the $\left[\begin{array}{cc}
-1 \\
1
\end{array}\right]$ is a vector in the new coordinate system.

### summary

$A^{-1}MA$ suggests a mathematical sort of empathy. And $M$ is a kind of transformation in the ordinary basis.



# Eigenvectors and Eigenvalues

The eigenvectors are the vectors land in the line spanned by the transformation.

The eigenvalues are the scaling ratios associated with the eigenvectors.

The equation:
$$
A\vec v = \lambda \vec v
$$
$A$ is the transformation matrix, $\vec v$ is the eigenvector, and $\lambda$ is the eigenvalue. Take a 3 dimension as an example:
$$
\begin{eqnarray}
A\vec v &=& \lambda \vec v \\
A\vec v &=& \left[\begin{array}{ccc}
\lambda & 0 & 0 \\
0 & \lambda & 0 \\
0 & 0 & \lambda
\end{array}\right] \vec v \\
A\vec v &=& (\lambda I)\vec v \\
(A-\lambda I)\vec v &=& \vec 0 \\
\end{eqnarray}
$$
And it would be something like this:
$$
\left[\begin{array}{ccc}
3-\lambda & 1 & 4 \\
1 & 5-\lambda & 9 \\
2 & 6 & 5-\lambda
\end{array}\right] \vec v = \vec0
$$
we need to find a $\vec v$ which satisfies the equation. zero vector always satisfies.

Only the __squishification__, which is a transformation from high dimension to low dimension, can be associated with a non-zero vectors such that the product of transformation matrix and the vector to be zero vector.

Therefore, we need to find a $\lambda$ such that the determinant of the transformation matrix is 0:
$$
|A-\lambda I| = 0
$$
But not every matrix has eigenvectors and eigenvalue in the real number field, (They will have some meaning in the complex plane.) such as rotation.

+ A single eigenvalue can have more that a line full of eigenvectors, such as scaling transformation.

## eigen-basis

A diagonal matrix can be regarded as a set of eigen-basis (each column is a component of the basis.)
$$
E^{-1}AE = diag 
$$

# vector space

determinant and eigenvectors don't care about the coordinate system.

## Linear concepts

### Additivity

$$
L(\vec v + \vec w) = L(\vec v) + L(\vec w)
$$

### Scaling (first order homogeneous)

$$
L(c \vec v) = cL(\vec v)
$$

Linear transformations preserve the operations of vector addition and scalar multiplication.

__Geometrically__, it means that grid lines remain __parallel__ and __evenly spaced__.

### derivative is linear

$$
\frac{d}{dx}(x^3+x^2)=\frac{d}{dx}(x^3)+\frac{d}{dx}(x^2)
$$

$$
\frac{d}{dx}(4x^3) = 4\frac{d}{dx}(x^3)
$$



For a space with all the polynomials:

The basis functions are
$$
b_0(x) = 1 \\
b_1(x) = x \\
b_2(x) = x^2 \\
\vdots \\
b_n(x) = x^n \\
$$
they are infinitely many, which means that if we treat them as a point in the space, they will have infinite coordinates. For example:
$$
1x^2+3x+5 =\left[\begin{array}{c}
5 \\
3 \\
1 \\
0 \\
0 \\
\vdots
\end{array}\right]
$$
and a polynomial equation will be
$$
a_nx^n+a_{n-1}x^{n-1}+\cdots+a_1x+a_0 =
\left[\begin{array}{c}
a_0 \\
a_1 \\
\cdots \\
a_{n-1} \\
a_{n} \\
0 \\
\vdots
\end{array}\right]
$$
and the derivative operative will be
$$
\frac{d}{dx}=
\left[\begin{array}{cccc}
0 & 1 & 0 & 0 & \cdots \\
0 & 0 & 2 & 0 & \cdots \\
0 & 0 & 0 & 3 & \cdots \\
0 & 0 & 0 & 0 & \cdots \\
\vdots & \vdots & \vdots & \vdots & \vdots
\end{array}\right]
$$
These concepts are correlated:

Linear transformations and Linear operators; dot products and inner products; eigenvectors and eigenfunctions.

## Rules for vectors addition and scaling

### Eight Axioms



# rule for computation

## Gaussian Elimination

## Cramer's rule

### Orthonormal Transformation

If for all $\vec u$ and $\vec v $, 
$$
T(\vec u) \cdot T(\vec v) = \vec u \cdot \vec v
$$
then $T$ is Orthonormal.

### Cramer's rule

$$
\text{Area} = \text{det}(A)x
$$

For example,  consider a linear system of equations:
$$
\left[\begin{array}{cc}
2 & -1 \\
0 & 1
\end{array}\right]
\left[\begin{array}{cc}
x \\
y
\end{array}\right] = 
\left[\begin{array}{cc}
4 \\
2
\end{array}\right]
$$

$$
x = \frac{\left|\begin{array}{cc}
4 & -1 \\
2 & 1
\end{array}\right|}
{\left|\begin{array}{cc}
2 & -1 \\
0 & 1
\end{array}\right|}, ~
y = \frac{\left|\begin{array}{cc}
2 & 4 \\
0 & 2
\end{array}\right|}
{\left|\begin{array}{cc}
2 & -1 \\
0 & 1
\end{array}\right|}
$$

