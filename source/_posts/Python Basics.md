---
title: Python Basics
date: 2019-3-16
update: 2019-3-18
tags: 
	- Python
categories: 
	- Computer Science
	- Programming
	- Python
---
This note contains basic knowledge of Python3 including basic syntax, arithmetic rules, comments, list, dictionary, strings, if statements, for statements, functions and debug operations and so on.



# List

```python
# list
# 使用[]中括号 can create an new list
list_var = []  # 这是一个空list
print(list_var), type(list_var)

# list是具有顺序的一组对象，其中的元素不需要是同类型
list_var = [1, '2', 3, 4.0, 5, 6, 'seven', [8], '九']  # list举例，其中包含了整数、小数、字符串、数组
print(list_var)


# =====list常见操作：索引，选取list中的某个元素
list_var = [1, '2', 3, 4.0, 5, 6, 'seven', [8], '九']  # list举例
print(list_var[0])  # 输出排在第1个位置的元素。位置的计数是从0开始的。
print(list_var[3])  # 输出排在第4个位置的元素。
print(list_var[8])  # 输出排在第9个位置的元素。也就是最后一个元素。
print(list_var[-1])  # 输出最后一个元素的另外一种方式。
print(list_var[-2])  # 输出最后第二个位置的元素。
print(list_var[9])  # 超出长度会报错 IndexError: list index out of range
print(list_var[-10])  # 超出长度会报错 IndexError: list index out of range
list_var[3] = 100  # 可以根据索引，直接修改list中对应位置的元素
print(list_var)


# =====list常见操作：切片，选取list中的一连串元素
# list_var = [1, '2', 3, 4.0, 5, 6, 'seven', [8], '九']  # list举例
# print list_var[3:8]  # list[a:b]，从第a个位置开始，一直到第b个位置之前的那些元素
# print list_var[:4]  # list[:b]，从头开始，一直到第b个位置之前的那些元素
# print list_var[3:]  # list[a:]，从第a个位置开始，一直到最后一个元素
# print list_var[1:7:3]  # list[a:b:c]，每c个元素，选取其中的一个


# =====list常见操作：两个list相加
# list_var1 = [1, '2', 3, 4.0, 5]
# list_var2 = [6, 'seven', [8], '九']
# print(list_var1 + list_var2)  # 两个list相加


# =====list常见操作：判断一个元素是否在list当中
list_var = [1, '2', 3, 4.0, 5]
print(1 in list_var)  # 判断1元素，是否在list_var中出现
print(100 in list_var)  # 判断100元素，是否在list_var中出现


# =====list常见操作：len，max，min
list_var = [1, 2, 3, 4, 5]
print(len(list_var))  # list中元素的个数，或者说是list的长度
print(len([]))  # 空list的长度是？
print(max(list_var))  # 这个list中最大的元素，
print(min(list_var))  # 最小的元素


# =====list常见操作：删除其中的一个元素
list_var = [1, 2, 3, 4, 5]
del list_var[0]  # 删除位置0的那个元素
print(list_var)


# =====list常见操作：如何查找一个元素的在list中的位置
list_var = [3, 5, 1, 2, 4]  # 如何才能知道1这个元素，在list中的位置是什么？
print(list_var.index(4))  # 不知道的话，直接搜索


# =====list常见操作：append,在后方增加一个元素
list_var = [1, '2', 3, 4.0, 5]
list_var.append(6)
print(list_var)
list_var.append(['seven', [8], '九'])
print(list_var)


# =====list常见操作：两个list合并
list_var = [1, '2', 3, 4.0, 5]
list_var.extend([6, 'seven', [8], '九'])
print(list_var)


# =====list常见操作：逆序、排序、
list_var = [3, 5, 1, 2, 4]
list_var.reverse()
print(list_var)
list_var = [3, 5, 1, 2, 4]
list_var.sort()
print(list_var)


# =====list常见操作：range函数
# python2和python3不同
# range函数用于快速创建[0，1，2，3，4，5，6……]这样的list
list(range(5))  # range(a)，对于[0，1，2，3……]这个数组，取前a个元素
list(range(1, 5))  # range(a, b)，对于[0，1，2，3……]这个数组，取从第a个位置的元素开始，到第b个位置元素之前的那个元素
list(range(1, 10, 3))  # range(a, b, c), 每c个元素，选取其中的一个
```

# dictionary
```python
# =====dict介绍
# 使用{}大括号就可以新建一个dict。
dict_var = {}  # 这是一个空dict
print(dict_var)
type(dict_var)

# 具有一系列成对的对象。一个叫做key，一个叫做value。其中的元素(包括key和value)不需要是同类型
dict_var = {'sh600000': '浦发银行',
             'sz000002': '万科A',
             300001: '特锐德'}  # 其中'sh600000'、'sz000002'、300001就是key，'浦发银行'、'万科A'、'特锐德'就是相对应的value。
print(dict_var)

# 字典是无顺序，key不可重复
dict_var[0]  # 因为没有顺序，所以dict_var[0]并不能取出第0个位置的元素，此处会报错。


# =====dict常见操作：根据key的值，取相应的value的值
dict_var['sh600000']  # 获取'sh600000'这个key对应的value
print(dict_var['sh600000'])
dict_var.get('sh600000')
print(dict_var.get('sh600000'))  # 效果同上


# =====dict常见操作：增加、修改一对key：value
dict_var['sh000001'] = '上证指数'
print(dict_var)
dict_var['sh000001'] = '上证综合指数'
print(dict_var['sh000001'])
print(dict_var)


# =====dict常见操作：判断一个key是不是在dict里面
print('sh600000' in dict_var)


# =====dict常见操作：输出一个dict中所有的key和value
print(dict_var.keys())  # 输出所有的key
print(dict_var.values())  # 输出所有的value
```

# string
```python
# =====字符串转义
print('what is wrong')  # 如何输入what's wrong
print('what\'s wrong\t')  # 使用\对特殊字符进行转义。转义也可以用于表达不可见字符，例如tab符号：\t。
print('\\')  # 如果要表达\本身，也需要转义，写为\。
print(r'what\'s wrong')  # 在字符串的开始加r（Raw String），使得字符串中不发生转义。


# =====unicode字符串
print('中国') 
type('中国')
print(u'中国')
type(u'中国')
'中国' == u'中国'


# =====字符串常见操作：字符串相加，相乘
stock_code1 = 'sh600000'
stock_code2 = 'sh600001'
print(stock_code1 + ', ' + stock_code2)  # 字符串可以直接相加
print(stock_code1 * 3)  # 字符串可以乘以整数
print('*' * 30)


# =====字符串常见操作：startswith、endswith、
stock_code = 'sh600000'
print(stock_code.startswith('sh'))  # 判断字符串是否是以'sh'开头
print(stock_code.startswith('s'))
print(stock_code.startswith('sz'))
print(stock_code.endswith('0'))  # 判断字符串是否是以'0'结尾
print(stock_code.endswith('00'))
print(stock_code.endswith('11'))

# =====字符串常见操作：判断
stock_code = 'sh600000'
print('sh' in stock_code)  # 判断字符串中是否包含'sh'
print('sz' in stock_code)


# =====字符串常见操作：替换
stock_code = 'sh600000'
stock_code.replace('sh', 'sz')  # 将字符串中的'sh'替换成'sz'
print('sh600000来自sh'.replace('sh', 'sz'))  # 会替换所有的sh


# =====字符串常见操作：split
stock_code = 'sh600000, sh600001, sh600002, sh600003'
stock_code.split(', ')
print(stock_code.split(', ')[0])
print(stock_code.split('sh'))
# 逆操作
stock_code_list = ['sh600000', 'sh600001', 'sh600002', 'sh600003']
print(', '.join(stock_code_list))


# =====字符串常见操作：strip
stock_code = '  sh600000  '
print(stock_code)
print(stock_code.strip())  # 去除两边的空格


# =====字符串的切片：把字符串当做list
stock_code = 'sh600000'
print(stock_code[0])
print(stock_code[:2])
print(stock_code[2:])
print(len(stock_code))
```

# if statement
```python
# 条件语句语法如下：
"""
if 条件A（结果为布尔值，true或者False）:
    执行相关操作1（需要使用tab缩进）
    ......

elif 条件B（结果为布尔值，true或者False）:
    执行相关操作2
    ......

else:
    执行相关操作3
"""

# 条件语句解释说明如下：
"""
1. 若条件A为True，那么执行相关操作1，程序结束
2. 若条件A为False，那么判断条件B，若条件B为True，那么执行相关操作2，程序结束
3. 若条件A为False，那么判断条件B，若条件B为False，那么执行相关操作3，程序结束
"""

# 条件语句示例：根据股票代码，判断股票来自于哪个市场
stock_code = 'sh600000'  # 尝试将stock_code改成'sz000002'，'aapl'看相关结果。
if stock_code.startswith('sh'):
     print('上海股票')
elif stock_code.startswith('sz'):
     print('深圳股票')
else:
     print('不知道哪里来的股票')
```

# for statement
```python
# =====for循环语句介绍
# for循环是最常用的循环语句
# 案例1：计算1+2+3+……+10
sum_num = 0  # 用于存储计算的结果
for i in list(range(10 + 1)):
    sum_num += i  # 此处需要使用tab按键进行缩进
    print(i, sum_num)

# 案例2：批量判断股票来自于哪个市场
stock_code_list = ['sh600000', 'sh600001', 'sz000001', 'aapl']
for stock_code in stock_code_list:
    # 若stock_code是sh600000
    if stock_code == 'sh600000':
        print(stock_code, '此股票为浦发银行，我已经知道它是来自上海的股票')
        continue  # 跳过此次循环，不运行接下来的语句，直接进入下个循环
        # break  # 停止整个循环，跳出for语句
    # 判断股票来自于哪个市场
    if stock_code.startswith('sh'):
        print(stock_code, '上海股票')
    elif stock_code.startswith('sz'):
        print(stock_code, '深圳股票')
    else:
        print(stock_code, '不知道哪里来的股票')
```

# while statement
```python
# =====while语句
# while语句语法如下：
"""
while 条件A:
    执行相关操作1（需要使用tab缩进）
    ......
"""

# 条件语句解释说明如下：
"""
1. 判断条件A，若条件A为False，那么程序结束。
2. 判断条件A，若条件A为True，那么执行相关操作1。
3. 然后再次判断条件A，重复上面的步骤
"""

# while语句案例1：计算1+2+3+……+10
num = 1
max_num = 10
sum_num = 0  # 存储计算结果
while num <= max_num:
    sum_num += num
    num += 1
    print(sum_num)

# while语句案例2：计算1+2+3+……+10
num = 1
max_num = 10
sum_num = 0
while True:
    sum_num += num
    num += 1
    print(sum_num, num)
    if num == max_num+1:
        break
```

# function
```python
# =====基本函数的定义
def print_h(str_var='hello world'):
    # 以下是函数内容
    # 函数的功能：将str_var变量打印出来
    print(str_var)

# 以def开头
# print_h是函数名
# str_var是参数，可以带上默认参数
# 函数首行的最后需要带上冒号


# =====调用函数
print_h()
print_h(str_var='你好，世界')
```

# try
```python
import time  # 导入系统库time，可以使用一些系统级别的函数

def buy_one_stock(stock_name='sh600000'):  # 参数为股票名
    """
    此程序用于下单买入某个股票，但是买入过程中，程序有50%的概率报错。
    """
    import random
    random = random.random()
    if random >= 0.5:
        return
    else:
        raise ValueError('程序报错！')
# buy_one_stock()

max_try_num = 5
tyr_num = 0
while True:
    try:  # 尝试做以下事情
        buy_one_stock()
    except:  # 如果因为各种原因报错
        print('警告！下单出错，停止1秒再尝试')
        tyr_num += 1
        time.sleep(5)
        if tyr_num > max_try_num:
            print('超过最大尝试次数，下单失败')
            # 此处需要执行相关程序，通知某些人
            break
    else:  # 如果没有报错
        print('下单成功了')
        break
```