---
title: JSON Basic
date: 2020-4-4
tags: 
	- JSON
	- Big Data
categories: 
	- Computer Science
	- Big Data
	- JSON
---

# Basic JSON

### Data Structure:

+ key / value pair

```json
var studentData = {
    "student_id": 1234567,
    "name": "John Smith",
    "enrollment_date": "1/1/2020",
    "location": "Tandon School, NYC",
    "course_nums":[6024, 7865, 5512, 8194]
};
```

### Data type:

Json Arrays

Srings

+ 0 or more Unicode characters
+ double quotes
+ backslash escapement

Numbers

+ Integer
+ real
+ no Ox, Hex
+ no NaN or Indfinity - use null



### Object in json

```json
{
    "student_id": 1234567,
    "name": "John Smith"
}
```

It can contain many key/value pairs.



which is the same as javaScript

```javascript
student_id = 1234567,
name = "John Smith"
```

JavaScript

```JSON
var sites = [
    {"student_id": 1234567, "name": "John Smith"}, 
    {"student_id": 1234568, "name": "Steven Bob"}, 
    {"student_id": 1234569, "name": "John Nash"}
];

# call
sites[0].name;

# revise
sites[0].name="Alex Jack";
```



Object Example

```json
var myObj, x;
myObj = { "name":"runoob", "alexa":10000, "site":null };

# call
x = myObj.name;
# or
x = myObj["name"];

# for loop
for (x in myObj) {
    document.getElementById("demo").innerHTML += x + "<br>";
}
```



Nested objects

```json
myObj = {
    "name":"runoob",
    "alexa":10000,
    "sites": {
        "site1":"www.runoob.com",
        "site2":"m.runoob.com",
        "site3":"c.runoob.com"
    }
}

```

### Delete

```json
# Delete object
delete myObj.sites.site1;
# or
delete myObj.sites["site1"]
```

delete just change the data to unsigned, the array length will not be changed. The array will become sparser.

### Array

```json
[ "Google", "Runoob", "Taobao" ]

# for in loop
for (i in myObj.sites) {
    x += myObj.sites[i] + "<br>";
}

# for loop
for (i = 0; i < myObj.sites.length; i++) {
    x += myObj.sites[i] + "<br>";
}
```

### Parse

`JSON.parse()` change the string data on the server to JavaScript Object.

```json
# receive the data from server like these:
{ "name":"runoob", "alexa":10000, "site":"www.runoob.com" }

# convert it to JavaScript object
var obj = JSON.parse('{ "name":"runoob", "alexa":10000, "site":"www.runoob.com" }');

```

parse example

```json
# Text Example
var xmlhttp = new XMLHttpRequest();
xmlhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
        myObj = JSON.parse(this.responseText);
        document.getElementById("demo").innerHTML = myObj.name;
    }
};
xmlhttp.open("GET", "/try/ajax/json_demo.txt", true);
xmlhttp.send();

# Array Example
var xmlhttp = new XMLHttpRequest();
xmlhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
        myArr = JSON.parse(this.responseText);
        document.getElementById("demo").innerHTML = myArr[1];
    }
};
xmlhttp.open("GET", "/try/ajax/json_demo_array.txt", true);
xmlhttp.send();

# if there is a function in data, convert the function to string
var text = '{ "name":"Runoob", "alexa":"function () {return 10000;}", "site":"www.runoob.com"}';
var obj = JSON.parse(text);
obj.alexa = eval("(" + obj.alexa + ")");
 
document.getElementById("demo").innerHTML = obj.name + " Alexa 排名：" + obj.alexa();
```



### JSON.stringify()

convert JavaScript object into strings

```json
var obj = { "name":"runoob", "alexa":10000, "site":"www.runoob.com"};
var myJSON = JSON.stringify(obj);
document.getElementById("demo").innerHTML = myJSON;
```



