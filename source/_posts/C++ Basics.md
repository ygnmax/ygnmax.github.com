---
title: C++ Basics
date: 2019-1-16
update: 2019-1-22
tags: 
	- C++
	- MOOC
categories: 
	- Computer Science
	- Programming
	- C++
---
This note contains basic structures of C++ including Iostream, if, while, for controlling statements.



## IOstream
Stream class:

+ standard I/O
+ read & write files

Standard I/O

+ Input: screen
+ Output: keyboard

notations

1\.input: `>>`; output: `<<`

+ cout << *expression* << *expression*
+ cin >> *expression* >> *expression"
	```c++
		int a, b;
		cin >> a >> b
	```



2\. manipulator

+ `dec`: decimal
+ `hex`: hexadecimal
+ `oct`: octal
+ `ws`: extract blank character
+ `endl`: change a line and refresh current
+ `ends`: insert blank character
+ `setsprecision(int)`: set the number of decimals of floats
+ `setw(int)`: set width

		cout << setw(5) << setprecision(3) << 3.1415


## if statement

syntax:

+ if(*expression*) *statement*
	```c++
		if (x > y) cout << x;
	```
+ if(*expression*) *statement1*  
  else *statement2*

  ```c++
  if ( x > y) cout << x;
  else cout << y;
  ```

+ if(*expression1*) *statement1*   
  else if(*expression2*) *statement2*  
  else if(*expression3*) *statement3*  
  ...  
  else *statementn*

> **determine whether a year is a leap year**
>
	```
	#include <iostream>  
	using namespace std
	int main(){
	int year;
	bool isLeapYear;
	cout << "Enter the year: ";
	cin >> year;
	isLeapYear = ((year % 4 == 0 && year & 100 != 0) || (year % 400 == 0));
	if (isLeapYear)
		cout << year << "is a leap year" << endl;
	else
		cout << year << "is not a leap year" << endl;
	return 0;
	}
	```
nesting:

+ if(*expression1*)      
　　if(*expression2*) *statement1*  
　　else *statement2*  
  else  
　　if(*expression3*) *statement3*  
　　else *statement4*

tips:

+ match each if and else, or use {}

>**compare 2 input integers**
>
```c++
#include<iostream>
using namespace std;
int main(){
	int x, y;
	cout << "Enter x and y: ";
	cin >> x >> y;
	if (x != y)
		if (x > y)
			cout << "x > y" << endl;
		else
			cout << "x < y" << endl;
	else
		cout << "x = y" << endl;
return 0;
}
```

## switch statement
syntax:

+ switch(*expression*){  
 case *expression1* : *statement1*

> **calculate the area of a graph**

## while statement
syntax:

+ while (*expression*) *statement*

tips: 

+ The statement must contain what changes the conditions of loop, which can be composite.
+ order: calculate the expression first. If it is true, do the statement

> **calculate the sum of natural number 1 ~ 10**
>
> ```c++
> #include <iostream>
> using namespace std;
> int main(){
> int i = 1, sum = 0;
> while (i <= 10){
>     	sum += i;  //sum = sum + i;
>     	i++;
>   	}
> cout << "sum = " << sum << endl;
>     return 0;
> }
> ```

## do-while statement
syntax:
> **calculate the sum of natural number 1 ~ 10**
>```c++
#include <iostream>
using namespace std;
int main()
{
    int i = 1, sum = 0;
    do {
        sum += i;
        i++;
    } while (i <= 10);
    cout << "sum = " << sum << endl;
    return 0;
}
>```

## for statement
syntax:

+ for(*initial statement*; *expression1*; *expression2*) *statement*

tips:

+ If expression1 is true, do the loop.
+ After the loop, do the expression2. 
+ The for statement can replace the while and do-while statement.

> **calculate the sum of natural number 1 ~ 10**
>```c++
	#include <iostream>
	using namespace std;
	int main(){
		int i = 1, sum = 0;
		for(i=1;i<=10;i++)
		{
			sum += i;
		}
		cout << "sum = " << sum << endl;
		return 0;
	}
	```
> **find all the factors of an input integer**






## nesting & other statement
syntax:

+ break
+ continue
+ goto

> **input an array of integers, determine whether each is positive or negative and count the number of them respectively**



## definition of type
1\. definition

+ typedef  
+ using

2\. enumeration

+ enum *TypeName* {*list of values*}
	```c++
    enum Weekday
    {SUN, MON, TUE, WED, THU, FRI, SAT}
	```
tips:
+ they cannot be evaluated to new values.
+ they can be matched with new values when defined.
	```c++
    enum Weekday
    {SUN=7, MON=1,}
  ```
+ they can be caluated.

3\. initial  

+ auto
+ decltype