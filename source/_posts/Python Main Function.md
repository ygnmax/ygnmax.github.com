---
title: Python Main Function
date: 2020-03-24
tags: 
	- Python
categories: 
	- Computer Science
	- Programming
	- Python
---
# main function

## \_\_name\_\_

```python
pi = 3.14
def main():
    print("pi: ", pi)
if __name__ == '__main__':
    main()
    
 
```

here, \_\_name\_\_ is a built-in variable, referring to the name of present module, as well as the structure of a package. `__name__ == '__main__':` defines the entry of the python script.

+ When the script is run as a script, then  `__name__=__main__`
+ When the script is run as a module/package, then  `__name__= <the name of package>`

## \_\_main\_\_.py

### script example

```bash
# run the script directly
python test.py
# run the script as a module
python -m test.py
```

### package example

package

+ `__init__.py`
+ `__main__.py`

```bash
# run package
python package
# run package as a module
python -m package
```

`__main__.py` is a entry program of a package, which will always be run.

useful link:

[if __name__=='__main__' in python](http://blog.konghy.cn/2017/04/24/python-entry-program/)

[if __name__ == '__main__'](https://zhuanlan.zhihu.com/p/21297237)

