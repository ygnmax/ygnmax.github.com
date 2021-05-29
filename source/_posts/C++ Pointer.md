---
title: C++ Class
date: 2019-10-4
tags: 
	- C++
	- MOOC
categories: 
	- Computer Science
	- Programming
	- C++
---
```c++
// define without initialized
int *p

// define
int n = 10; int *p = &n;

int a a[8] = {1, 2, 3, 4, 5, 6, 7, 8}; int * p = a;
```

p as a pointer will point to the first element of array a



```c++
Pointer Assignment 
int n = 10; int *p = &n, *q; q = p;
```



"&": get the address

```c++
int m, n = 10;
int *q = & n;
m = *q;
```



+ Swap 2 integers

example 1: swap 2 integers by changing integer values

```c++
#include<iostream>
using namespace std;
int main()
{
    //exchange m and n, without changing the pointer p and q    
	int m = 10， n = 20； t;
	int *p = &m;
	int *q = &n;

	t = *p;
	*p = *q;
	*q = t;

return 0;
}
```





example 2: swap 2 integers by changing pointer

```c++
#include<iostream>
using namespace std;

int main()
{
	int m =10, n = 20;
    int *p = &m, *q = &n, *t;
    
    t = p;
	p = q;
	q = t;
    
    return 0;
}
```



example 3: swap 3 integers by function

```c++
#include<iostream>
using namespace std;
void Swap(int *x, int *y);

int main()
{
	int m = 10, n = 20;
    #ifndef NDEBUG
    cout << "main (before swapped): m = " << m << "; n = " << n << endl;
    #endif
    Swap(&m, &n);
    #ifndef NDEBUG
    cout << "main (after swapped): m = " << m << "; n = " << n << endl;
    #endif    
    return 0;
}

void Swap(int *x, int *y)
{
    int t;
    if (! x || !y){
        cout << ""
    }
}
```



## Constant Pointer

+ Constant Pointer

```c++
int n = 10; const int *p = &n;
```



```c++
void PrintObject( const int *p);
```



+ Pointer pointing to a constant

```c++
int n = 10; int * const p = &n;
```



+ Constant pointer pointing to a constant

```c++
const int n = 10; const int * const p = &n;
```



## pointer and return value

```c++
int global = 0;
int *ReturnPointer()
{
    return &global;
}
```



## Pointer and complicated data type

```c++
int a[8] = {1, 2, 3, 4, 5, 6, 7, 8};
int *p; p =&a[0];

int *p; p = a
int *q; q = &a[2]; // q point to a[2]
```



### pointer operation

```c++
*p = a
p+2
*p = a[3]; p-2
q = p+2
p++
--p
*p = a[0]; *q = a[2]; q-p = 2;

p == q
p = NULL
if(p != NULL)
if(p)
```



## pointer and array

```c++
//Definition
void GenerateIntegers(int a[], unsigned int n)
{
    unsigned int i;
    Randomize();
    for (i = 0; i < n; i++)
        a[i] = GenerateRandomNumber(Lower, Upper);
}

//Call
#define NUM_OF_ELEMENTS 8
int a[NUM_OF_ELEMENTS];
GenerateIntegers(a, NUM_OF_ELEMENTS);
```

Pointers as parameter

```C++
//Definition
void GenerateIntegers(int *p, unsigned int n)
{
    unsigned int i;
    Randomize();
    for (i = 0; i < n; i++)
        *p++ = GenerateRandomNumber(Lower, Upper);
}

//Call
#define NUM_OF_ELEMENTS 8
int a[NUM_OF_ELEMENTS];
GenerateIntegers(a, NUM_OF_ELEMENTS);
```

example:



### Similarity of pointer and array 

```c++
int a[3] = {1, 2, 3}; int *p = &a; int i;
for (i  = 0; i < 3; i++)
    cout << p[i] << endl;
for (i  = 0; i < 3; i++)
	cout << *(a+i) << endl;
```



+ multidimensional array 

```c++
void PrintTwoDimensinalArray( int a[8][8], unsigned int m, unsigned int n );

void PrintTwoDimensinalArray( int a[][], unsigned int m, unsigned int n );

void PrintTwoDimensinalArray( int * a, unsigned int m, unsigned int n );
// a + n * i + j
```

```c++
// 
void PrintTwoDimensinalArray(int * a, unsigned int m, unsigned int n)
{
unsigned int i, j;
for( i = 0; i < m; i++ )
for( j = 0; j < n; j++ )
cout << *(a + n * i + j) << "; ";
}
// 
int a[2][3] = { { 1, 2, 3 }, { 4, 5, 6 } };
PrintTwoDimensinalArray( a, 2, 3 );
```



## pointer and structure

```c++
struct STUDENT{ int id; STRING name; int age; };
STUDENT student = { 2007010367, "Name", 19 };
STUDENT * pstudent = &student;

(*pstudent).id = 2007010367;
(*pstudent).name = DuplicateString( "Name" );
(*pstudent).age = 19;

pstudent->id = 2007010367;
```

```c++
struct ARRAY{ unsigned int count; int * elements; };
int a[8] = { 1, 2, 3, 4, 5, 6, 7, 8 };
ARRAY array = { 8, &a };
```

```c++
//访问 elements 的第 i 个元素: array.elements[i]
//若有定义:ARRAY * parray = &array;
//访问 parray 指向的结构体对象 elements 的第 i 个元素:
(*parray).elements[i]
parray->elements[i]
```

+ dynamic array

```c++
struct ARRAY { unsigned int count; int *
elements; };
```



# String

## String array

```c++
char s[8] = { 'C', 'P', 'P', '-', 'P', 'r', 'o', 'g' };
char t[5] = { 'H', 'e', 'l', 'l', 'o' };
```

```c++
// add '\0' at the end of string array
char s[9] = { 'C', 'P', 'P', '-', 'P', 'r', 'o', 'g', '\0' };
char t[6] = { 'H', 'e', 'l', 'l', 'o', '\0' };
```

example:

```c++
unsigned int FindCharFirst( char c, char s[] )
{
    unsigned int i;
    if( !s )
    {
        cout << "FindCharFirst: Illegal string.\n";
        exit(1);
    }
        for( i = 0; s[i] != '\0'; i++ )
    {
        if( s[i] == c )
        return i;
    }
    return inexistent_index; // 0xFFFFFFFF
}
```

```c++
unsigned int FindCharFirst( char c, char * s )
{
    char * t;
    if( !s )
    {
        cout << "FindCharFirst: Illegal string.\n";
        exit(1);
    }
        for( t = s; *t != '\0'; t++ )
    {
        if( *t == c )
        return t - s;
    }
    return inexistent_index; // 0xFFFFFFFF
}
```

## abstract string

```c++
typedef char * STRING;
typedef const char * CSTRING;

unsigned int FindCharFirst( char c, char s[] );
unsigned int FindCharFirst( char c, char* s );
unsigned int FindCharFirst( char c, STRING s );
```



```c++
char s[9] = { 'C', 'P', 'P', '-', 'P', 'r', 'o', 'g', '\0' };

char * s = "CPP-Prog";

char * s; s = "CPP-Prog"; //correct

char s[9]; s = "CPP-Prog"; //wrong
char s[9] = "CPP-Prog" //correct

```

example

```c++
STRING TransformCharIntoString( char c )
{
    STRING _s = (STRING)malloc( 2 );
    _s[0] = c;
    _s[1] = '\0';
    return _s;
}

//wrong
STRING TransformCharIntoString( char c )
{
	char _s[2];
    _s[0] = c;
	_s[1] = '\0';
	return _s;
}
```

# standard string library

```c++
char * strcat( char * dest, const char * src );
int strcmp( const char * s1, const char * s2 );
char * strcpy( char * dest, const char * src );
int strlen( const char * s );
char * strtok( char * token, const char * delimiters );
```



# String Class

```c++
string s = "abcdefg";
string s( "abcdefg" );

cout << s << endl;
cin >> s; 
getline( cin, s, '\n' ); 
```



```c++
string s = "abcdefg";
int a = s.length();
s.resize(32); // 将s设为32字符长,多余舍弃,不足空闲
s.resize(32, '='); // 多余舍弃,不足补‘=’

string s1 = "abcd", s2 = "efg";
s1.append( s2 ); // 将字符串s2追加到s1尾部

string s1 = "abcdefg", s2 = "abcdxyz";
int a = s1.compare( s2, 0 ); // 从0号位字符开始比较

string s1 = "abcdefg", s2 = "bcd";
int a = s1.find( s2, 0 );
```



# Dynamic Storage Allocation

```c++
#include <cstdlib>
#include <cmalloc>
void * malloc( unsigned int size );
void free( void * memblock );
```

## malloc

```c++
char * p;
p = (char *)malloc(11);
```

```c++
char * DuplicateString( char * s )
{
    char * t;
    unsigned int n, i;
    if( !s )
    { 
        cout << "DuplicateString: Parameter Illegal."; 
        exit(1); 
    }
    n = strlen( s );
    t = ( char * )malloc( n + 1 );
    for( i = 0; i < n; i++ )
    	t[i] = s[i];
    t[n] = '\0';
    return t;
}
```

```c++
char * p;
p = (char *)malloc(11);
free(p);

int * p = ( int * )malloc( 10 * sizeof( int ) );
free( p );

free( p ); p = NULL;
```

## new

```c++
int * p; p = new int; *p = 10;
int * p; p = new( int ); *p = 10;
int * p; p = new int(10); // 将 *p 初始化为 10
int * p; p = new(int)(10);
int * p; p = new int[8]; // 分配 8 个元素的整数数组
```

## delete

```c++
int * p; p = new int; *p = 10; delete p;
int * p; p = new int[8]; delete[] p;
// not delete p[ ]!
```

```c++
int *p, *q;
q = ( int* )malloc( sizeof(int) );
p = q;

free( p ); 
p = NULL; // q is dangling pointer
```



## storage leak

```c++
void f()
{ 
    int * p = new int; 
    *p = 10; 
}
```



# Reference

```c++
int a; int & ref = a;
```



```c++
#include <iostream>
using namespace std;
int main(){
    int a;
    int & ref = a;
    a = 5;
    cout << "a: " << a << endl; cout << "ref: " << ref << endl;
    ref = 8;
    cout << "a: " << a << endl; cout << "ref: " << ref << endl;
    return 0;
}
```

### call by reference

```c++
void Swap( int & x, int & y )
{
	int t; t = x; x = y; y = t; return;
}
```

```c++
int main(){
	int a = 10, b = 20; 
    Swap( a, b ); 
    return 0;
}
```

### constant reference

```c++
int & Inc( int & dest, const int & alpha );

int & Inc( int & dest, const int & alpha )
{
	dest += alpha; 
    return dest;
}

int main()
{
	int a = 10, b = 20, c; 
    Inc( a, b ); 
    c = Inc(a, b)++; 
    return 0;
}
```

# Function Pointer

```c++
typedef void * ADT; typedef const void * CADT;
```

data type ()()

```c++
char * ( * as_string )( ADT object );
```

```c++
char * DoTransformObjectIntoString( ADT object )
{ return PtTransformIntoString( (PPOINT)object ); }
as_string = DoTransformObjectIntoString;
```

```c++
char * returned_value;
PPOINT pt = PtCreate( 10, 20 );
as_string = DoTransformObjectIntoString;
returned_value = as_string( (ADT)pt );
```

example: qsort

```c++
void qsort( void * base, unsigned int number_of_elements,
unsigned int size_of_elements,
int ( * compare )( const void *, const void * ) );
```

```c++
#include <iostream>
#include <cstdlib>
using namespace std;
#include "arrmanip.h"
#define NUMBER_OF_ELEMENTS 8
int DoCompareObject( const void * e1, const void * e2 );

int main()
{
    int a[NUMBER_OF_ELEMENTS];
    GenerateIntegers( a, NUMBER_OF_ELEMENTS );
    cout << "Array generated at random as follows: \n";
    PrintIntegers( a, NUMBER_OF_ELEMENTS );
    qsort( a, NUMBER_OF_ELEMENTS, sizeof(int), DoCompareObject );
    cout << "After sorted: \n";
    PrintIntegers( a, NUMBER_OF_ELEMENTS );
    return 0;
}
int DoCompareObject( const void * e1, const void * e2 )
{
    return CompareInteger( *(const int *)e1, *(const int *)e2 );
}
```

