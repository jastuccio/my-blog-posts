  #Javascript - Understanding the Weird Parts

### lexical environment -Where something sits physically in your code.
                                                                                                                                                                                                                                                                                                    
exists in programming languages in which where you write something is important.

### execution context - A wrapper to help manage the code that is running. 
  There are lots of lexical environments.  Which one is currently runnig is managed via execution contexts. It can contain things beyond what you have written in your code.

### Object - a collection of name value pairs

``` javascript
Address:
  {
    Street: 'Main',
    Number: 100,
    Apartment:
    {
      Floor: 3,
      Number: 301
    }
  }
```

-----
The base execution context is the global execution context.

### 2 content creation phases
  1. Creation phase
    * creates the global object
      * 'Global' = not inside a function
    * creates the 'this' variable
    * Outer Environment
    * "hoisting"
      * prior to executing your code line by line the JS engine setups memory space for variables and functions
      * sets a place holder for variables of 'undefined
        * assigns variable values in the execution phase
      * functions are in memory in their entirety

  2. Execution phase - goes through your code line by line


-----
JS has dynamic typing

### The 6 primitive data types

primitive data types are types that are not objects. They represent a single value.

* undefined - represents a lack of existence
  8 Do not set your variables to `undefined`
  * leave undefined to the JS engine
* null - also represents a lack of existence
  * you can set your variables to `null`
* Boolean
  * true or false
* Number
  * only 1 type of number
    * floating point number (always some decimals)
    * it can make math "weird"
* String
  * a sequence of characters
  * both ' and " can be used
* Symbol
  * used in ES6
  * more on this later

### Operators

A special function with a different syntax.  They generally take two parameters and return one one result. example + calls the addition function. instead of:

``` javascript
function + (a,b) {
  return a + b;
}

+ (3,4);
```

we can use an operator like so: `3 + 4;` // infix notation

-----

Operator precedence - which operator or function gets called first

Operator associativity - The order operator functions get called in when they have the same precedence.
  * left to right (left associativity) or right to left (right associativity)

-----

### coercion

-----

js can fake namespaces using objects

``` javascript
var english = { 
    greet: 'Hello!' 
};

var spanish = {};
spanish.greet = 'Hola!';

console.log("english greeting = " + english.greet);
console.log("spanish greeting = " + spanish.greet);
```

-----
first class functions - everything you can do with other types you can do with other functions.

  * assign them to variables
  * pass them around
  * create them on the fly

### function statements vs function expressions

function statement:

``` javascript
function greet() {
  console.log("Hi");
}
```
* The funcition is placed in memory
* It doesnt return a value until the function is executed
* it is hoisted

function expression:
``` javascript
greet(); //can be called before it is created because of the way funcitons are hoisted

var greet = function () {
  console.log("Hi");
}

//can **NOT** be called before it is created
hello()
```

* function expressions are not hoisted
* `hello` goes into memory as a `var` with the value `undefined`
* when the js engine executes the code the function is stored in the variable
  * this is why you get an erro if you try to call it first

  -----

  ### 'by value' vs 'by reference'

  ``` javascript
  // by value (primitives)
var a = 3;
var b;

b = a;
a = 2;

console.log(a);  // 2
console.log(b); // 3

// by reference (all objects (including functions))
var c = { greeting: 'hi' };
var d;

d = c;
c.greeting = 'hello'; // mutate both c and d because they are the same memory space

console.log(c); // hello
console.log(d); // hello

// by reference (even as parameters)
function changeGreeting(obj) {
    obj.greeting = 'Hola'; // mutate   
}

changeGreeting(d);
console.log(c); // Hola
console.log(d); // Hola

// equals operator sets up new memory space (new address)
c = { greeting: 'howdy' };
console.log(c); // howdy
console.log(d); // Hola
```

-----

The State Pattern `var self = this`

https://medium.com/@patrickackerman/the-state-pattern-with-vanilla-javascript-e40ff83e85d0

-----

arguments - the parameters you pass to functions
`arguments` is a key word that contains all the arguments you pass to a function





