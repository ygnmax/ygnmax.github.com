---
title: Python Pandas Basics
date: 2019-3-18
update: 2019-8-6
tags: 
	- Python
	- Pandas
	- NYU
	- Bootcamp
categories:
	- Computer Science
	- Programming
	- Python
---
This note contains basic knowledge of pandas including basic syntax and so on. Posted on Aug 6th is a draft.

# 1. Data Type in Pandas

pandas is a newer package built on top of NumPy. Series and DataFrame is the basic data type. Pandas provides efficient access to these sorts of "data munging" tasks that occupy much of a data scientist's time.

## 1.1 Series

### 1.1.1 Series Basics

**Series is a one-dimensional array of indexed data.**

```python
import pandas as pd
data = pd.Series([0.25, 0.5, 0.75, 1.0])
data
```

output:

```
0    0.25
1    0.50
2    0.75
3    1.00
dtype: float64
```



**The values are simply a familiar Numpy array and the index is an array-like of type pd.index.**

```python
data.values
data.index
```

output:

```
array([0.25, 0.5 , 0.75, 1.  ])
RangeIndex(start=0, stop=4, step=1)
```



**we can access the element in the series via square-bracket notation.**

```python
print(data[1])
print(data[1:3])
```

output:

```
0.5
1    0.50
2    0.75
dtype: float64
```



### 1.1.2 Series Index

**Series is similar to one-dimensional NumPy Array.** The essential difference is the presence of the index: while the NumPy Array has an implicitly defined integer index used to access the values, the Pandas Series has an explicitly defined index associated with the values.

we can define the index with any desired type when creating a series

```python
data = pd.Series([0.25, 0.5, 0.75, 1.0], index=["a", "b", "c", "d"])
data
```

output:

```
a    0.25
b    0.50
c    0.75
d    1.00
dtype: float64
```

We can access the element by using index

```python
data["b"]
```

output:

```
0.5
```



**Here, series is a bit like a specialization of a Python dictionary.** It is even more clear and efficient than dictionary in Python.

```python
population_dict = {'California': 38332521,
                  'Florida': 19652860,
                   'Illinois':12882135,
                   'New York': 19651127,
                   'Texas': 26448193
                  }
population = pd.Series(population_dict)
population
```

output:

```
California    38332521
Florida       19652860
Illinois      12882135
New York      19651127
Texas         26448193
dtype: int64
```



**Here, series is a bit like a specialization of a Python dictionary.** It is even more clear and efficient than dictionary in Python.

```python
population['California']
population['California':'Illinois']
```

output:

```
38332521
California  38332521
Florida     19552860
Illinois    12882135
dtype: int64
```



### 1.1.3 Constructing Series

We can construct a Series from scratch: `pd.Series(data, index = index)`, where Index is an optional argument. data can be one of many entities.

The 'data' can be a list or Numpy array, can be a scalar, can be a dictionary

```python
pd.Series(5, index = [100, 200, 300])
pd.Series({2:'a', 1:'b', 3:'c'})
pd.Series({2:'a', 1:'b', 3:'c'}, index = [3, 2])
```

output:

```
100    5
200    5
300    5
dtype: int64
2    a
1    b
3    c
dtype: object
3    c
2    a
dtype: object
```

In this case, the Series is populated only wit the explicitly identified keys.



## 1.2 DataFrame

### 1.2.1 DataFrame Basics

Dataframe can be thought of either as a generalization of a NumPy array, or as a specialization of a Python dictionary. It is an analog of a two dimensional array with flexible row indices and column names.

```python
area_dict = {'California': 423967,
                  'Florida': 170312 ,
                   'Illinois':149995,
                   'New York': 141297,
                   'Texas': 696562
                  }
area = pd.Series(area_dict)
area
```

output:

```
California    423967
Florida       170312
Illinois      149995
New York      141297
Texas         696562
dtype: int64
```

we can use a dictionary to construct a single two-dimensional object:

```python
states = pd.DataFrame({'population': population, 'area': area})
states
```

output:

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>population</th>
      <th>area</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>California</th>
      <td>38332521</td>
      <td>423967</td>
    </tr>
    <tr>
      <th>Florida</th>
      <td>19652860</td>
      <td>170312</td>
    </tr>
    <tr>
      <th>Illinois</th>
      <td>12882135</td>
      <td>149995</td>
    </tr>
    <tr>
      <th>New York</th>
      <td>19651127</td>
      <td>141297</td>
    </tr>
    <tr>
      <th>Texas</th>
      <td>26448193</td>
      <td>696562</td>
    </tr>
  </tbody>
</table>


**DataFrame also has index attribute that gives access to the index lables:**

```python
states.index
states.columns
```

output:


```
Index([California, Florida, Illinois, New York,Texas], dtype=object)
Index([area, population], dtype=object)
```



**A Pandas Dataframe can be constructed in variety of ways**

**a. from a single Series object:**

```python
pd.DataFrame(population, columns=['popluation'])
```

output:

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>popluation</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>California</th>
      <td>38332521</td>
    </tr>
    <tr>
      <th>Florida</th>
      <td>19652860</td>
    </tr>
    <tr>
      <th>Illinois</th>
      <td>12882135</td>
    </tr>
    <tr>
      <th>New York</th>
      <td>19651127</td>
    </tr>
    <tr>
      <th>Texas</th>
      <td>26448193</td>
    </tr>
  </tbody>
</table>



**b. from a list of dicts:**

```python
data = [{'a':i, 'b':2 * i}
       for i in range(3)]
pd.DataFrame(data)
```

output:

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

```
.dataframe tbody tr th {
    vertical-align: top;
}

.dataframe thead th {
    text-align: right;
}
```

</style>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>b</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>4</td>
    </tr>
  </tbody>
</table>

</div>

**Even if some keys in the dictionary are missing, Pandas will fill them in with NaN (i.e., \not a number") values:**

```python
pd.DataFrame([{'a':1, 'b': 2},{'b':3, 'c':4}])
```

output:

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>2</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>NaN</td>
      <td>3</td>
      <td>4.0</td>
    </tr>
  </tbody>
</table>


**c. from a dictionary of Series objects** 

```python
pd.DataFrame({population: population, area: area})
```



**d. from a two-dimensional Numpy array**

```python
pd.DataFrame(np.random.rand(3, 2),
            columns=['foo', 'bar'],
            index=['a', 'b', 'c'])
```

output:

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>foo</th>
      <th>bar</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>0.010853</td>
      <td>0.798349</td>
    </tr>
    <tr>
      <th>b</th>
      <td>0.970245</td>
      <td>0.074233</td>
    </tr>
    <tr>
      <th>c</th>
      <td>0.429177</td>
      <td>0.251008</td>
    </tr>
  </tbody>
</table>



**e. from a numpy structured array**

```python
A = np.zeros(3, dtype = [('A', 'i8'), ('B', 'f8')])
```



### 1.2.2 Pandas Index Object

Here is an example:

```python
ind = pd.Index([2, 3, 5, 7, 11])
ind
```

output:

```
Int64Index([2, 3, 5, 7, 11], dtype='int64')
```

**a. we can use standard Python indexing notation to retrieve values or slices:**

```python
print(ind[1])
print(ind[::2])
print(ind.size,ind.shape, ind.ndim, ind.dtype)
```

```
3
Int64Index([2, 5, 11], dtype='int64')
5 (5,) 1 int64
```

**b. index objects and numpy arrays are immutable, they cannot be modified**

```python
ind[1] = 0
```

output:

```
---------------------------------------------------------------------------

TypeError                                 Traceback (most recent call last)

<ipython-input-66-906a9fa1424c> in <module>
----> 1 ind[1] = 0
```

```
D:\Anaconda\lib\site-packages\pandas\core\indexes\base.py in __setitem__(self, key, value)
   2063 
   2064     def __setitem__(self, key, value):
-> 2065         raise TypeError("Index does not support mutable operations")
   2066 
   2067     def __getitem__(self, key):
```

```
TypeError: Index does not support mutable operations
```

**This immutability makes it safer** to share indices between multiple DataFrames and arrays, without the potential for side effects from inadvertent index modification.



**c. set arithmetic**

```python
indA = pd.Index([1, 3, 5, 7, 9])
indB = pd.Index([2, 3, 5, 7, 11])
indA & indB # Intersection
indA | indB # Union
indA ^ indB # symmetric difference
```

output:

```
Int64Index([3, 5, 7], dtype='int64')
Int64Index([1, 2, 3, 5, 7, 9, 11], dtype='int64')
Int64Index([1, 2, 9, 11], dtype='int64')
```



## 1.3 Data Selection and Operation

- indexing (e.g., arr[2; 1])
- slicing (e.g., arr[:; 1 : 5])
- masking (e.g., arr[arr > 0])
- fancy indexing (e.g., arr[0; [1; 5]])
- combinations thereof (e.g., arr[:; [1; 5]])

### 1.3.1 Series Operation

```python
import pandas as pd
data = pd.Series([0.25, 0.5, 0.75, 1.0])
data.Index = ['a', 'b', 'c', 'd']
data
```

output:

```
0    0.25
1    0.50
2    0.75
3    1.00
dtype: float64
```



**Index, key and values:**

```python
'a' in data
data.keys()
list(data.items())
```

output:

```
True
Index(['a', 'b', 'c', 'd'], dtype='object')
[]
```



**We can modify the values or extend a Series by assigning to a new index value.**

```python
data['e'] = 1.25
```

output:

```
a 0.25
b 0.50
c 0.75
d 1.00
e 1.25
dtype: float64
```



**Examples of slices, masking, fancy indexing:**

```python
# slicing by explicit index
data['a':'c']

# slicing by implicit integer index
data[0:2]

# masking
data[(data > 0.3)&(data<0.8)]

# fancy indexing
data[['a', 'e']]
```

output:

```
a 0.25
b 0.50
c 0.75
dtype: float64

a 0.25
b 0.50
dtype: float64

b    0.50
c    0.75
dtype: float64

a 0.25
e 1.25
dtype: float64
```

Notice that when slicing with an explicit index (i.e.,`data['a': 'c']`), the nal index is included in the slice, while when slicing with an implicit index (i.e., `data[0 : 2]`), the final index is excluded from the slice.



### 1.3.2 Indexers: loc, iloc, and ix

The slicing and indexing conventions can be a source of
confusion in term of explicit and implicit form:

```python
data= pd.Series(['a', 'b', 'c'], index=[1, 3, 5])
print(data)

# index changed 
print(data[1])

# cannot use slicing
print(data[1:3])
```

output:

```
1    a
3    b
5    c
dtype: object
a
3    b
5    c
dtype: object
```

**1. `loc`**

the `loc` attribute allows indexing and slicing that always references the explicit index:

```python
print(data.loc[1])
print(data.loc[1:3])
```

output:

```
a
1    a
3    b
dtype: object
```

**2. `iloc`**

The `iloc` attribute allows indexing and slicing that always references the implicit Python-style index:

```python
data.iloc[1]
data.iloc[1:3]
```

output:

```
'b'
3 b
5 c
dtype: object
```

**3. `ix`**

`ix` , is a hybrid of the two, and for Series objects is equivalent to standard [] - based indexing, the purpose of which will become more apparent in the context of Dataframe object.

One guiding principle of Python code is that **"explicit is better than implicit"**

### 1.3.3 DataFrame Operation









