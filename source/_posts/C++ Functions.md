---
title: C++ Functions
date: 2019-1-28
tags: 
	- C++
	- MOOC
categories: 
	- Computer Science
	- Programming
	- C++
---
This note contains basic knowledge of functions in C++ including definition, invocation, overloading and so on.

## definition of functions
syntax:

type identifier *Name*(**formal parameter**)  
{  
　　***statements***  
　　return  
}

tips:

+ If the type identifier is `void`, there is **no need to include a return statement** in the function body.

## invocation of functions
### 1\. declaration prototype

syntax:

function prototype: type identifier *Name*(**formal parameter with type notifications**)

tips:

+ if a function is defined after the invocation point, its prototype must be declared before invocation.
+ if a function is defined before the invocation point, there is no need to declare the prototype.

### 2\. invocation

syntax:

*Name*(**argument**)

> **3\.1\. write a function to compute the n power of x**
>
	#include <iostream>  
	using namespace std
	double power(double x, int n){
		dowble val = 1.0;
		while(n--)
			val *= x;
		return val;
	}
	int main(){
		double pow;
		pow = power(5, 2):
		cout << "5 to the power 2 is " << pow << endl;
	return 0;
	}




> **3\.2\. write a function to converse an input number from binary to decimal**
> 
	#include <iostream>
	using namespace std;
>
	double power(double x, int n);
>	
	int main() {
		int value = 0;		
		cout << "Enter an 8 bit binary number: ";
		for (int i = 7; i >= 0; i--) {
			char ch;
			cin >> ch;
			if (ch == '1')
				value += static_cast<int>(power(2, i));
		}
		cout << "Decimal value is " << value << endl;
		return 0;
	}
>	
	//compute the n power of x
	double power (double x, int n) {
		double val = 1.0;
		while (n--)
			val *= x;
		return val;
	}

>**3\.3\. write a function to compute the value of Pi**
>
	#include <iostream>
	using namespace std;
>	
	double arctan(double x) {
		double sqr = x * x;
		double e = x;
		double r = 0;
		int i = 1;
		while (e / i > 1e-15) {
			double f = e / i;
			r = (i % 4 == 1) ? r + f : r - f;
			e = e * sqr;
			i += 2;
		}
		return r;
	}
>
	int main(){
		double a = 16.0 * arctan(1/5.0);
		double b = 4.0 * arctan(1/239.0);
		cout << "Pi = " << a - b << endl;
		return 0;
	}

>**3\.4\. find all the number from 11 to 999 of which the 1, 2 and 3 power are all palindrome numbers**
>
	#include <iostream>
	using namespace std;
>	
	//determin whether n is a palindrome number
	bool symm(unsigned n) {
		unsigned i = n;
		unsigned m = 0;
		while (i > 0) {
			m = m * 10 + i % 10;
			i /= 10;
		}
		return m == n;
	}
>	
	int main() {
		for (unsigned m = 11; m < 1000; m++)
			if (symm(m) && symm(m * m) && symm(m * m * m)) {
				cout << "m = " << m;
				cout << "m * m = " << m * m;
				cout << "m * m * m = " << m * m * m << endl;
			}
		return 0;
	}

>**3\.5\. write a function to compute a piecewise function**
>
	#include <iostream>
	#include <cmath>
	using namespace std;
>	
	const double TINY_VALUE = 1e-10;
>	
	double tsin(double x) {
		double g = 0;
		double t = x;
		int n = 1;
		do {
			g += t;
			n++;
			t = -t * x * x / (2 * n - 1) / (2 * n - 2);
		} while (fabs(t) >= TINY_VALUE); 
		return g;
	}
>	
	int main() {
		double k, r, s;
		cout << "r = ";
		cin >> r;
		cout << "s = ";
		cin >> s;
		if (r * r <= s * s)
			k = sqrt(tsin(r) * tsin(r) + tsin(s) * tsin(s));
		else
			k = tsin(r * s) / 2;
		cout << k << endl;
		return 0;
	}

Random Function


## nesting invocation of functions
nesting: invoke another function in a function.

>**3\.7\. compute the sum of square of the two input integer**
> 
	#include <iostream>
	using namespace std;
>	
	int fun2(int m) {
		return m * m;
	}
>	
	int fun1(int x,int y) {
		return fun2(x) + fun2(y);
	}
>	
	int main() {
		int a, b;
		cout << "Please enter two integers(a and b): ";
		cin >> a >> b;
		cout << "The sum of square of a and b: " << fun1(a, b) << endl;
		return 0;
	}

## recursive invocation of functions
recursive: invoke itself in a function

>**3\.8\. compute the factorial of n**
>
	#include <iostream>
	using namespace std;
>
	unsigned fac(unsigned n) {
		unsigned f;
		if (n == 0)
			f = 1;
		else
			f = fac(n - 1) * n;
		return f;
	}
>	
	int main() {
		unsigned n;
		cout << "Enter a positive integer: ";
		cin >> n;
		unsigned y = fac(n);
		cout << n << "! = " << y << endl;
		return 0;
	}


>
**3\.9\. compute the number of combinations of k individuals selected from n individuals**
>
	#include <iostream>
	using namespace std;
>
	int comm(int n, int k) {
		if (k > n)
			return 0;
		else if (n == k || k == 0)
			return 1;
		else
			return comm(n - 1, k) + comm(n - 1, k - 1);
	}
>	
	int main() {
		int n, k;
		cout << "Please enter two integers n and k: ";
		cin >> n >> k;
		cout << "C(n, k) = " << comm(n, k) << endl;
		return 0;
	}

**3\.10\. Solution of Hanoi Tower**
>
	#include <iostream>
	using namespace std;
>	
	//move the top plate which is on the src to the dest
	void move(char src, char dest) { 
		cout << src << " --> " << dest << endl;
	}
>	
	//move n plates which is on the src to the dest via medium
	void hanoi(int n, char src, char medium, char dest) {
		if (n == 1)
			move(src, dest);
		else {
			hanoi(n - 1, src, dest, medium);
			move(src, dest);
			hanoi(n - 1, medium, src, dest);
		}
	}
>	
	int main() {
		int m;
		cout << "Enter the number of diskes: ";
		cin >> m;
		cout << "the steps to moving " << m << " diskes:" << endl;
		hanoi(m,'A','B','C');
		return 0;
	}


## parameter passing
### 1\. reference passing
syntax:

type identifier & *Name*

>
	int i,j;
	int &ri = i;
	j = 10;
	ri = j

> **swap two different numbers**
>
	#include <iostream>
	using namespace std;	
	void swap(int & a, int & b) {
		int t = a;
		a = b;
		b = t;
	}
>	
	int main() {
		int x = 5, y = 10;
		cout << "x = " << x << " y = " << y << endl;
		swap(x, y);
		cout << "x = " << x << " y = " << y << endl;
		return 0;
	}

## variable parameter function

initializer_list



## inline function
syntax:

**inline** type identifier *Name*

tips:

+ inline function cannot contain the switch and if statement.

**compute the area of a circle**
	
	#include <iostream>
	using namespace std;

	const double PI = 3.14159265358979;
	inline double calArea(double radius) {
		return PI * radius * radius;
	}
	
	int main() {
		double r = 3.0;	//r is the radius
		//it will be replaced by the statements in calArea function during compiling.
		double area	= calArea(r);
		cout << area << endl;
		return 0;
	}

## constexpr function
syntax:

**constexpr** type identifier *Name*

tips:

+ There is only one return statement in a constexpr function, in which the return value should be a constant.  

example:

	constexpr int get_size(){
		return 20;
	}

	constexpr int foo = get_size();

## functions with default parameter values
syntax:

type identifier *Name*(parameter1, **parameter2 = value**, ...)

tips:

+ The parameter with default values should be ordered by the right side when defined.
+ The default values should be defined in the front one: function definition or publication.  


**compute the volume of some cuboid boxes**
	
	#include <iostream>
	#include <iomanip>
	using namespace std;
	
	int getVolume(int length, int width = 2, int height = 3);
	
	int main() {
		const int X = 10, Y = 12, Z = 15;
		cout << "Some box data is " ;
		cout << getVolume(X, Y, Z) << endl;
		cout << "Some box data is " ;
		cout << getVolume(X, Y) << endl;
		cout << "Some box data is " ;
		cout << getVolume(X) << endl;
		return 0;
	}
	
	int getVolume(int length, int width/* = 2 */, int height/* = 3 */) {
		cout << setw(5) << length << setw(5) << width << setw(5) << height << '\t';
		return length * width * height;
	}

## overloading of functions
syntax:

**type identifier1** *Name*(type identifier1 *parameter1*...)  
**type identifier2** *Name*(type identifier2 *parameter2*, type identifier3 *parameter3*...)

tips:

+ The number of parameters can be different.
+ Overloading of functions is determined by the type identifier, rather than return values or expression in the functions.

**computer the sum of square of two numbers**

	#include <iostream>
	using namespace std;
	
	int sumOfSquare(int a, int b) {
		return a * a + b * b;
	}
	
	double sumOfSquare(double a, double b) {
		return a * a + b * b;
	}
	
	int main() {
		int m, n;
		cout << "Enter two integer: ";
		cin >> m >> n;
		cout << "Their sum of square: " << sumOfSquare(m, n) << endl;
	
		double x, y;
		cout << "Enter two real number: ";
		cin >> x >> y;
		cout << "Their sum of square: " << sumOfSquare(x, y) << endl;
	
		return 0;
	}

## system function
The system functions are usually defined in the head files:

+ mathematics: `<cmath>`

**compute the sine, cosine and tangent function value of a input angle.

	#include <iostream>
	#include <cmath>
	using namespace std;
	
	const double PI = 3.14159265358979;	
	int main() {
		double angle;
		cout << "Please enter an angle: ";
		cin >> angle;
		double radian = angle * PI / 180;
		cout << "sin(" << angle << ") = " << sin(radian) <<endl;
		cout << "cos(" << angle << ") = " << cos(radian) <<endl;
		cout << "tan(" << angle << ") = " << tan(radian) <<endl;
		return 0;
	}
