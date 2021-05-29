---
title: C++ Array, Pointer & String
date: 2019-2-27
tags: 
	- C++
	- MOOC
categories: 
	- Computer Science
	- Programming
	- C++
---
This note contains the basic rules of array, pointer and string in C++.

# Array

## Definition

Type Identifier *Name* [*Expression1*] [*Expression2*]...

```c++
int a[10]
// a is an integer array with 10 elements.
```

```c++
int a[5][3]
// a is an 2-dimension integer array with 5 rows and 3 columns and 15 elements.
```

tips

+ The array must be declared first, then be used.

+ refer the elements one by one, not the whole array.

  ```c++
  a[0]=a[5]+a[7]-a[2*3]
  b[1][2]=a[2][3]/2
  ```

example

```c++
#include <iostream>
using namespace std;
int main() {
	int a[10], b[10];
	for(int i = 0; i < 10; i++) {
		a[i] = i * 2 - 1;
		b[10 - i - 1] = a[i];
	}
	for(int i = 0; i < 10; i++) {
	cout << "a[" << i << "] = " << a[i] << " ";
	cout << "b[" << I << "] = " << b[i] << endl;
	}	
return 0;
}
```

## Initialization

+ One dimension 

    ```C++
    // 1. list all the initial value of elements
    static int a[10]={0,1,2,3,4,5,6,7,8,9}
    // 2. initialize part of elements
    static int a[10]={0,1,2,3,4}
    // 3. don't set the length when initializing
    static int a[]={0,1,2,3,4,5,6,7,8,9}
    ```

+ two dimension

    ```c++
    // 1. list all the initial value in braces by order
    static int a[3][4]={1,2,3,4,5,6,7,8,9,10,11,12}
    // 2. list the initial value by different rows
    static int a[3][4]={{1,2,3,4},{5,6,7,8},{9,10,11,12}}
    // 3. initialize part of elements
    static int a[3][4]={{1},{0,6},{0,0,11}}
    // 4. list all the initial values, the first index can be ignored
    static int a[][4]={1,2,3,4,5,6,7,8,9,10,11,12}
    static int a[][4]={{1,2,3,4},{5,6,7,8},{9,10,11,12}}
    ```

>Find the first 20 items in Fibonacci sequence

```c++
#include <iostream>
using namespace std;
int main() {
	int f[20] = {1,1}; //initialize the 0th and the first number
	for (int i = 2; i < 20; i++)
		f[i] = f[i - 2] + f[i - 1];
	for (int i=0;i<20;i++) { //output 5 number on each row
		if (i % 5 == 0) cout << endl;
		cout.width(12); //set output width in 12
		cout << f[i];
	}
return 0;
}
```

> Input the answers of multiple choices in a loop, compute and output the correct rate of each answer till input the ctrl+z. The answers will be input in a row as “a”, “b”, "c", "d".

```c++
#include <iostream>
using namespace std;
int main() {
	const char key[ ] = {'a','c','b','a','d'};
	const int NUM_QUES = 5;
	char c;
	int ques = 0, numCorrect = 0;
	cout << "Enter the " << NUM_QUES << " question tests:" << endl;
	while(cin.get(c)) {
	    if(c != '\n') {
	        if(c == key[ques]) {
		        numCorrect++; cout << " ";
		    } else
		        cout<<"*";
			    ques++;
		} else {
		    cout << " Score " << static_cast<float>(numCorrect)/NUM_QUES*100 << "%";
		    ques = 0;  numCorrect = 0; cout << endl;
		}
	}
	return 0;
}
```

## Array as argument

tips

+ when elements in an array are parameters, they are just like variables. The name of array should be arguments and parameters. Type should be the same.

> Compute the sum of every row of an array.

```c++
#include <iostream>
using namespace std;
void rowSum(int a[][4], int nRow) {
	for (int i = 0; i < nRow; i++) {
    	for(int j = 1; j < 4; j++)
        	a[i][0] += a[i][j];
     }
}
int main() {
    int table[3][4] = {{1, 2, 3, 4}, {2, 3, 4, 5}, {3, 4, 5, 6}};
    for (int i = 0; i < 3; i++)  {
         for (int j = 0; j < 4; j++)
              cout << table[i][j] << "   ";
         cout << endl;
    }
    rowSum(table, 3); //compute the sum of every row
	//output the result
    for (int i = 0; i < 3; i++) 
	    cout << "Sum of row " << i << " is " << table[i][0] << endl;
    return 0;
}
```

## Object Array

+ definition

  **Class Name** *Array Name*[number of elements]

+ syntax

  **Array Name**[index].*member Name*

+ initialization

  ```c++
  Point a[2]={Point(1,2),Point(3,4)}
  ```

+ example

  ```c++
  //Point.h
  #ifndef _POINT_H
  #define _POINT_H
  class Point {
  public:
  	Point();
  	Point(int x, int y);
  	~Point();
      void move(int newX,int newY);
      int getX() const { return x; }
      int getY() const { return y; }
      static void showCount();
  private:
  	int x, y;
  };
  #endif //_POINT_H
  
  //Point.cpp
  #include <iostream>
  #include "Point.h"
  using namespace std;
  Point::Point() : x(0), y(0) {
  	cout << "Default Constructor called." << endl;
  }
  Point::Point(int x, int y) : x(x), y(y) {
  	cout << "Constructor called." << endl;
  }
  Point::~Point() {
  	cout << "Destructor called." << endl;
  }
  void Point::move(int newX,int newY) {
  	cout << "Moving the point to (" << newX << ", " << newY << ")" << endl;
  	x = newX;
  	y = newY;
  }
  
  //main.cpp
  #include "Point.h"
  #include <iostream>
  using namespace std;
  int main() {
  	cout << "Entering main..." << endl;
  	Point a[2];
  	for(int i = 0; i < 2; i++)
  		a[i].move(i + 10, i + 20);
  	cout << "Exiting main..." << endl;
  	return 0;
  }
  ```

## for loop based on range

+ traversal all the elements in an array

```c++
int main(){
	int array[3] = {1,2,3};
	int *p;
	for(p = array; p < array + sizeof(array) / sizeof(int); ++p){
	    *p += 2;
	    std::cout << *p << std::endl;
	}
	return 0;
}
```

```c++
int main(){
	int array[3] = {1,2,3};
	for(int & e : array){
	    e += 2;
	    std::cout<<e<<std::endl;
	}
	return 0;
}
```

# Pointer

## Definition

+ pointer operator

  + \**Pointer Name*

    ```c++
    static int i;
    static int* ptr = &i
    *ptr = 3
    ```

+ address operator

  + &*Variable Name*

## Initialization

syntax

+ *Storage Type* Type Identifier * **Pointer Name** = initial address

```c++
int *pa = &a
```

tips:

+ The variable should be declared before assigned to a pointer.
+ A non-static variable can be assigned to a static pointer.

## Assignment

syntax

+ **Pointer Name** = address value

tips:

+ The address value must be a address constant or address variable rather than an integer.

+ 0 can be assigned to a pointer, which means a null pointer. Now `nullptr` can be used as a null pointer
+ `void` pointer can be assigned to the address of any type object.

example of pointer

```c++
#include <iostream>
using namespace std;
int main() {
	int i;
	int *ptr = &i; //assign the address of i to ptr
	i = 10;
	cout << "i = " << i << endl; //output the value of the int variable
	cout << "*ptr = " << *ptr << endl; //output the content that the int pointer is assigned to
return 0;
}
```

the output result is:

```
i = 10
*ptr = 10
```

example of a void pointer

```c++
#include <iostream>
using namespace std;
int main() {
	//!void voidObject; //wrong: there is no void  variable
	void *pv; //right: the void type pointer
	int i = 5;
	pv = &i; //void pointer is assigned to the int variable
	int *pint = static_cast<int *>(pv); //void pointer is transformed to an int pointer
	cout << "*pint = " << *pint << endl;
return 0;
}
```

+ pointer assigned to an constant and const pointer

  + the assigned object cannot be changed by a pointer assigned to an constant.

  ```c++
  int a;
  const int *p1 = &a; //p1 is a pointer assigned to an constant
  int b;
  p1 = &b; //right，the assigned value of p1 can be changed
   *p1 = 1; //wrong，the object value cannot be changed by p1
  ```

  + the assigned value of an const pointer cannot be changed

  ```c++
  int a;
  int * const p2 = &a;
  p2 = &b; //wrong，p2 is a const pointer which cannot be changed
  ```

## Operation

### Arithmetic Operation

+ addition and subtraction: 

  + +n or -n meaning

    the pointer assign to the initial address of the n-th data object.

  + ++ or --

    the initial address of the last or the next data object

  ```c++
  short a[4]
  short *pa=a
  ```

### Relationship Operation

tips:

+ the same type of pointers can be operated with relationship

```c++
p==0
p!=0
```

## Access Array with Pointer

```c++
int a[10], *pa;
pa = &a[0]; //or: pa = a
```

tips: 

+ There are similar expression:

  + `*pa` is `a[0]`,  `*(pa+1)` is `a[1]`,  `*(pa+i)` is `a[i]`,  

  + `a[i]`,`*(pa+i)`,`*(a+i)` and `pa[i]`are the same effect.

+ `a++` is wrong, because a is the initial address of the array, a constant.

example:

+ access array with index

```c++
#include <iostream>
using namespace std;
int main(){
	int a[10] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 0 };
	for (int i = 0; i < 10; i++)
		cout << a[i] << "  ";
	cout << endl;
	return 0;
}
```

+ access array with pointer

```c++
#include <iostream>
using namespace std;
int main() {
	int a[10] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 0 };
	for (int i = 0; i < 10; i++)
		cout << *(a+i) << "  ";
	cout << endl;
	return 0;
}
```

+ access array with pointer variable

```c++
#include <iostream>
using namespace std;
int main() {
	int a[10] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 0 };
	for (int *p = a; p < (a + 10); p++)
		cout << *p << "  ";
	cout << endl;
	return 0;
}
```

## Array with pointer elements

Definition：

​	`Point *pa[2]` is made up of `pa[0]` and `pa[1]`.

```c++
#include <iostream> 
using namespace std;
int main() {
	int line1[] = { 1, 0, 0 };	//The first row
	int line2[] = { 0, 1, 0 };	//The second row
	int line3[] = { 0, 0, 1 };	//The third row
	//define an int array with pointer elements and initialize it
	int *pLine[3] = { line1, line2, line3 };	
	cout << "Matrix test:" << endl;
	for (int i = 0; i < 3; i++) {
		for (int j = 0; j < 3; j++)
	    	cout << pLine[i][j] << " ";
    	cout << endl;
	}
	return 0;
}
```

The output result is:

```c++
Matrix test:
1,0,0
0,1,0
0,0,1
```

## Function with pointer arguments and parameters

+ example: split a number into integer and fraction.

```c++
#include <iostream>
using namespace std;
void splitFloat(float x, int *intPart, float *fracPart) {
    *intPart = static_cast<int>(x);
	*fracPart = x - *intPart;
}
int main() {
	cout << "Enter 3 float point numbers:" << endl;
	for(int i = 0; i < 3; i++) {
    	float x, f;
    	int n;
    	cin >> x;
    	splitFloat(x, &n, &f);	//address is the parameter.
    	cout << "Integer Part = " << n << " Fraction Part = " << f << endl;
	}
	return 0;
}
```

+ example: a pointer assigned to const is argument

```c++
#include <iostream>
using namespace std;
const int N = 6;
void print(const int *p, int n);
int main() {
    int array[N];
    for (int i = 0; i < N; i++)
        cin>>array[i];
    print(array, N);
	return 0;
}
void print(const int *p, int n) {
    cout << "{ " << *p;
    for (int i = 1; i < n; i++)
        cout << ", " << *(p+i);
    cout << " }" << endl;
}
```

## Function with a pointer return value

syntax:

+ **Type Identifier** *Function Name(){

  ​	//expression

  }

tips:

+ a non-static local address cannot be a return value.

example1:

```c++
#include <iostream>
using namespace std;
int main(){
    int array[10];
    int* search(int* a, int num);
    for(int i=0; i<10; i++)
        cin>>array[i];
    int* zeroptr= search(array, 10);  //assign the address of array in main function to the sub-function
    return 0;
}
int* search(int* a, int num){ //pointer a assign to the array defined in the main function
    for(int i=0; i<num; i++)
        if(a[i]==0)
            return &a[i];
}
```

example2:

```c++
#include <iostream>
using namespace std;
int main(){
    int* newintvar();
    int* intptr= newintvar();
    *intptr=5; //a valid address
    delete intptr; //if not delete, the memory will leak
    return 0;
}
int* newintvar (){ 
    int* p=new int();
    return p; //the returned address is assigned to the dynamic allocated space
}
```

## Pointer assigned to the Function

Definition:

*Type Identifier* (\***Function Pointer Name**)();

> define a function which can achieve any kind of arithmetic operation

 ```c++
#include <iostream>
using namespace std;

int compute(int a, int b, int(*func)(int, int))
{ return func(a, b);}

int max(int a, int b)
{ return((a > b)?a: b);}

int min(int a, int b)
{ return((a < b)?a: b);}

int sum(int a, int b)
{ return a + b;}

int main(){
    int a, b, res;
    cout << "inout intager a: "; cin >> a;
    cout << "inout intager b: "; cin >> b;
    res = compute(a, b, & max);
    cout << "Max of " << a << " and " << b << " is " << res << endl;
    res = compute(a, b, & min);
    cout << "Min of " << a << " and " << b << " is " << res << endl;
    res = compute(a, b, & sum);
    cout << "Sum of " << a << " and " << b << " is " << res << endl;
}
 ```



## Object Pointer

syntax: 

+ definition:

  *Class Name* \***Object Pointer Name**

    ```
    Point a(5, 10);
    Point *ptr;
    ptr = &a;
    ```

+ access object member by pointer

  **Object Pointer Name**-> *object member name*

	`ptr->getx()` equals `(*ptr).getx()`;

example:

```c++
#include <iostream>
using namespace std;
class Point {
public:
    Point(int x = 0, int y = 0) : x(x), y(y) { }
    int getX() const { return x; }
    int getY() const { return y; }
private:
	int x, y;
};

int main() {
    Point a(4, 5);
    Point *p1 = &a; //define object pointer and initialize with address of a
    cout << p1->getX() << endl;
    cout << a.getX() << endl;
    return 0;
}
```

## This Pointer

`return x` equals to`return this -> x`

```c++
class Fred; 
class Barney {
	Fred *x;
};
class Fred {
	Barney y;
};
```



## Dynamic Memory Allocation

### Definition

syntax:

*new* **Type Identifier**(initial arguments list)

*delete* **Pointer Name**

example:

```c++
#include <iostream>
using namespace std;
class Point {
public:
    Point() : x(0), y(0) {
    cout<<"Default Constructor called."<<endl;
    }
    Point(int x, int y) : x(x), y(y) {
    cout<< "Constructor called."<<endl;
    }
    ~Point() { cout<<"Destructor called."<<endl; }
    int getX() const { return x; }
    int getY() const { return y; }
    void move(int newX, int newY) {
    x = newX;
    y = newY;
    }
private:
	int x, y;
};

int main(){
    cout << "step one: " << endl;
    Point *ptr1 = new Point; //default constructor function
    delete ptr1; //destructor function
    cout << "Step two: " << endl;
    ptr1 = new Point(1,2);
    delete ptr1;
    return 0;
}
```

The result:

```c++
Step One:
Default Constructor called.
Destructor called.
Step Two:
Constructor called.
Destructor called.
```

### Dynamic Array

syntax:

+ one dimension

  new **Type identifier** [length of the array]

  delete[] **Array Name**

example:

```c++
#include <iostream>
using namespace std;
class Point {
public:
    Point() : x(0), y(0) {
    cout<<"Default Constructor called."<<endl;
    }
    Point(int x, int y) : x(x), y(y) {
    cout<< "Constructor called."<<endl;
    }
    ~Point() { cout<<"Destructor called."<<endl; }
    int getX() const { return x; }
    int getY() const { return y; }
    void move(int newX, int newY) {
    x = newX;
    y = newY;
}

private:
	int x, y;
};

int main() {
    Point *ptr = new Point[2]; //create
    ptr[0].move(5, 10);
    ptr[1].move(15, 20);
    cout << "Deleting..." << endl;
    delete[] ptr;
    return 0;
}
```

The result is:

```
Default Constructor called.
Default Constructor called.
Deleting...
Destructor called.
Destructor called.
```

+ multiple dimension

  new **Type identifier** [length of the dimension1] [length of the dimension2]

example:

```c++
#include <iostream>
using namespace std;
int main() {
    int (*cp)[9][8] = new int[7][9][8];
    for (int i = 0; i < 7; i++)
        for (int j = 0; j < 9; j++)
            for (int k = 0; k < 8; k++)
                *(*(*(cp + i) + j) + k) =（i * 100 + j * 10 + k);
    for (int i = 0; i < 7; i++) {
        for (int j = 0; j < 9; j++) {
            for (int k = 0; k < 8; k++)
                cout << cp[i][j][k] << " ";
    		cout << endl;
		}
		cout << endl;
	}
	delete[] cp;
	return 0;
}
```

example2: encapsulate dynamic array class

```c++
#include <iostream>
#include <cassert>
using namespace std;
class Point {
public:
    Point() : x(0), y(0) {
    cout<<"Default Constructor called."<<endl;
    }
    Point(int x, int y) : x(x), y(y) {
    cout<< "Constructor called."<<endl;
    }
    ~Point() { cout<<"Destructor called."<<endl; }
    int getX() const { return x; }
    int getY() const { return y; }
    void move(int newX, int newY) {
    x = newX;
    y = newY;
	}
private:
	int x, y;
};
class ArrayOfPoints {
public:
    ArrayOfPoints(int size) : size(size) {
    	points = new Point[size];
    }
    ~ArrayOfPoints() {
    	cout << "Deleting..." << endl;
    	delete[] points;
    }
    Point& element(int index) {
    	assert(index >= 0 && index < size);
    	return points[index];
	}
private:
    Point *points; //dynamic array initial address
    int size; //size of array
};

int main() {
    int count;
    cout << "Please enter the count of points: ";
    cin >> count;
    ArrayOfPoints points(count);
    points.element(0).move(5, 0);
    points.element(1).move(15, 20);
    return 0;
}
```

The result is:

```c++
Please enter the number of points:2
Default Constructor called.
Default Constructor called.
Deleting...
Destructor called.
Destructor called.
```

## Smart Pointer

`unique_ptr`

`shared_ptr`

`weak_ptr`

## Vector

syntax:

+ definition

vector\<*Element Type*\> **Array Name**(array length);

```c++
vector<int> arr(5)
```

+ access

vector **Array name** [ index ]

vector **Array name**.size()

example:

> Calculate the average of elements in the array.

```c++
#include <iostream>
#include <vector>
using namespace std;

double average(const vector<double> &arr){
    double sum = 0;
    for (unsigned i = 0; i<arr.size(); i++)
    sum += arr[i];
    return sum / arr.size();
}
int main() {
    unsigned n;
    cout << "n = ";
    cin >> n;
    vector<double> arr(n); //create array object
    cout << "Please input " << n << " real numbers:" << endl;
    for (unsigned i = 0; i < n; i++)
    cin >> arr[i];
    cout << "Average = " << average(arr) << endl;
    return 0;
}
```

example2: auto pointer

```c++
#include <vector>
#include <iostream>
int main(){
    std::vector<int> v = {1,2,3};
    for(auto i = v.begin(); i != v.end(); ++i)
    	std::cout << *i << std::endl;
    for(auto e : v)
    	std::cout << e << std::endl;
}


```

# Object Replication

## Shallow Copy



## Deep Copy



## Move Assignment

syntax:

class_name ( class_name && )

example: 

+ version 1

```c++
#include<iostream>
using namespace std;
class IntNum{
public:
	IntNum(int x = 0) : xptr(new int(x)){ //constructor
	cout << "Calling constructor..." << endl;
	}
    IntNum(const IntNum & n) : xptr(new int(*n.xptr)){//copy constructor
    cout << "Calling copy constructor..." << endl;
    };
    ~IntNum(){ //destructor
    delete xptr;
    cout << "Destructing..." << endl;
    }
    int getInt() { return *xptr; }
private:
	int *xptr;
};
//return IntNum class object
IntNum getNum(){
	IntNum a;
	return a;
}
int main() {
	cout<<getNum().getInt()<<endl;
	return 0;
}
```

+ version 2:

```c++
#include<iostream>
using namespace std;
class IntNum {
public:
    IntNum(int x = 0) : xptr(new int(x)){ //constructor
    cout << "Calling constructor..." << endl;
    }
	IntNum(const IntNum & n) : xptr(new int(*n.xptr)){ // copy constructor
	cout << "Calling copy constructor..." << endl;
 	IntNum(IntNum && n): xptr( n.xptr){ //move constructor
 	n.xptr = nullptr;
	cout << "Calling move constructor..." << endl;
}

~IntNum(){ //destructor
    delete xptr;
    cout << "Destructing..." << endl;
}
private:
	int *xptr;
};

//return IntNum class
IntNum getNum() {
	IntNum a;
	return a;
}
int main(){
	cout << getNum().getInt() << endl; 
    return 0;
}
```



# String

## String of C type

syntax:

+ string constant

const char \***string name**="*string content*"

```c++
const char *STRING1 = "program"
```

+ string array

char **string name** = {,..,'\0'}

```c++
char str[8] = { 'p', 'r', 'o', 'g', 'r', 'a', 'm', '\0' };
char str[8] = "program";
char str[] = "program";
```

## String Class

syntax:

+ constructor
  + `string()`
  + `string(const char *s)`
  + `string(const string& rhs)`

+ operator
  + `s+t`
  + `s=t`
  + `s==t`, `s!=t`, `s<=t`, `s>=t`, `s<t`, `s>t`
  + `s[i]`

```c++
string s1 = "abc", s2 = "def";
string s3 = s1 + s2; //"abcdef"
bool s4 = (s1 < s2); //true
char s5 = s2[1]; //'e'
```

example:

```c++
#include <string>
#include <iostream>
using namespace std;
//output true or false based on the value
//title is notification
inline void test(const char *title, bool value){
    cout << title << " returns "
    << (value ? "true" : "false") << endl;
}
int main() {
    string s1 = "DEF";
    cout << "s1 is " << s1 << endl;
    string s2;
    cout << "Please enter s2: ";
    cin >> s2;
    cout << "length of s2: " << s2.length() << endl;
    test("s1 <= \"ABC\"", s1 <= "ABC");
    test("\"DEF\" <= s1", "DEF" <= s1);
    s2 += s1;
    cout << "s2 = s2 + s1: " << s2 << endl;
    cout << "length of s2: " << s2.length() << endl;
    return 0;
}
```

### getline

getline(*cin*, **string name**)

getline(*cin*, **string name**, ',')

example:

```c++
include <iostream>
#include <string>
using namespace std;
int main() {
    for (int i = 0; i < 2; i++){
    string city, state;
    getline(cin, city, ',');
    getline(cin, state);
    cout << "City:" << city << “ State:" << state << endl;
    }
    return 0;
}
```

