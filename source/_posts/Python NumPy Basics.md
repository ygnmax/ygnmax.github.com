---
title: Python NumPy Basics
date: 2019-8-5
update: 2019-8-6
tags: 
	- Python
	- Numpy
	- NYU
	- Bootcamp

categories: 
	- Computer Science
	- Programming
	- Python
---

This is a class note of NYU MFE Bootcamp, including contains basic knowledge of Python NumPy syntax and techniques. Understanding Data Types in Python to part of Operations of NumPy arrays was on Aug 5th; The rest was on Aug 6th.

# Understanding Data Types in Python

## Statically-typing & Dynamic typing

A statically-typed language like C or Java requires each variable to be explicitly declared, while Python skips this specification.

```python
result = 0
for i in range(100):
    result += i
print(result)
```

This means we can assign any kind of data to any variable.

## Behind the python: flexibility

The standard Python implementation is written in C, which means every Python object is simply a cleverly-disguised C structure, not only its value, but other information as well.

### Integer

A single integer in Python 3.4 contains four pieces.

+ `ob_refcnt`
+ `ob_type`
+ `ob_size`
+ `ob_digit`

A python integer is a pointer to a position in memory containing all the Python object information, including the bytes that contain the integer value.

### List

List is almost the most flexibility type in Python.

```python
L = list(range(10))
L
type(L[0])
```

output:


    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    int



**Change it to a list of strings:**


```python
L2 = [str(c) for c in L]
L2
type(L2[0])
```

output:


    ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9']
    str



Or we can create heterogeneous lists:


```python
L3 = [True, "2", 3.0, 4]
[type(item) for item in L3]
```

output:


    [bool, str, float, int]



Flexibility comes with a cost (**loss of storage and efficiency**). In the special case that all variables are of the same type, much of this flexibility is redundant. Then comes with fixed-type NumPy-style array.

### Array

The built in array module can be used to create dense arrays of a uniform type:


```python
import array
L = list(range(10))
A = array.array('i', L)
A
```

output:


    array('i', [0, 1, 2, 3, 4, 5, 6, 7, 8, 9])



However, the NumPy Array is more efficient than array because of the operations on data.



# Overlook of NumPy arrays

## Basic NumPy array syntax:

**basic syntax:**


```python
import numpy as np
np.array([1,4,2,5,3])
```

output:


    array([1, 4, 2, 5, 3])



**The type of elements in array should, but does not have to, be the same.  If the types do not match, Numpy will upcast if possible.**


```python
np.array([3.14, 4, 2, 3])
```

output:


    array([3.14, 4.  , 2.  , 3.  ])



Here, integers are up-cast to floating point. **And we can use dtype keyword to set the data type:**


```python
np.array([1, 2, 3, 4], dtype='float32')
```

output:


    array([1., 2., 3., 4.], dtype=float32)



## NumPy array as matrix

**Numpy arrays can explicity be muti-dimensional, using a list of lists:**


```python
# nested lists result in multi-dimensional arrays
np.array([range(i, i+3) for i in [2, 4, 6]])
```

output:


    array([[2, 3, 4],
           [4, 5, 6],
           [6, 7, 8]])

for better understanding, we can run a 2*2 array:


```python
np.array([range(i, i+2) for i in [2, 4]])
```

output


    array([[2, 3],
           [4, 5]])

or a 3*10 array:


```python
np.array([range(i, i+10) for i in [2, 4, 6]])
```

output:


    array([[ 2,  3,  4,  5,  6,  7,  8,  9, 10, 11],
           [ 4,  5,  6,  7,  8,  9, 10, 11, 12, 13],
           [ 6,  7,  8,  9, 10, 11, 12, 13, 14, 15]])



**It is more efficient to create arrays from scratch using routines built into Numpy:**

**zero array** with 10 integer:


```python
np.zeros(10, dtype=int)
```

output:


    array([0, 0, 0, 0, 0, 0, 0, 0, 0, 0])



**one array:**


```python
np.ones((3,5), dtype=float)
```

output:


    array([[1., 1., 1., 1., 1.],
           [1., 1., 1., 1., 1.],
           [1., 1., 1., 1., 1.]])



**An array with some identical elements:**


```python
np.full((3, 5), 3.14)
```

output:


    array([[3.14, 3.14, 3.14, 3.14, 3.14],
           [3.14, 3.14, 3.14, 3.14, 3.14],
           [3.14, 3.14, 3.14, 3.14, 3.14]])



**A linear sequence**


```python
# create an array filled with a linear sequence
# starting at 0, this is similar to the built-in range() function
np.arange(0, 20, 2)
```

output:


    array([ 0,  2,  4,  6,  8, 10, 12, 14, 16, 18])



**linspace**


```python
# create an array of five values evenly spaced
# between 0 and 1
np.linspace(0, 1, 5)
```

output:


    array([0.  , 0.25, 0.5 , 0.75, 1.  ])



**uniformly distributed random value**


```python
# create a 3*e arrayof uniformly distributed random values between 0 and 1
np.random.random((3, 3))
```

output:


    array([[0.57226098, 0.56849713, 0.63410602],
           [0.88335333, 0.46056684, 0.95494879],
           [0.22305721, 0.18478839, 0.78352821]])



**normal distributed random value**


```python
np.random.normal(0, 1, (3, 3))
```

output:


    array([[ 1.05100904,  1.71407429,  0.75356105],
           [-0.61885082,  0.43198626,  0.63819954],
           [-0.53911965,  1.07533192, -0.27227068]])



**random value**


```python
# create a 3*3 array of random integers in the interval [0, 10]
np.random.randint(0, 10, (3, 3))
```

output:


    array([[0, 7, 1],
           [2, 7, 6],
           [7, 8, 5]])



**create identity matrix**


```python
# create a 3*3 identity matrix
np.eye(3)
```

output:


    array([[1., 0., 0.],
           [0., 1., 0.],
           [0., 0., 1.]])



**uninitialized array**


```python
# create an uninitialized array of three integers
# the values will be whatever happens to 
# already exist at that memory location
np.empty(3)
```

output:


    array([1., 1., 1.])



**Standard Data Types**

numpy is also built in C, the data type  can be specified using a string:


```python
np.zeros(10, dtype = 'int16')
np.zeros(10, dtype = np.int16) #same
```

output


    array([0, 0, 0, 0, 0, 0, 0, 0, 0, 0], dtype=int16)



# Operations of NumPy arrays

+ attributes of arrays
+ indexing of arrays
+ slicing of arrays
+ reshaping of arrays
+ joining and splitting of arrays

## Attributes of arrays

**determining the size, shape, memory consumption, and data types of arrays**

We can use random number generator, which we will seed with a set value in order to ensure that the same random arrays are generated each time this code is run:


```python
np.random.seed(0)# seed for reproducibility
x1 = np.random.randint(10, size=6)
x2 = np.random.randint(10, size=(3, 4))
x3 = np.random.randint(10, size=(3, 4, 5))
print(x1)
print(x2)
print(x3)
```

output:

    [5 0 3 3 7 9]
    [[3 5 2 4]
     [7 6 8 8]
     [1 6 7 7]]
    ([[[8, 1, 5, 9, 8],
    [9, 4, 3, 0, 3],
    [5, 0, 2, 3, 8],
    [1, 3, 3, 3, 7]],
    
    [[0, 1, 9, 9, 0],
    [4, 7, 3, 2, 7],
    [2, 0, 0, 4, 5],
    [5, 6, 8, 4, 1]],
    
    [[4, 9, 8, 1, 1],
    [7, 9, 9, 3, 6],
    [7, 2, 0, 3, 5],
    [9, 4, 4, 6, 4]]])



**each array has attributes ndim, shape and size:**


```python
print("x3 ndim: ", x3.ndim)
print("x3 shape: ", x3.shape)
print("x3 size: ", x3.size)
```

output:

    x3 ndim:  3
    x3 shape:  (3, 4, 5)
    x3 size:  60



**we can check the type of x3**

```python
print("dtype:", x3.dtype)
```

    dtype: int32



**`itemsize` is another attribute, which list the size in bytes of each array element, and `nbytes` list the total size of the array:**


```python
print("itemsize: ", x3.itemsize, "bytes")
```

    itemsize:  4

In general, we expect that **nbytes is equal to itemsize times size**.



## Array Indexing

**Getting and setting the value of individual array elements**


```python
print(x1[0])
print(x1[4])
```

output:

    5
    7



**use negative indices:**


```python
print(x1[-1])
print(x1[-2])
```

ouptut:

    9
    7



**items can be accessed using a comma-separated tuple of indices:**

```python
print(x2)
print(x2[2, 0])
print(x2[2, -1])
```

output:

    [[3 5 2 4]
     [7 6 8 8]
     [1 6 7 7]]
    1
    7



**Values can be modified using any of the above index notation:**

```python
print(x2)
x2[0, 0] = 12
print(x2)
```

output:

    [[3 5 2 4]
     [7 6 8 8]
     [1 6 7 7]]
    [[12  5  2  4]
     [ 7  6  8  8]
     [ 1  6  7  7]]



Numpy arrays have a fixed type. The different type will be **silently truncated automatically**


```python
x1[0] = 3.14159 # this will be truncated!
x1
```

output:


    array([3, 0, 3, 3, 7, 9])



## Array Slicing

**Getting and setting smaller subarrays within a larger array**

The standard Python list slicing is:

​	`x[start:stop:step]`

The default to the values start = 0, stop = size of dimension, step = 1


```python
x = np.arange(10)
x
```

output:


    array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])

### One-dimension

**This is operation of one-dimensional subarrays**


```python
x[:5] # first five elements
x[5:]
x[4:7] # middle sub-array
x[::2] # every other element
x[1::2] # every other element, starting at index1
x[::-1] # reversed
x[5::-2] # reversed every other from index 5
```

output:


    array([0, 1, 2, 3, 4])
    array([5, 6, 7, 8, 9])
    array([4, 5, 6])
    array([0, 2, 4, 6, 8])
    array([1, 3, 5, 7, 9])
    array([9, 8, 7, 6, 5, 4, 3, 2, 1, 0])
    array([5, 3, 1])

### Multi-dimension


```python
x2
```

output:


    array([[12,  5,  2,  4],
           [ 7,  6,  8,  8],
           [ 1,  6,  7,  7]])

**Some operations of multi-dimensional subarrays**


```python
x2[:2, :3] # first two rows, three columns
x2[:3, ::2] #all rows, every other column
x2[::-1, ::-1] # subarray dimensions can even be reversed together
```

output:


    array([[12,  5,  2],
           [ 7,  6,  8]])
    array([[12,  2],
           [ 7,  8],
           [ 1,  7]])
    array([[ 7,  7,  6,  1],
           [ 8,  8,  6,  7],
           [ 4,  2,  5, 12]])

**Accessing of single rows or columns of an array can be done by combining indexing and slicing, using an empty slice marked by a single colon (:):**


```python
print(x2[:,0]) #first column of x2
print(x2[0,:]) #first row of x2

# In the case of row access, the empty slice can be omitted for a more compact syntax

print(x2[0]) #equivalent
```

output:

    [12  7  1]
    [12  5  2  4]
    [12  5  2  4]

### Copy & No-Copy Subarrays

**NumPy array slice return views rather than copies of the array data. However, Python list slicing will be copies.**

+ Changed Example

  Extract a 2*2 subarray from this:


  ```python
  x2_sub = x2[:2, :2]
  print(x2_sub)
  ```

      [[12  5]
       [ 7  6]]

  **The original array is changed:**

  ```python
  x2_sub[0, 0] = 99
  print(x2_sub)
  print(x2)
  ```

  output:

      [[99  5]
       [ 7  6]]
      [[99  5  2  4]
       [ 7  6  8  8]
       [ 1  6  7  7]]

  it is a useful property, we can access and process pieces of these datasets without the need to copy the underlying data buffer.

+ Unchanged Example

  we can also create a explicitly copy the data within an array or a subarray.


  ```python
  x2_sub_copy = x2[:2,:2].copy()
  print(x2_sub_copy)
  print(x2)
  ```

  output:

      [[99  5]
       [ 7  6]]
      [[99  5  2  4]
       [ 7  6  8  8]
       [ 1  6  7  7]]

  If we modify this subarray, **the original array is not touched:**

  ```python
  x2_sub_copy[0,0] = 42
  print(x2_sub_copy)
  print(x2)
  ```

  output:

      [[42  5]
       [ 7  6]]
      [[99  5  2  4]
       [ 7  6  8  8]
       [ 1  6  7  7]]

  


## Array Reshaping

**Changing the shape of a given array**


```python
# put number 1-9 in a 3*3 grid:
grid = np.arange(1,10).reshape((3,3))
print(grid)
```

output:

    [[1 2 3]
     [4 5 6]
     [7 8 9]]

The size of the initial array must match the size of the reshaped array. The reshape method will use a no-copy view of the initial array.

We can use `newaxis` method to realize the reshape effect.

```python
x = np.array([1,2,3])

x.reshape((1,3))
x[np.newaxis, :]

x.reshape((3,1))
x[:, np.newaxis]
```

output:


    array([[1, 2, 3]])
    array([[1, 2, 3]])
    array([[1],
           [2],
           [3]])
    array([[1],
           [2],
           [3]])



## Array concatenation and splitting

**Combining multiple arrays into one, and splitting one array into many**

### Concatenation

**`concatenation`: combine multiple arrays into one**


```python
x = np.array([1, 2, 3])
y = np.array([3, 2, 1])
np.concatenate([x, y])
```

output:


    array([1, 2, 3, 3, 2, 1])

In two-dimensional situation, default is zero-indexed.

```python
grid = np.array([[1, 2, 3],
               [4, 5, 6]])
# concatenate along the first axis
np.concatenate([grid, grid])
```

output:


    array([[1, 2, 3],
           [4, 5, 6],
           [1, 2, 3],
           [4, 5, 6]])

We can concatenate along the second axis (zero-indexed).


```python
# zero-indexed
np.concatenate([grid, grid], axis=1) 
```

output:


    array([[1, 2, 3, 1, 2, 3],
           [4, 5, 6, 4, 5, 6]])



**`vstack`:  vertically stack the arrays**


```python
x = np.array([1,2,3])
grid = np.array([[9, 8, 7],
                [6, 5, 4]])
np.vstack([x, grid])
```

output:


    array([[1, 2, 3],
           [9, 8, 7],
           [6, 5, 4]])

**`hstack`: horizontally stack the arrays**


```python
# horizontal
y = np.array([[99],
             [99]])
np.hstack([grid, y])
```

output:


    array([[ 9,  8,  7, 99],
           [ 6,  5,  4, 99]])



### Spliting

**`split`: opposite of concatenation.**


```python
x = [1, 2, 3, 99, 99, 3, 2, 1]
x1, x2, x3 = np.split(x, [3, 5])
print(x1, x2, x3)
```

output:

    [1 2 3] [99 99] [3 2 1]

Notice that *N* split-points, leads to *N+1* subarrays.



`np.hsplit` and `np.vsplit` are similar. In multi-dimensional situation:

```python
grid = np.arange(16).reshape((4, 4))
grid
```

output:


    array([[ 0,  1,  2,  3],
           [ 4,  5,  6,  7],
           [ 8,  9, 10, 11],
           [12, 13, 14, 15]])



`np.vsplit` and `np.hsplit`


```python
upper, lower = np.vsplit(grid, [2])
print(upper)
print(lower)

left, right = np.hsplit(grid, [2])
print(left)
print(right)
```

output:

    [[0 1 2 3]
     [4 5 6 7]]
    [[ 8  9 10 11]
     [12 13 14 15]]
    [[ 0  1]
     [ 4  5]
     [ 8  9]
     [12 13]]
    [[ 2  3]
     [ 6  7]
     [10 11]
     [14 15]]



# Computation and Functions in NumPy

## The speed of computation on Numpy

Computation can be very fast or very slow. The key to making it fast is to use vectorized operations, generally implemented through universal functions(ufuncs).

### The Slowness of Loops


```python
# slowness of loops
import numpy as np
np.random.seed(0)

def compute_reciprocals(values):
    output = np.empty(len(values))
    for i in range(len(values)):
        output[i] = 1.0 / values[i]
    return output

values = np.random.randint(1, 10, size = 5)
compute_reciprocals(values)
```

output:


    array([0.16666667, 1.        , 0.25      , 0.25      , 0.125     ])

If we use  this code for a large input, the operation is very slow.


```python
# IPython's %timeit
big_array = np.random.randint(1, 100. size=1000000)
%timeit compute_reciprocals(big_array)
```

It turns out that the bottleneck here is not the operations themselves, but the type-checking and function dispatches that CPython must do at each cycle of the loop.

### Vectorized Operation

However, Numpy provides a convenient interface to compile routine, which is named as a vectorized operation.


```python
print(compute_reciprocals(values))
print(1.0 / values)
%timeit (1.0 / big_array)
```

**Vectorized operations in Numpy are implemented via ufuncs, whose main purpose is to quickly execute repeated operations or values in Numpy arrays.**


```python
np.arange(5) / np.arange(1,6)
```

output:


    array([0.        , 0.5       , 0.66666667, 0.75      , 0.8       ])

**Here is the multi-dimensional situation:**


```python
x = np.arange(9).reshape((3,3))
2 ** x
```

output:


    array([[  1,   2,   4],
           [  8,  16,  32],
           [ 64, 128, 256]], dtype=int32)

We can use these ufuncs to realize various purpose.

## Computation via NumPy UFuncs

Ufuncs exist in two flavors:

+ unary ufuncs, which operate on a single input
+ binary ufuncs, which operate on two inputs

We can use uFuncs to achieve arithmetic purpose.

### Array arithmetic

**The basic arithmetic operations**

```python
import numpy as np
x=np.arange(4)
print("x     =", x)
print("x + 5 =", x + 5)
print("x - 5 =", x - 5)
print("x + 5 =", x + 5)
print("x + 5 =", x + 5)
print("x + 5 =", x + 5)
print("-x    =", -x) # negation
print("x ** 2 =", x ** 2) # exponentiation
print("x % 2 =", x & 2) # modulus
```

output:

```
x     = [0 1 2 3]
x + 5 = [5 6 7 8]
x - 5 = [-5 -4 -3 -2]
x + 5 = [5 6 7 8]
x + 5 = [5 6 7 8]
x + 5 = [5 6 7 8]
-x    = [ 0 -1 -2 -3]
x ** 2 = [0 1 4 9]
x % 2 = [0 0 2 2]
```

We can also combine them together. these arithmetic are simply wrappers specific functions built into NumPy.

```python
print(-(0.5* + 1)**2)
print(np.add(x, 2))
```

output:

```
-0.25
[2 3 4 5]
```

Other arithmetic operators and functions include:

```python
abx(x)
np.exp(x)
np.log(x)
np.sin(x)
```



**Specialized functions used in statistics exist in scipy**

```python
from scipy import special
x = [1, 5, 10]
print("gamma(x)      =", special.gamma(x))
print("ln|gamma(x)|  =", special.gammaln(x))
print("beta(x, 2)    =", special.beta(x, 2))
```

output:

```
gamma(x)      = [1.0000e+00 2.4000e+01 3.6288e+05]
ln|gamma(x)|  = [ 0.          3.17805383 12.80182748]
beta(x, 2)    = [0.5        0.03333333 0.00909091]
```



**To summarize the typical values in a dataset, we can use aggregates function.** NumPy's aggregate function version is computed much more quickly.

```python
L = np.random.random(100)
print(sum(L))
print(np.sum(L))
```

```
47.620210778723894
47.620210778723894
```

Timing the different functions:

```python
big_array = np.random.rand(1000000)
%timeit sum(big_array)
%timeit np.sum(big_array)
```

ouptut:

```
113 ms ± 7.37 ms per loop (mean ± std. dev. of 7 runs, 10 loops each)
1.28 ms ± 69.8 µs per loop (mean ± std. dev. of 7 runs, 1000 loops each)
```



**For min, max, sum, and several other NumPy aggregates, a shorter syntax is to use methods of the array object itself:**

```python
min(big_array), max(big_array)
np.min(big_array), np.max(big_array)
print(big_array.min(), big_array.max(), big_array.sum())
```

output:

```
(7.476608001599772e-07, 0.9999999017465359)
(7.476608001599772e-07, 0.9999999017465359)
7.476608001599772e-07 0.9999999017465359 499703.64780246833
```



**For multi-dimensional aggregates, there are three situation: the entire array, the row and the column.**

```python
M = np.random.random((3, 4))
print(M)
print(M.sum())
```

output:

```
[[0.31678953 0.12015542 0.47115746 0.91046151]
 [0.66547603 0.36825635 0.79325825 0.2072341 ]
 [0.73285524 0.39698562 0.5593977  0.514694  ]]
6.0567212054611375
```

To calculate aggregate from an axis.

```python
print(M.min(axis=0))
print(M.max(axis=1))
```

output:

```
[0.31678953 0.12015542 0.47115746 0.2072341 ]
[0.91046151 0.79325825 0.73285524]
```

**The axis keyword specifies the dimension of the array will be collapsed, rather than the dimension that will be returned.**

additionally, most aggregates have a NaN-safe counterpart that computes the result while ignoring values, for example, `np.sum` and `np.nansum`.



## Example: What is Average Height of US Presidents?



```python
import numpy as np
import pandas as pd
data = pd.read_csv('E:/NYU/BootCamp/Bootcamp Onsite/Afternoon/python/president_heights.csv')
# data.head()
heights = np.array(data['height(cm)'])
print(heights)
print("Mean height: ", heights.mean())
print("Standard deviation:", heights.std())
print("Minimum height: ", heights.min())
print("Maximum height: ", heights.max())
print("25th percentile: ", np.percentile(heights, 25))
print("Median: ", np.median(heights))
print("75th percentile: ", np.percentile(heights, 75))
```

output:

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>order</th>
      <th>name</th>
      <th>height(cm)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>George Washington</td>
      <td>189</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>John Adams</td>
      <td>170</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Thomas Jefferson</td>
      <td>189</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>James Madison</td>
      <td>163</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>James Monroe</td>
      <td>183</td>
    </tr>
  </tbody>
</table>

```
[189 170 189 163 183 171 185 168 173 183 173 173 175 178 183 193 178 173
 174 183 183 168 170 178 182 180 183 178 182 188 175 179 183 193 182 183
 177 185 188 188 182 185]
```



```python
%matplotlib inline
import matplotlib.pyplot as plt
import seaborn; seaborn.set() # set  plot style

plt.hist(heights)
plt.title('Height Distributtion of US Presidents')
plt.xlabel('height (cm)')
plt.ylabel('number')
```

output:

```
Text(0, 0.5, 'number')
```

![png](E:/Blog/source/_posts/output_3_1.png)