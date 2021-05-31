---
title: Python Parallel
date: 2020-03-24
tags: 
	- Python
categories: 
	- Computer Science
	- Programming
	- Python
---
# parallel

## joblib

### example for one parameter

__target:__ run `my_fun` multiple times 

```python
from joblib import Parallel, delayed
import time, math

def my_fun(i):
    """ We define a simple function here.
    """
    time.sleep(1)
    return math.sqrt(i**2)
```

__for loop :__

```python
num = 10
start = time.time()
for i in range(num):
    my_fun(i)

end = time.time()

print('{:.4f} s'.format(end-start))
```

__parallel :__

```python
num = 10
start = time.time()
# n_jobs is the number of parallel jobs
Parallel(n_jobs=2)(delayed(my_fun)(i) for i in range(num))
end = time.time()
print('{:.4f} s'.format(end-start))
```

### example for multiple parameters

```python
def my_fun_2p(i, j):
    time.sleep(1)
    return math.sqrt(i**j)

j_num = 3
num = 10
start = time.time()
for i in range(num):
    for j in range(j_num):
        my_fun_2p(i, j)

end = time.time()
print('{:.4f} s'.format(end-start))

30.0778 s

start = time.time()
# n_jobs is the number of parallel jobs
Parallel(n_jobs=2)(delayed(my_fun_2p)(i, j) for i in range(num) for j in range(j_num))
end = time.time()
print('{:.4f} s'.format(end-start))
```

## with as

```python
with Parallel(n_jobs=10, verbose=1) as parallel:
        parallel(delayed(my_fun)(i) for i in range(num))
```

__multiple terms__

```python
With open('1.txt') as f1, open('2.txt') as  f2:
    do something
```

