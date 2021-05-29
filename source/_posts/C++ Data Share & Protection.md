---
title: C++ Data Share & Protection
date: 2019-2-1
tags: 
	- C++
	- MOOC
categories: 
	- Computer Science
	- Programming
	- C++
---
This note contains basic knowledge of data share and protection in C++ including.

# Scope

+ classification

  function prototype scope

  ```c++
  double area(double radius)
  ```

  local scope

  ```c++
  void fun(int a) {
     int b = a;
     cin >> b;
     if (b > 0) {
       int c;
       ......
     }
  }
  ```

  global scope 

  file scope

+ visibility

  ```c++
  #include 
  using namespace std;
   
  int i;	//global variable，file scope
  int main() { 
       i = 5; //i is a global variable (external)
       {
           int i; //local scope (inner)
           i = 7;
           cout << "i = " << i << endl;//output 7
        }
        cout << “i = ” << i << endl;//output 5
        return 0;
  }
  ```

# Lifetime

+ static lifetime
+ local lifetime

```c++
#include<iostream>
using namespace std;

int i = 1; // i is global variable with static lifetime and global visibility.
void other() {
    static int a = 2;
    static int b;
    // a,b are static local variables, with static lifetime and local visibility
    // a,b will be initialized only at the first time
    int c = 10; // c is a local variable with local lifetime and local visibility
    //c will be initialized every time the "other function" is about to run.
    a += 2; i += 32; c += 5;
    cout<<"---OTHER---\n";
    cout<<" i: "<<i<<" a: "<<a<<" b: "<<b<<" c: "<<c<<endl;
    b = a;
}

int main() {
    static int a;//a is static local variable with static lifetime and local visibility
    int b = -10; // b, c are local variables with local lifetime
    int c = 0;
    cout << "---MAIN---\n";
    cout<<" i: "<<i<<" a: "<<a<<" b: "<<b<<" c: "<<c<<endl;
    c += 8; other();
    cout<<"---MAIN---\n";
    cout<<" i: "<<i<<" a: "<<a<<" b: "<<b<<" c: "<<c<<endl;

    i += 10; other();
    return 0;
}
```

The result is below:

```c++
---MAIN---
i: 1 a: 0 b: -10 c: 0
---OTHER---
i: 33 a: 4 b: 0 c: 15
---MAIN---
i: 33 a: 0 b: -10 c: 8
---OTHER---
i: 75 a: 6 b: 4 c: 15
```

# Friend Function & Class

## friend function

 ```c++
#include <iostream>
#include <cmath>
using namespace std;
class Point { //Point类声明
public: //外部接口
	Point(int x=0, int y=0) : x(x), y(y) { }
	int getX() { return x; }
	int getY() { return y; }
	friend float dist(Point &a, Point &b);
private: //私有数据成员
	int x, y;
};

float dist(Point& a, Point& b) {
	double x = a.x - b.x;
	double y = a.y - b.y;
	return static_cast<float>(sqrt(x * x + y * y));
}
int main() {
	Point p1(1, 1), p2(4, 5);
	cout <<"The distance is: ";
	cout << dist(p1, p2) << endl;
	return 0;
}
 ```

## friend class

```c++
class A {
	friend class B;
public:
	void display() {
	cout << x << endl;
}
private:
	int x;
}

class B {
public:
	void set(int i);
	void display();
private:
	A a;
};

void B::set(int i) {
	a.x=i;
}

void B::display() {
	a.display();
};
```

+ tips:
  + The friend function and class is a one-direction relationship.

# Shared Data Protection

## const object

```c++
class A{
public:
    A(int i,int j) {x=i; y=j;}
                     ...
private:
    int x,y;
};
A const a(3,4); 
```

## const function

```c++
#include<iostream>
using namespace std;

class R {
public:
	R(int r1, int r2) : r1(r1), r2(r2) { }
	void print();
	void print() const;
private:
	int r1, r2;
};

void R::print() {
	cout << r1 << ":" << r2 << endl;
}

void R::print() const {
	cout << r1 << ";" << r2 << endl;
}

int main() {
	R a(5,4);
	a.print(); //调用void print()
	const R b(20,52); 
	b.print(); //调用void print() const
    return 0;
}
```

## const member

```c++
#include <iostream>
using namespace std;
class A {
public:
    A(int i);
    void print();
private:
    const int a;
    static const int b;
};
const int A::b=10;
A::A(int i) : a(i) { }
void A::print() {
	cout << a << ":" << b <<endl;
}

int main() {
//建立对象a和b，并以100和0作为初值，分别调用构造函数，
//通过构造函数的初始化列表给对象的常数据成员赋初值
	A a1(100), a2(0);
	a1.print();
	a2.print();
	return 0;
}
```

## const reference

```c++
#include <iostream>
#include <cmath>
using namespace std;
class Point{
public:          
    Point(int x = 0, int y = 0)
	: x(x), y(y) { }
    int getX() { return x; }
    int getY() { return y; }
    friend float dist(const Point &p1,const Point &p2);
private:
    int x, y;
};
float dist(const Point &p1, const Point &p2) {
    double x = p1.x - p2.x; 
    double y = p1.y - p2.y;
    return static_cast<float>(sqrt(x*x+y*y));
}
int main(){
    const Point myp1(1, 1), myp2(4, 5);    
    cout << "The distance is: ";
    cout << dist(myp1, myp2) << endl;
    return 0;
}
```

