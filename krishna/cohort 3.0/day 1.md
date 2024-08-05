# Javascript - The basics

**Web development**

Web development involves writing a lot of HTML, CSS and JS code.

Historically (and even today to some extend), browsers could only understand HTML, CSS and JS

Any website that you see, is a bunch of HTML, CSS and JS files along with some assets (images, videos etc)

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F7ec5034a-be7d-4e01-90e8-c82713918f55%2FScreenshot_2024-08-04_at_5.56.48_PM.png?table=block&id=82c27591-39d6-4982-9c63-55cbdd90fa38&cache=v2)

### 

[](https://projects.100xdevs.com/tracks/javascript-1/Javascript-101-2#3174957cdd82480b889f948fa4b15b7a "Facts/Callouts")Facts/Callouts

1. React, NextJS are `frameworks` . They compile down to HTML, CSS, JS in the end. That is what your browser understands.

2. When you run your C++ code on `leetcode` , it does not run on your browser/machine. It runs somewhere else. Your browser can’t (almost) compile and run C++ code.

3. If someone asks — What all languages can your browser interpret, the answer is HTML, CSS, JS and WebAssembly. It can, technically, run C++/Rust code that is compiled down to Wasm

#### 

[](https://projects.100xdevs.com/tracks/javascript-1/Javascript-101-2#48cd5549a594419ca41bf538dedbd1be "Before we proceed, do one of the following -")Before we proceed, do one of the following -

1. Create an account on replit

2. Install Node.js locally

3. Keep your browser console open for testing locally




# Properties of JS

Every language comes with it’s unique set of features.

Javascript has the following -

## 

[](https://projects.100xdevs.com/tracks/javascript-1/Javascript-101-3#079d4a0db47e449ab33d642aea6fae45 "1. Interpreted")1. Interpreted

JavaScript is an interpreted language, meaning it's executed line-by-line at runtime by the JavaScript engine in the browser or server environment, rather than being compiled into machine code beforehand.

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F3e158041-21f9-4456-b8da-fb7efc1f1c72%2FScreenshot_2024-08-04_at_6.04.48_PM.png?table=block&id=cde43870-90f3-4819-b559-5a1e3a12cc85&cache=v2)

**Upsides -**

1. There is one less step to do before running your code

**Downsides -**

1. Performance Overhead:

2. More prone to runtime errors

## 

[](https://projects.100xdevs.com/tracks/javascript-1/Javascript-101-3#52210a581fa742a5a0f85a52774c560c "2. Dynamically Typed")2. Dynamically Typed

Variables in JavaScript are not bound to a specific data type. Types are determined at runtime and can change as the program executes

#### 



```javascript
#include <iostream>

int main() { 
  int a = 1;
  a = "hello";
  a = true;
}
```

#### 

[](https://projects.100xdevs.com/tracks/javascript-1/Javascript-101-3#c7878a6267f440679865a5ef561d49a7 "JS Code (will compile)")JS Code (will compile)

```javascript

var a = 1;
a = "harkirat";
a = true;

console.log(a)
```

## 

[](https://projects.100xdevs.com/tracks/javascript-1/Javascript-101-3#f4dc81f30d4940b2aa53565da916f8fd "3. Single threaded")3. Single threaded

JavaScript executes code in a single-threaded environment, meaning it processes one task at a time. We will dive deeper into this next week.

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Fabb89c43-81b7-4a96-afb6-866843329579%2FScreenshot_2024-08-04_at_6.12.41_PM.png?table=block&id=ec373070-dd6a-4861-85a5-8a2dc42fb422&cache=v2)

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F524dfd92-1f94-472b-ade8-e988608116f7%2FScreenshot_2024-08-04_at_6.13.11_PM.png?table=block&id=3e7388e9-5708-4bfe-9d7f-8c32cc680408&cache=v2)

## 

[](https://projects.100xdevs.com/tracks/javascript-1/Javascript-101-3#ba97ae4319774bb0bf84a93e4fffd8ee "4. Garbage collected")4. Garbage collected

JavaScript automatically manages memory allocation and deallocation through garbage collection, which helps prevent memory leaks by automatically reclaiming memory used by objects no longer in use.

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2Fec5e527b-de5a-4718-b3b2-d5c4a95f279c%2FScreenshot_2024-08-04_at_6.16.07_PM.png?table=block&id=1d3a4740-c417-46c4-abce-e27475bc9d86&cache=v2)

### 

[](https://projects.100xdevs.com/tracks/javascript-1/Javascript-101-3#c15f510507304bbfa076a527c0834967 "Conclusion")Conclusion

Is JS a good language?

Yes and no. It is beginner friendly, but has a lot of performance overhead. **Bun** is trying to solve for a lot of this, but there’s a long way to go before JS can compete with languages like C++/Rust






#### **Variables**

Variables are used to store data. In JavaScript, you declare variables using `var`, `let`, or `const`.

```javascript
let name = "John";     // Variable that can be reassigned
const age = 30;        // Constant variable that cannot be reassigned
var isStudent = true;  // Older way to declare variables, function-scoped
```

Assignment

Create a variable for each of the following: your favorite color, your height in centimeters, and whether you like pizza. Use appropriate variable declarations (`let`, `const`, or `var`). Try logging it using `console.log`

#### 

[](https://projects.100xdevs.com/tracks/javascript-1/Javascript-101-4#cd34f1283f4a4b40a0512089e8d8be52 "2. Data types")2. Data types

```javascript
let number = 42;             // Number
let string = "Hello World";  // String
let isActive = false;        // Boolean
let numbers = [1, 2, 3];     // Array
```

#### 

[](https://projects.100xdevs.com/tracks/javascript-1/Javascript-101-4#fe43bfb4f8414d2285ab1f1f99768f36 "3. Operators")3. **Operators**

```javascript
let sum = 10 + 5;          // Arithmetic operator
let isEqual = (10 === 10); // Comparison operator
let isTrue = (true && false); // Logical operator
```

#### 

[](https://projects.100xdevs.com/tracks/javascript-1/Javascript-101-4#1c0625f2ce304242bb1e34735a1308f3 "4. Functions")4. **Functions**

```javascript
// Function declaration
function greet(name) {
    return "Hello, " + name;
}

// Function call
let message = greet("John"); // "Hello, John"
```

Assignment #1

Write a function `sum` that finds the sum of two numbers. Side quest - Try passing in a string instead of a number and see what happens?

Assignment #2

Write a function called `canVote` that returns true or false if the `age` of a user is > 18

#### 

[](https://projects.100xdevs.com/tracks/javascript-1/Javascript-101-4#c54d85778a6f4f419f486cd61693bc64 "5. If/Else")5. If/Else

```javascript
if (age >= 18) {
    console.log("You are an adult.");
} else {
    console.log("You are a minor.");
}
```

Assignment

Write an if/else statement that checks if a number is even or odd. If it's even, print "The number is even." Otherwise, print "The number is odd."

#### 

[](https://projects.100xdevs.com/tracks/javascript-1/Javascript-101-4#b6270110b2704512aeb3d061f89389e8 "6. Loops")6. Loops

```javascript
// For loop
for (let i = 0; i < 5; i++) {
    console.log(i); // Outputs 0 to 4
}

// While loop
let j = 0;
while (j < 5) {
    console.log(j); // Outputs 0 to 4
    j++;
}
```

Assignment

Write a function called sum that finds the `sum` from 1 to a num





# Complex types

### 

[](https://projects.100xdevs.com/tracks/javascript-1/Javascript-101-5#a327d04a41a64efea1663b549313dbd1 "Objects")Objects

An object in JavaScript is a collection of `key-value pairs`, where each `key` is a string and each `value` can be any valid JavaScript data type, including another object.

![notion image](https://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F085e8ad8-528e-47d7-8922-a23dc4016453%2F3282ffa1-783b-478a-87d3-3bba79f09d15%2FScreenshot_2024-08-04_at_6.43.02_PM.png?table=block&id=e3a09d36-b901-4ea0-8d6f-903ab5851304&cache=v2)

```javascript
let user = {
	name: "Harkirat",
	age: 19
}

console.log("Harkirats age is " + user.age);
```

Assignment #1

Write a function that takes a `user` as an input and greets them with their name and age

Assignment #2

Write a function that takes a new object as input which has `name` , `age` and `gender` and greets the user with their gender (Hi `Mr/Mrs/Others` harkirat, your age is 21)

Assignment #3

Also tell the user if they are legal to vote or not

### 

[](https://projects.100xdevs.com/tracks/javascript-1/Javascript-101-5#9b197a5cdcf647569573074e1c949b30 "Arrays")Arrays

Arrays let you group data together

```javascript
const users = ["harkirat", "raman", "diljeet"];
const tatalUsers = users.length;
const firstUser = users[0];
```

Assignment

Write a function that takes an array of numbers as input, and returns a new array with only even values. Read about `filter` in JS

### 

[](https://projects.100xdevs.com/tracks/javascript-1/Javascript-101-5#9f55b8b49ba54601ba8b91488f5845ab "Array of Objects")Array of Objects

We can have more complex objects, for example an array of objects

```javascript
const users = [{
		name: "Harkirat",
		age: 21
	}, {
		name: "raman",
		age: 22
	}
}

const user1 = users[0] 
const user1Age = users[0].age
```

Assignment

Write a function that takes an array of users as inputs and returns only the users who are more than 18 years old

### 

[](https://projects.100xdevs.com/tracks/javascript-1/Javascript-101-5#622b71d42e904b918145fd156a83b410 "Object of Objects")Object of Objects

We can have an even more complex object (object of objects)

```javascript
const user1 = {
	name: "harkirat",
	age: 19,
	address: {
		city: "Delhi",
		country: "India",
		address: "1122 DLF"
	}
}

const city = user1.address.city;
```

Assignment

Write a function that takes a user


