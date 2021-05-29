---
title: Data Structure Basics
date: 2019-3-10
update: 2019-3-11
tags:
	- Data Structure
	- MOOC
categories:
	- Computer Science
	- Data Structure & Algorithm
	- Data Structure 
---

This note contains basic knowledge of data structure and algorithm, including  big-O.

# Computing Model



# Complexity

## Complexity



# Notations

## Big-$\Omega$



## Big-$\theta$



## Big-O



### O(c)



### O($log^n$)



### O($n^c$)

tractable



### O($2^n$)

intractable

+ example: 2-Subset Problem
  + 2-Subset is NP-complete



# Algorithm Analysis

## Objective

+ Validity
+ Complexity

## Method

### Iteration: summation of series

+ Arithmetic Series

$$
T(n) = 1 + 2 + ... + n = \frac{n(n+1)}{2} = O(n^2)
$$

+ *Power of natural number* Series

$$
\sum_{k=0}^{n}k^d \approx \int_{0}^{n}x^{d+1}dx=\frac{1}{d+1}x^{d+1}\bigg|_{0}^{n}=\frac{n^{d+1}}{d+1}=O(n^{d+1})
$$

$$
\begin{align*}
T_2(n) &= 1^2+2^2+..+n^2=\frac{n(n+1)(2n+1)}{6}=O(n^3) \\
T_3(n) &= 1^3+2^3+..+n^3=\frac{n^2(n+1)^2}{4}=O(n^4) \\
T_4(n) &= 1^4+2^4+..+n^4=\frac{n(n+1)(2n+1)(3n^2+3n-1)}{30}=O(n^5) \\
\end{align*}
$$

+ Geometric series

$$
T_p(n)=p^0+p^1+...p^n=\frac{p^{n+1}-1}{p-1}=O(a^n)
$$

$$
1 + 2 + 4 + ... + 2^n = 2^{n+1}-1=O(2^{n+1})=O(2^n)
$$

+ Convergent series

$$
1+\frac{1}{2^2}+...+\frac{1}{n^2}<1+\frac{1}{2^2}+...+\frac{1}{n^2}+...=\frac{\pi^2}{6}=O(1)
$$

​	storage unit can be *fraction*:
$$
(1-\lambda)[1+2\lambda+3\lambda^2+4\lambda^3+...]=\frac{1}{1-\lambda}=O(1) ~ , ~ 0<\lambda<1
$$

+ Divergent series

$$
h(n)=1+\frac{1}{2}+\frac{1}{3}+...+\frac{1}{n}=\theta(logn)
$$

$$
\log1+\log2+\log3+...+\log n=\log(n!)=\theta(n\log n)
$$

example1:

```c++
for (int i = 0; i < n; i++)
for (int j = 0; j < n; j++)
    O1Oeration(i, j);    
```

$$ \sum\limits_{i=0}^{n-1}n=n+n+...n=n*n=O(n^2) $$

example2:

```c++
for (int i = 0; i < n; i++)
for (int j = 0; j < i; j++)
    O1Oeration(i, j);    
```

$$ \sum\limits_{i=0}^{n-1}i=0+1+...n-1=\frac{n(n-1)}{2}=O(n^2) $$

example3:

```c++
for (int i = 0; i < n; i++)
for (int j = 0; j < i; j += 2013)
    O1Oeration(i, j);
```

$$ O(n^2) $$

example4:

```c++
for (int i = 0; i < n; i <<= 1)
for (int j = 0; j < i; j++)
    O1Oeration(i, j);
```

$$
1+2+4+...+2^{\lfloor\log_2(n-1)\rfloor}
=\sum_{k=0}^{\lfloor\log_2(n-1)\rfloor}2^k
=2^{\lceil\log_{2}n\rceil}-1
=O(n)
$$

example5:

```c++
for (int i = 0; i <= n; i++)
for (int j = 1; j < i; j+=j)
    O1Oeration(i, j);
```

$$
\begin{align*}
\sum_{k=0}^{n}\lceil\log_{2}i\rceil
&=O(n\log n),~(i=0,1,2,3\sim4, 5\sim8, 9\sim16,...) \\
&= 0+0+1+2*2+3*4+4*8+... \\
&= \sum_{0}^{\log n}(k*2^{k-1})\\
&= O(\log n*2^{\log n})
\end{align*}
$$



### Recursion: recursive function



### Inference