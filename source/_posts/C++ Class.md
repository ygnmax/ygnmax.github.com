---
title: C++ Class
date: 2019-2-1
tags: 
	- C++
	- MOOC
categories: 
	- Computer Science
	- Programming
	- C++
---
This note contains basic knowledge of class and objects in C++ including characteristics, definition, constructor, destructor, sturcture, union and enumeration class.

## characteristics of object-oriented programming
### 1\. abstract

### 2\. encapsulation

### 3\. inheritance

### 4\. polymorphism

## definition of class and object
### 1\. class
syntax:

+ class *Name*{  
　　public:  
　　　　*public member* (which is also external interface)  
　　private:  
　　　　*private member*  
　　protected:  
　　　　*protected member*  
  }

tips:

+ Members can be provided with default values when defined. 
+ The members without default values will be initialized.

### 2\. object
syntax:

1\. definition

+ class Name *object Name*;

2\. access public members

+ object Name.*member Name*
 

### 3\. member function in class
syntax:
	
+ class Name::*Name*{

tips:

+ declare the function prototype in the class definition
+ the function body can be defined outside the class  with class name to qualify.
+ the function can be defined in the class as an inline function.

> define a class of clock.
	#include <iostream>	
	using namespace std;
	
	class Clock	{
	public:
		void setTime(int newH = 0, int newM = 0, int newS = 0);
		void showTime();
	private:
		int hour, minute, second;
	};
	
	void Clock::setTime(int newH, int newM, int newS) {
		hour = newH;
		minute = newM;
		second = newS;
	}
	
	inline void Clock::showTime() {
		cout << hour << ":" << minute << ":" << second << endl;
	}
	
	int main() {
		Clock myClock;
		cout << "First time set and output:" << endl;
		myClock.setTime();
		myClock.showTime();
		cout << "Second time set and output:" << endl;
		myClock.setTime(8, 30, 30);
		myClock.showTime();
		return 0;
	}

## constructor
syntax:

tips:

	class Clock	{
	public:	
		Clock() =default; //default constructor
   		Clock(int newH, int newM, int newS); //constructor
	private:
		int hour, minute, second;
	};


> define a class of clock with a constructor.

	#include <iostream>	
	using namespace std;
	
	class Clock	{
	public:
		Clock(int newH, int newM, int newS);
		void setTime(int newH, int newM, int newS);
		void showTime();
	private:
		int hour, minute, second;
	};

	Clock::Clock(int newH, int newM, int newS):
	hour(newH), minute(newM), second(newS){
	}

	void Clock::setTime(int newH, int newM, int newS) {
		hour = newH;
		minute = newM;
		second = newS;
	}
	
	inline void Clock::showTime() {
		cout << hour << ":" << minute << ":" << second << endl;
	}
	
	int main() {
		Clock c(0,0,0);
		c.showTime();
		return 0;
	}

> define a class of clock with a constructor and a default constructor.

	#include <iostream>	
	using namespace std;
	
	class Clock	{
	public:
		Clock(int newH, int newM, int newS);
		Clock();
		void setTime(int newH, int newM, int newS);
		void showTime();
	private:
		int hour, minute, second;
	};
	
	Clock::Clock():hour(0), minute(0), second(0){
	}

	Clock::Clock(int newH, int newM, int newS):
	hour(newH), minute(newM), second(newS){
	}

	void Clock::setTime(int newH, int newM, int newS) {
		hour = newH;
		minute = newM;
		second = newS;
	}
	
	inline void Clock::showTime() {
		cout << hour << ":" << minute << ":" << second << endl;
	}
	
	int main() {
		Clock c(8,10,0);
		Clock c2;
		c.showTime();
		c2.showTime();
		return 0;
	}

### delegating constructors
syntax:

tips:
+ delegating constructors help to maintain the constancy of codes.

		// 2 constructors
		Clock(int newH, int newM, int newS): 
		hour(newH), minute(newM), second(newS){
		}
		Clock::Clock(): hour(0),minute(0),second(0) { }
	
		// delegating constructors
		Clock(int newH, int newM, int newS):  
		hour(newH),minute(newM),  second(newS){
		}
		Clock(): Clock(0, 0, 0) { 
		}

### copy constructor
syntax:

1\. create

+ class *class Name*{  
  　　public:  
  　　*class Name*(parameter);  
  　　*class Name*(const *class Name* & *object Name*);  
  }
+ *class Name*::*class Name*(const *class Name* & *object Name*){  
}

2\. delete

+ *class Name*(const *class Name* & *object Name*) = delete

		class Point {
			public:
			    Point(int xx=0, int yy=0) { x = xx; y = yy; }  //constructor, inline
			    Point(const Point& p) =delete; //don't create default copy constructor
			private:
			    int x, y;
		};

tips:
 
+ 3 conditions that copy constructors will be invoked:
	+ 1 
	+ 2
	+ 3


### destructor
syntax:

~*class Name*

	#include <iostream>
	using namespace std;
	class Point{
		public:
			Point(int xx, int yy);
			~Point();
		private:
			int x, y;
	};
	
	Point::Point(int xx, int yy){
		x = xx;
		y = yy;
	}
	Point::~Point(){
	}

tips:
 
+ The destructor will be invoked when the object disappears.

## combination of class
syntax:

+ *class Name*::*class Name*(parameters of members in the object, parameters of members in this class) : object1(parameter), object2(parameter),...{  
  　　function body  
  }

tips:

+ the order of initialization: the member which is declared first will be constructed first.

> create a line class using point class

	#include <iostream>
	#include <cmath>
	using namespace std;
	
	class Point {
	public:
		Point(int xx = 0, int yy = 0) {
			x = xx;
			y = yy;
		}
		Point(Point &p);
		int getX() { return x; }
		int getY() { return y; }
	private:
		int x, y;
	};
	
	Point::Point(Point &p) {
		x = p.x;
		y = p.y;
		cout << "Calling the copy constructor of Point" << endl;
	}
	
	//combination of class
	class Line {
	public:
		Line(Point xp1, Point xp2);
		Line(Line &l);
		double getLen() { return len; }
	private:
		Point p1, p2;
		double len;
	};
	
	//constructor of the combination class
	Line::Line(Point xp1, Point xp2) : p1(xp1), p2(xp2) {
		cout << "Calling constructor of Line" << endl;
		double x = static_cast<double>(p1.getX() - p2.getX());
		double y = static_cast<double>(p1.getY() - p2.getY());
		len = sqrt(x * x + y * y);
	}
	
	//copy constructor of the combination class
	Line::Line (Line &l): p1(l.p1), p2(l.p2) {
		cout << "Calling the copy constructor of Line" << endl;
		len = l.len;
	}
	
	int main() {
		Point myp1(1, 1), myp2(4, 5);	//build Point objects
		Line line(myp1, myp2);	//build Line objects
		Line line2(line);	//use copy constructor of the combination class to build a new object
		cout << "The length of the line is: ";
		cout << line.getLen() << endl;
		cout << "The length of the line2 is: ";
		cout << line2.getLen() << endl;
		return 0;
	}

### preceding reference declaration
tips:

+ declare a class name before define another class.
	
		class B; 
		class A {
		public:
			void f(B b);
		};
		
		class B {
		public:
		  void g(A a);
		};

+ cannot be involved with details of this declared class:

		class Fred;
		class Barney {
		   Fred x;
		};
		
		class Fred {
		   Barney y;
		};

## UML introduction
basic elements
 
+ Things
+ Relationships
+ Diagrams

## Structures
syntax:  

+ struct *Name*{  
　　*public members*  
  protected:  
　　*protected members*  
  private:  
　　*private members*  
  };

tips:

+ default members in structures is public, and can be data members or function members.

> Students' basic information

	#include <iostream>
	#include <iomanip>
	#include <string>
	using namespace std;
	
	struct Student {
		int num;	
		string name;
		char sex;
		int age;
	};
	
	int main() {
		Student stu = { 97001, "Lin Lin", 'F', 19 };
		cout << "Num:  " << stu.num << endl;
		cout << "Name: " << stu.name << endl;
		cout << "Sex:  " << stu.sex << endl;
		cout << "Age:  " << stu.age << endl;
		return 0;
	}

## unions
syntax:

+ union *Name*{  
　　*public members*  
  protected:  
　　*protected members*  
  private:  
　　*private members*  
  };

tips:

+ members in unions share the storage space, therefore there is only one effective member at the same time.
+ The storage space is determined by the largest space demand members.

> Student's mark

	union Mark{
		char grade;	//class grade: A, B, C, D, F
		bool pass;	//pass or fail
		int percent;	//hundred mark
	};

### anonymous unions

	union {
	  int i;
	  float f;
	}

tips:
 
+ i and f will share the storage space.

> Student's mark information

	#include <string>
	#include <iostream>
	using namespace std;
	
	class ExamInfo {
	public:
		ExamInfo(string name, char grade)
			: name(name), mode(GRADE), grade(grade) { }
		ExamInfo(string name, bool pass)
			: name(name), mode(PASS), pass(pass) { }
		ExamInfo(string name, int percent)
			: name(name), mode(PERCENTAGE), percent(percent) { }
		void show();
	
	private:
		string name;
		enum {
			GRADE,
			PASS,
			PERCENTAGE
		} mode;
		union {
			char grade;
			bool pass;
			int percent;
		};
	};
	
	void ExamInfo::show() {
		cout << name << ": ";
		switch (mode) {
		case GRADE:
			cout << grade;
			break;
		case PASS:
			cout << (pass ? "PASS" : "FAIL");
			break;
		case PERCENTAGE:
			cout << percent;
			break;
		}
		cout << endl;
	}
	
	int main() {
		ExamInfo course1("English", 'B');
		ExamInfo course2("Calculus", true);
		ExamInfo course3("C++ Programming", 85);
		course1.show();
		course2.show();
		course3.show();
		return 0;
	}

## enumeration class
syntax:

enum class *Name*: ***Type name***{ enumeration list };

	enum class Type {General, Light, Medium, Heavy};
	enum class Type: char {General, Light, Medium, Heavy};
	enum class Category {General=1, Pistol, MachineGun, Cannon};

*Name*::enumeration element
	
	Type::General

tips:

+ the Type name can be defined as `int`, `char`, `double` etc. The default is `int`.
+ Strong scope
+ Strict

		#include<iostream>
		using namespace std;

		enum class Side{ Right, Left };
		enum class Thing{ Wrong, Right };
		int main(){
			Side s = Side::Right;		
			Thing w = Thing::Wrong;
			cout << (s == w) << endl;
			return 0;
		}

