---
title: Python Manipulating File
date: 2020-03-24
tags: 
	- Python
categories: 
	- Computer Science
	- Programming
	- Python
---
# Path

## OS

```python
os.path.isfile(<path>)
"""
Return True if path is an existing regular file. This follows symbolic links, so both islink() and isfile() can be true for the same path.
"""

os.path.exists(<path>)
"""
Return True if there exist a files in the path 
"""

os.path.makedirs(<path>)
```



## iterate files in a folder

```python
for root, dirs, files in os.walk(file_location):
    for filename in files:
        if filename.endswith('.csv'):
            file_path = os.path.join()
			file_list.append(file_path)
            file_

# iterate file name and append them    
all_data = pd.DataFrame()
for fp in sorted(file_list[:300]):
    print(fp)
    
    df = pd.read_csv(fp, skiprows = 1, encoding = 'gbk')
    all_data = all_data.append(df, ignore_index = True)
print(all_data)

all_data.sort_values(by = ['trddt', 'stkid'], inplace = True)
all_data.to_csv('all_data.csv', index = False, encoding = 'gbk')
```



# Search files

## glob

### search files in a folder

```python
import glob

glob.glob(pathname, *, recursive=False)
glob.iglob(pathname, *, recursive=False)
```

__example__: list all the python scripts in the folder

```python
cd new #the path
print(glob.glob(r"*.py"))
## output: a list of file names
['Bag.py', 'helpers.py', 'KMeans.py']
## Or all the files in a specific folder
print(glob.glob(r"E:\pic**.jpg"))


cd new #the path
print(glob.iglob(r"*.py"))
## output: an iterator to generate file names
<generator object _iglob at 0x7f45746ec4d0>

for py in glob.iglob(r"*.py"):
    print(py)
## output: 
vocab_unnormalized.png
figure_1.png
vocab.png
```

### search files and ignore the wild card

```python
import glob

glob.escape(pathname)
```

