---?image=assets/images/grauman-js-at-bancor.png

---
# Introduction

Our Facebook Group: 
GRAUMAN - JavaScript at Bancor

Tools: 
VSCode, Browser, Smile

---

## JavaScript @ Bancor

@color[#e49436](GRAUMAN) dev courses for R&D teams
https://www.grauman.co.il

---

### @color[#e49436](JavaScript History)

- Netscape

- The browser war

- Standartization - ECMAScript

- jQuery

- Node

- SPA

---

### @color[#e49436](JavaScript in a nutshell)

- All browser support JS - After all, JS is the language of the browsers
- Client Side
- Structured and syntax inspired by C language
- Dynamic - Types, Evaluation at runtime

---

### @color[#e49436](JavaScript in a nutshell)

- Prototype based, as opposed to classical OO with classes
- Function is First-Class - Meaning it’s an object! It can be passed around, assigned to variables, create objects

---

### @color[#e49436](JavaScript on the Server?)

* Node.js revolutionized the way JS can be used

* Node is a server-side runtime
  * Allow JS programs on the ‘other end’ 
  * Full-Stack JS apps!

---

### @color[#e49436](JavaScript on the Server?)


* NPM - The worlds’ biggest open-source ecosystem
  * Currently more than 600,000 packages!

* Currently v10
  * Keeps evolving
  * New release every 6 months

---

### @color[#e49436](ECMAScript)


In 2015, the 6th version (referred as ES6 or ES2015) was released

ES6 brought a lot of new features and improvements, most notably

---
### @color[#e49436](ES6)
@ol
- Block scoped variables (let, const)
- Arrow functions (lambda)
- Enhanced parameters (default values, rest)
- Destructuring
- Modules (Yet to be natively supported)
- Classes syntax (‘Looks like’ OOP)
- Iterators
- Generators
- Promises
- and more...
@olend

---

### @color[#e49436](Variables)

- var was used more than 20 years

- Introduced scope issues

- var is scoped to the function
  - regardless of its declaration
  - Hoisting mechanism

---

- Primitives:
  - number, string, boolean, object, undefined, null, symbol (es6)
  - All the others considered as object types
  - js is dynmaically typed

```js
var whoAmI;
whoAmI = 17;
whoAmI = false;
whoAmI = "Shahar";
whoAmI = { name: 'Shahar', age: 27 };
```

---

- == vs. ===
  - == checks for value equality
  - === behaves as == but with type check

```js
console.log('== vs. ===');
console.log("0 == ''", 0 == ''); // true
console.log("0 === ''", 0 === ''); // false
console.log("0 == '0'", 0 == '0'); // true
console.log("0 === '0'", 0 === '0'); // false
console.log("false == '0'", false == '0'); // true
console.log("false === '0'", false === '0'); // false
console.log("true == 1", true == 1); // true
console.log("true === 1", true === 1); // false
console.log("null == undefined", null == undefined); // true
console.log("null === undefined", null === undefined); // false
```

---

### @color[#e49436](typeof operator)

```js
console.log('\ntypeof operator');

console.log(typeof "lala");
console.log(typeof '@');

console.log(typeof 3);
console.log(typeof 3.5);
console.log(typeof Infinity);
console.log(typeof NaN);

console.log(typeof true);
console.log(typeof false);

console.log(typeof [1, 2, 3, 4]);
console.log(typeof { name: 'Shahar', age: 34 });
console.log(typeof /^[0-9]$/);
console.log(typeof (new Date()));
console.log(typeof null);

console.log(typeof undefined);

console.log(typeof function () { });

console.log(typeof x === undefined ? 'x is undefined' : 'x is defined');
console.log(x === undefined ? 'x is undefined' : 'x is defined');
```

---

### What can be sent to test for the output to be truthy?

```js
function test(x) {
    return x != x;
}
```

---

### @color[#e49436](var scope)

```js

for (var i = 1; i < 5; i++) {
  console.log(i);
}

console.log(i); //?

```

---

### @color[#e49436](var scope - hoisting)

var is raised to the top of its scope before execution

```js
//Hoisting equals headache :)

function hoist() {
    var ok = true;

    if (ok) {
        var notOK = false;
        console.log(notOK);
    }

    console.log(ok, notOK);
}

hoist();

```

---

### @color[#e49436](var scope - hoisting)

##### JS interpreter reorganizes the code and hoist notOK to the top of the function:

```js
function hoist(){
    var notOK;
    var ok = true;

        if (ok) {
        var notOK = false;
        console.log(notOK);
    }

    console.log(ok, notOK);
}

hoist();
```

##### This is the reason it's available to the last console.log...

---

### @color[#e49436](var scope - hoisting)

```js
function hoist2(){
    console.log(i);
    for (var i = 0; i < 5; i++) {
        console.log(i);        
    }
    console.log(i);
}

hoist2();
```

---

### @color[#e49436](var scope - hoisting)

```js
function loopsi(){
    var numbers = [];

    for(var i = 0; i < 5; i++){
        numbers.push(function () { return i; });
    }

    numbers.forEach(item => console.log(item()));
}

loopsi();
```
@ul
- Because var is hoisted, all functions refer to the same variable!
@ulend

---

### @color[#e49436](let - not hoisted)

```js
function loopsi2(){
    var numbers = [];

    for(let i = 0; i < 5; i++){
        numbers.push(function () { return i; });
    }

    numbers.forEach(item => console.log(item()));
}

loopsi2();
```

---
### @color[#e49436](let) and const

- let and const was introduced in es 2015
- let behaves similary to declarations in other languages
- It's available ONLY inside the immediate surrounding block, 
- From the declaration line until the end of the block
---

### let and @color[#e49436](const)

- const is like let, but needs initialization right away
- Can't be modified later on
- If const is reference, it can't be assigned a new one
- But we can modify the data it points to

---

### @color[#e49436](functions)
#### It's all about functions!

@ul
- Functions are objects
- Function constructors
- Can be assigned to a variable
- Can be passed as an argument
- Closure - Can be nested inside another function
- Can get more/less arguments than declared
- Can invoke itself (uh?!)
- Lambda (Arrow functions)
@ulend

---

### @color[#e49436](functions)

#### Functions are objects

```js
function imAnObject(){
    console.log('Hi there' + imAnObject.whatsup);    
}

imAnObject.whatsup = 'Whasssaaaa?';
imAnObject();
```

---
### @color[#e49436](functions)

#### Function Expressions

- JS functions are flexible structure, for example:
- You can name a function as usual and assign it to a variable like so:

```js
function calc(num) {
    return num * 2;
}

//Function expression
let calcF = calc;

console.log(calcF(3));
```

---
### @color[#e49436](functions)

#### Function statement vs. Expressions

```js
function calc(num) {
    return num * 2;
}

let calcF = calc;

console.log(calcF(3));
console.log(calc(3));
```

```js
let calcF2 = function calc2(num) {
    return num * 3;
}

console.log(calcF2(3));
//console.log(calc2(2)); //Can be used no more 
```

---
### @color[#e49436](functions)

#### Anonymous function

```js
const myFunc = function(x){
    console.log(isNaN(x) ? 'Not a number' : `x is ${x}`);
}

myFunc();
myFunc(8);
myFunc('6t');
myFunc(0x32);
```

---
### @color[#e49436](functions)

#### function can be passed as argument

```js
function calcThis(x, func){
    func(x);
    console.log(`Raising x by 2: ${Math.pow(x,2)}`);       
}

calcThis(8, myFunc);
```

#### Heavily used for callbacks

---

### @color[#e49436](functions)

#### There is no overloading in JS

```js
function studentDetails(name, age, email) {
    let details = 'No details!';

    if (name != undefined) {
        details = `Student Details:\nName: ${name}`;
    }

    if (age != undefined) {
        details += `\nAge: ${age}`;
    }

    if (email != undefined) {
        details += `\nEmail: ${email}`;
    }

    return details;
}

console.log('studentDetails1');
console.log(studentDetails());
console.log(studentDetails('Shahar'));
console.log(studentDetails('Shahar', 27));
console.log(studentDetails('Shahar', 27, 'info@grauman.co.il'));
```

---
### @color[#e49436](functions)

##### It is common to pass an object containing the parameters
##### As with configuration objects

```js
function studentDetails2(props) {

    if (!props) return 'No details!';

    let details = '';

    if (props.name != undefined) {
        details = `Student Details:\nName: ${props.name}`;
    }

    if (props.age != undefined) {
        details += `\nAge: ${props.age}`;
    }

    if (props.email != undefined) {
        details += `\nEmail: ${props.email}`;
    }

    return details;
}

console.log('studentDetails2');
console.log(studentDetails2());
console.log(studentDetails2({ name: 'Shahar' }));
console.log(studentDetails2({ name: 'Shahar', age: 27 }));
console.log(studentDetails2({ name: 'Shahar', age: 27, email: 'info@grauman.co.il' }));

```

---
### @color[#e49436](functions)

#### Destructuring is a new feature of es6.
##### (more on it later) but let's see a bit of it

```js
function studentDetails3({ name, age, email }) {

    let details = 'No details!';

    if (name != undefined) {
        details = `Student Details:\nName: ${name}`;
    }

    if (age != undefined) {
        details += `\nAge: ${age}`;
    }

    if (email != undefined) {
        details += `\nEmail: ${email}`;
    }

    return details;
}

//console.log(studentDetails3());
console.log('studentDetails3');
console.log(studentDetails3({ name: 'Shahar' }));
console.log(studentDetails3({ age: 27, name: 'Shahar' }));
console.log(studentDetails3({ email: 'info@grauman.co.il', age: 27, name: 'Shahar' }));
```

---
### @color[#e49436](functions)

#### functions can be nested, so the inner has the scope of the outer.
- Meaning, the inner has access to outer variables/parameters
- This is called @color[#e49436](Closure)

```js
function outer(num) {
    let num1 = 9;

    function inner(x) {
        console.log('inner', num + x + num1);
        return x;
    }

    console.log('outer', inner(7));
}

outer(2);
```

---
### @color[#e49436](Closure)

##### Functions maintain a lexical scoping of variables upon declaration
##### It enables encapsulation

```js
function func2(){
    let num = 42;

    function square(){
        return num * num;
    }

    return square;
}

let innerF = func2();

console.log(innerF());
```

---
### @color[#e49436](Closure)

```js
function F(f) {
  function G(g) {
    function H(h) {
      console.log(f + g + h);
    }
    H(3);
  }
  G(2);
}
F(1);
```

---
### @color[#e49436](Function's arguments object)

Functions can be passed less/more arguments than declared

```js
function concat(separator) {
   var result = '', 
       i;

   for (i = 1; i < arguments.length; i++) {
      result += arguments[i] + separator;
   }
   
   return result;
}

concat(', ', 'me', 'you', 'her');
concat('; ', 'X', 'R', 'S', 'U');
concat('. ', 'js', 'node', 'es6', 'web', 'fun');
```

---
### @color[#e49436](Default values)

Functions can be passed less/more arguments than declared

```js
function multiply(a, b) {
  b = typeof b !== 'undefined' ?  b : 1;

  return a * b;
}

multiply(5);
```
```js
function multiply (a, b = 2) {
  return a * b;
}
multiply(5);
```
---
### @color[#e49436](Default values)

```js
function multiply (a, b = 2) {
  return a * b;
}

function foo (num = 1, mul = multiply(num)) {
  return [num, mul];
}
foo(); // [1, 2]
foo(6); // [6, 12]
```
---
### @color[#e49436](Default values)

@size[0.5em](Let's say we need to assign some default values to each of the parameters)
```js
function stam() { return 'lala'; }

function omg(a, b, c, d, e, f, g) {
  switch (arguments.length) {
    case 0:
      a = 1;
    case 1:
      b = 5;
    case 2:
      c = b;
    case 3:
      d = stam();
    case 4:
      e = this;
    case 5:
      f = arguments;
    case 6:
      g = this.num;
    default:
  }
  //...
  //Further processing
}

omg.call({ num: 101 });
```
---
### @color[#e49436](Default values)

And here is with default values (smile):
```js
function notSoBad(a, b = 5, c = b, d = stam(), 
                  e = this, f = arguments, g = this.num) {
  //...
  //Further processing
}

notSoBad.call({ num: 101 });
```

---
### @color[#e49436](Default values)

Let's turn this to use default values

```js
function createElement (tag, config) {
  tag = tag || 'div';
  config = config || {};
  
  const element = document.createElement(tag);
  const content = config.content || 'Default Content';
  const text = document.createTextNode(content);
  let classNames = config.classNames;
  
  if (classNames === undefined) {
    classNames = ['module-text', 'default'];
  }
  
  element.classList.add(...classNames);
  element.appendChild(text);
  
  return element;
}
```
---

```js
function createElement (tag = 'div', {
            content = 'Default Content',
            classNames = ['module-text', 'special']
          } = {}) {
  const element = document.createElement(tag);
  const text = document.createTextNode(content);
  
  element.classList.add(...classNames);
  element.appendChild(text);
  
  return element;
}
```

@size[0.5em](Not only we set the config parameter to empty object, we disect this parameter using *desctructuring* syntax, extracting content and classNames, with default values!)

---
### @color[#e49436](Labmda) - Fat Arrow Functions

- Allow cleaner syntax.
- Preserve the 'this' context in which they operate in

```js
let add1 = function(x, y) {
    return x + y;
}

console.log(add1(3,4));
```
```js
let add2 = (x, y) => x + y;

console.log(add2(3,4));
```

---
### @color[#e49436](Labmda) - Fat Arrow Functions

```js
var strings = [
  'Lala',
  'Wawa',
  'Babala',
  'Sababa'
];

var arr = strings.map(function(str) { return str.length; });
console.log(arr);

var arr2 = strings.map(str => str.length);
console.log(arr2);
```

---
### @color[#e49436](IIFE) - Immediate Invoked Function Expression

- Function can be self invoked. Yes. Why?
- It can create closure out of it, making modules possible

```js
var res = (function () { 
    var name = 'Shahar'; 
    return name; 
})(); 
console.log(res);
```
---
### @color[#e49436](IIFE)

```js
var config = (function (){
    //Get data from somewhere
    var server = 'server-address',
        database = 'database-name',
        userid = 'username',
        pwd = 'password';
    
    return {
        getSQLConnectionString() {
            return `Server=${server}; Database=${database};  User Id=${userid}; Password=${pwd}`;               
        }
        //more config stuff...
    };
})();
```

Voila! - config is ready

---
### @color[#e49436](IIFE)

```js
var images = (function countImgs(element) {
    if (element.nodeName.toLowerCase() === 'img') return 1;
    
    var count = 0;
    for (var i = 0, child; child = element.childNodes[i]; i++) {
        count += countImgs(child);
    }
    return count;
})(document.body);
```
@ul
- Invoking IIFE with argument
- The name, countImgs, is neccessary here
  - To be able to call it recursively
  - Notice - the name can be called ONLY within the scope of the IIFE
@ulend

---

Remember this?

```js
function func(){
    let funcs = [];

    for(var i = 0; i < 5; i++) {
        var res = function(){
            console.log(i);
        }         
        funcs.push(res);
    }
 
    funcs.forEach(f => f());
}
func();
```

- Short Ex - Fix the problem with:
  - Closure
  - IIFE

---

Here is one solution

```js
function func(){
    let funcs = [];

    for(var i = 0; i < 5; i++) {
        function outer(){
            let num = i;
            function res(){
                console.log(num);
            }
            return res;
        }
        funcs.push(outer());
    }
 
    funcs.forEach(f => f());
}
func();
```
---

Here is the same solution using IIFE

```js
function func(){
    let funcs = [];

    for(var i = 0; i < 5; i++) {
        funcs.push((function(){
            let num = i;
            function res(){
                console.log(num);
            }
            return res;
        })());        
    }
 
    funcs.forEach((f, i) => f());
}
func();
```
---
The same, but passing parameter

```js
function func(){
    var numbers = [];

    for(var i = 0; i < 5; i++){
        numbers.push((function(n){
            return function () { console.log(n); }
        })(i));
    }

    numbers.forEach(f => f());
}

func();
```
So *Closure* and *IIFE*. Got that?
<br>
Or just use *let* @fa[thumbs-o-up]

---
#### Let's see what you've got for me:
#### (1) What is the output of this?

```js
function doSomething(a) {
    function doSomethingElse(a) {
        return a - 1;
    }
    var b;
    b = a + doSomethingElse(a * 2);
    console.log(b * 3);
}
doSomething(2);
```
Solution:
@ul
- 15
@ulend

---
#### Let's see what you've got for me:
#### (2) What is the output of this?

```js
function foo() {
    function bar(a) {
        i = 3;

        console.log(a + i);
    }
    for (var i = 0; i < 10; i++) {
        bar(i * 2);
    }
}
foo();
```
Solution:
@ul
- Infinite loop! How we can fix that?
@ulend

---
#### Let's see what you've got for me:
#### (3) What is the output of this?

```js
var a = 2;

(function func(obj) {
    var a = 3;
    console.log(a);
    console.log(obj.a);
})(window);

console.log(a);
```
Solution:
@ul
- 3, 2, 2
@ulend

---
#### Let's see what you've got for me:
#### (4) What is the output of this?

```js
var a = 2;
(function func(def) {
    def(window);
})(function (obj) {
    var a = 3;
    console.log(a); 
    console.log(obj.a);
});
```
Solution:
@ul
- 3, 2
@ulend

---
### Ex

- @size[0.5em](Create a function for copy properties from one json object to the other, by flattening other object)
-  @size[0.5em](For example, you use person object with this structure:)

```js
const person = {
    firstName: '',.
    lastName: '',
    age: 0,
    email: ''
}
// And you get, from some api, this object:
const otherPerson = {
    fullName: {
        firstName: 'Shahar',
        lastName: 'Grauman'
    },
    age: 80,
    email: 'info@grauman.co.il'
}
```

---
### @color[#e49436](Function constructor)

Functions can be used to construct objects

```js
function person(name, age, address = 'Some Address...'){
    return {
        name: name || 'john doe',
        age: age || 0,
        address,
        getAddress: function () { return this.address; },
        details: function(){
            return `Person ${this.name} is ${this.age} years old, leaving in ${this.getAddress()}`;        
        }
    };
}

const me = person('Shahar', 27, 'Karkur');
const anonymous = person();
console.log(me.details(), anonymous.details());
```

---
### @color[#e49436](Function constructor)

Although it's damn simple, the problem is each object contains a copy of the functions!
<br>
This can quickly lead to memory bloat
<br>
But this is not a constructor as we're familiared with
<br>
So we can use 'new'

---
### @color[#e49436](Function constructor)

- new Func(args) will create a new object
- 'this' will reffer to the newly created object

```js
function Car(model){
  this.model = model;
  this.wheels = 4;  
}

var myCar = new Car('Volvo');
console.log(`Car ${myCar.model} has ${myCar.wheels} wheels`);

myCar.constructor.name //"Car"
```

---
### @color[#e49436](Function constructor)

The this problem. Consider 'this' :)

```js
function Car(){
  this.model;
  this.wheels = 4;  
  
  setTimeout(function() {
    this.model = 'BMW';
  }, 2500);
}

var myCar = new Car();
console.log(`Car ${myCar.model} has ${myCar.wheels} wheels`);
```

---

1- Using local variable to 'cache' the this reference for later use

```js
function Car(){
  var self = this;  
  self.model = 'Volvo';
  
  setTimeout(function() {
    self.model = 'BMW';
  }, 2500);
}
```
2- With lambdas it's straight forward
```js
function Car(){
  this.model = 'Volvo';
  
  setTimeout(() => {
    this.model = 'BMW';
  }, 2500);
}
```
---
#### Understanding the @color[#e49436](this context) 

```js
function sayYourName() {
    console.log(this.myName);
}

sayYourName();
```
- myName belongs to...
- The global context

```js
myName = 'Shahar';
sayYourName();
```
---
#### Understanding the @color[#e49436](this context) 

Attaching outer function to behave like methods

```js
function sayYourName() {
    console.log(this.myName);
}
const person = {
    myName: 'Shahar',
    sayYourName
}

person.sayYourName();
```

---
#### Understanding the @color[#e49436](this context) 

- Use call/apply to set the 'this' object as the first argument
- Pass arguments if necessary
- call gets variadic arguments
- apply gets arguments in array

```js
myName = 'Shahar'; //or global.myName = 'Shahar'
sayYourName.call({ myName }, 'lala');
sayYourName.apply(global, ['lala']);
```

---
#### Understanding the @color[#e49436](this context) 

@color[#e49436](bind) the person context to the function for later invokation

```js
function sayYourName() {
    console.log(this.myName);
}

const person = {
    myName: 'Shahar'
}

const saySomething = sayYourName.bind(person);
saySomething();
```

---
#### Understanding the @color[#e49436](this context) 

```js
const person = {
    myName: 'Shahar'
}

person.saySomething = sayYourName;

//now person is the context of saySomething
person.saySomething();
```

---

### @color[#e49436](Prototypes) 

#### All JavaScript objects inherit properties and methods from a prototype

The *Object.prototype* is on the top of the **prototype inheritance chain**:

- Array objects inherit from Array.prototype
- Date objects inherit from Date.prototype
- Car objects inherit from Car.prototype
- All the above inherit from **Object.prototype**

---
#### @color[#e49436](Prototypes) - Object.setPrototypeOf 

```js
function sayYourName() {
    console.log(this.myName);
}
const person = {
    myName: 'Shahar'
}
//Set the prototype of person
Object.setPrototypeOf(person, {saySomething: sayYourName});
person.saySomething();
console.log(person);
```

---
### @color[#e49436](Prototypes)

- So by setting the prototype, we're actually delegating the functionality to a higher object
- If the current object doesn't have the method, it's being looked up the *'protorype chain'*

```js
const person = {
    sayYourName
}

const shahar = {
    myName: 'Shahar'
}

Object.setPrototypeOf(shahar, person);
shahar.sayYourName();
```
---
### @color[#e49436](Prototype) chaining

```js
const person = {
    sayYourName
}
const shahar = {
    myName: 'Shahar'
}
const son = {
    myName: 'Hanoch'
}

Object.setPrototypeOf(shahar, person);
Object.setPrototypeOf(son, shahar);
shahar.sayYourName();
son.sayYourName();
```
---
### @color[#e49436](Prototype) chaining

```js
const person = { };

const shahar = {
    myName: 'Shahar',
    sayYourName
};

Object.setPrototypeOf(shahar, person);

//Now shahar has it too!
person.stateYourName = function(){
    console.log(`Please state your name: ${this.myName}`);
}

shahar.sayYourName();
shahar.stateYourName();

//Override by implement the same function down the chain

person.sayYourName = function(){
    console.log(`My name is: ${this.myName}`);
}

delete shahar.sayYourName;
shahar.sayYourName();
```

---
### @color[#e49436](Prototype) - *new* keyword

```js
function Person(name, age){
    this.name = name;
    this.age = age;
}

let me = new Person('Shahar', 27);
console.log(me.name, me.age);

let him = new Person('Yeled', 4);
```
We can use prototype like so
```js
Person.prototype.details = function(){
    console.log(`Name: ${this.name}, Age: ${this.age}`);
}
him.details();

```
---
### @color[#e49436](Prototype) - Object.create

Create a new object, using an existing object as the prototype of the newly created object

```js
function Student(name, age, course){
    Person.call(this, name, age);
    this.course = course;
}
Student.prototype = Object.create(Person.prototype);
```
We 'reset back' the constructor because now it's Person
```js
Student.prototype.constructor = Student;
```

---
### @color[#e49436](Prototype) - Object.create

```js
let student = new Student('Ace', 25, 'JavaScript');
student.details();

Student.prototype.details = function(){
    //Using delegation to parent
    Person.prototype.details.call(this);
    console.log(`Studying ${this.course}`);
};

student.details();
```
---
### @color[#e49436](Prototype) - Common practice

properties will be defined in the constructor

```js
function Ctor(x, y){
    //properties...    
}
```
methods will be defined on the prototype
```js
Ctor.prototype.method1 = function() {};
```
---
### @color[#e49436](Prototype) - Shadowing

Shadowing is like overriding:

A.prototype.func,

B inherited A's prototype

Objects of B has func (from A.prototype)

B.prototype added func as well

Objects of B uses now the shadowing func

---
### @color[#e49436](Prototype) - Shadowing

```js
var a = { a: 42 };
var b = Object.create(a);
a.a;
b.a;
a.hasOwnProperty('a');
b.hasOwnProperty('a');
b.a++;
a.a;
b.a;
b.hasOwnProperty('a');
```

---
### @color[#e49436](Prototype)

Short Ex:

Make this work

```js
const arr = ['a','b','c','d','e','f'];
arr.randomize();
console.log(arr); //['b','d','a','c','f', 'e',]
```

---
### @color[#e49436](Prototype)

```js
Array.prototype.shuffle = function(){
	for(let i = 0; i < this.length; i++){
		let rand = parseInt(Math.random()*this.length);
		let [a,b] = [this[i], this[rand]];
		this[i] = b;
		this[rand] = a;
    }
}
```

---
#### ES6 @color[#e49436](Classes) - a spoon of sugar

```js
class Person {
  //Only 1 constructor is allowed
  constructor(name, age) {
    this.name = name;
    this.age = age;
    Person.counter++;
  }
  //getter
  get details(){
    return `${this.name}, ${this.age}`;
  }
  //Static methods can be defined inside the class
  static Counter() { 
    return Person.counter; 
  }
}
//Static properties - must be defined outside 
Person.counter = 0;
```
---
#### ES6 @color[#e49436](Classes) - inheritance

```js
class Student extends Person {
  constructor(name, age, course){
    //First line should call super ctor
    super(name, age);
    //Before accessing 'this'
    this.course = course;
  }
  
  //Override super method
  get details() {
    return `${super.details}, studying ${this.course}`;
  }
}
```

---
#### @color[#e49436](Callbacks) - *I'll call you back*

Callbacks were here since the beginning

```js
try {
  const data = getData();
  const manipulated = manipulateData(data);
  const result = finalize(manipulated);
  console.log('Result: ' + result);
} catch(err) {
  failedCallback(err);
}
```

We start off nicely, but time goes by and...

---
#### @color[#e49436](Callbacks) - Callback Hell

```js
getData(function(data) {
    manipulateData(data, function(manipulated) {
        finalize(manipulated, function(result) {
            console.log('Result: ' + result);
    }, failedCallback);
  }, failedCallback);
}, failedCallback);

```
They were good till a point where nesting callbacks was hillarious

---
### @color[#e49436](Promise) (preview)

Promises let us chain those functions more easily

```js
getData().then(function(data) {
  return manipulateData(data);
})
.then(function(manipulated) {
  return finalize(manipulated);
})
.then(function(result) {
  console.log('Result: ' + result);
})
.catch(failedCallback);
```
---
### @color[#e49436](Promise) (preview)

We can even shorten this by using lambdas

```js
getData().then(data => manipulateData(data))
	 .then(manipulated => finalize(manipulated))
	 .then(result => console.log('Result: ' + result))
	 .catch(faileCallback);
```

---
### @color[#e49436](Promise) - (preview)

**async/await** let us use promises like synchronous coding

```js
async () => {
  try {
    const data = await getData();
    const manipulated = await manipulateData(data);
    const result = await finalize(manipulated);
    console.log('Result: ' + result);
  } catch(err) {
    failedCallback(err);
  }
}
```
---
### @color[#e49436](Promise) - break it apart

- Promise object is what its name implies
  - A promise to complete at some later point in time
- Promise can complete or fail
- Promise may return a value

```js
const promise = new Promise((resolve, reject) => {
  setTimeout(() => resolve('timed out'), 1000);
});
console.log('Promise fired');
promise.then(res => console.log(res));
console.log('Promise done');
```
---
### @color[#e49436](Promise) - break it apart

rejecting the promise usualy used when an error occur

```js
const promise = new Promise((resolve, reject) => {
  setTimeout(() => reject('timed out'), 1000);
});
console.log('Promise fired');
promise.then(res => console.log('Completed: ' + res), rej => console.log('Rejected: ' + rej));
console.log('Promise done');
```
---
### @color[#e49436](Promise) - break it apart

- If an error is thrown inside the promise
  - It's automatically rejected
  - And the return value is ignored

```js
const promise = new Promise((resolve, reject) => {
  throw new Error('OMG!');
  //Same as 
  await Promise.reject(new Error("OMG!"));
});
console.log('Promise fired');
promise
  .then(res => console.log('Completed: ' + res), rej => console.log('Rejected: ' + rej))
  .catch(err => console.log(err));
console.log('Promise done');
```
---
### @color[#e49436](Promise) - async/await

```js
async function func() {
  return 42;
}
```
- The word @color[#e49436](async) means the function **always** returns a promise
- If the code returns non-promise
  - Then it's being wrapped into a *resolved promise* with that value (*return Promise.resolve(42)*)

```js
func().then(console.log); // 42
```
---
### @color[#e49436](Promise) - async/await

- Inside *async* function we can call some promise
- @color[#e49436](await) makes JS wait until that promise settles
- @color[#e49436](await) can be used **only** inside *async* function

```js
async function func() {

  const promise = new Promise((resolve, reject) => {
    setTimeout(() => resolve(42), 1000);
  });

  console.log('Promise done: ', await promise);
}

func();
```

---
### @color[#e49436](Promise) - async/await

- await awaits thenable object
- You can create your own object with then compatible function

```js
class Student {
  constructor(name) {
    this.name = name;
  }
  then(resolve, reject) {
    setTimeout(() => resolve(`Student name: ${this.name}`), 500);
  }
};

(async () => {
  const result = await new Student('Shahar');
  alert(result);
})();
```

---
### @color[#e49436](Promise) - async/await

Class method can by async as well

```js
class Student {
  constructor(name) {
    this.name = name;
  }
  async hold() {
    return `Student name: ${this.name}`;
    //Or return Promise.resolve(`Student name: ${this.name}`);
    //Or return await some promise
  }
};

new Student('Shahar')
    .hold()
    .then(console.log);

```

---
### @color[#e49436](Promise) - async/await

What's also great about this is *Error handling*: is so similar to synchronous coding!

```js
async () => {
  try {
    const response = await fetch('some url');
    const user = await response.json();
  } catch(err) {
    //catches errors either of fetch or response.json
    alert(err);
  }
}
```
```js
async function func() {
  const response = await fetch('bad url');
  //...
}
// func() becomes a rejected promise
func().catch(err => {});
```

---
### @color[#e49436](Promise) - async/await

- @color[#e49436](Promise.all) waits for multiple promises to complete
- @color[#e49436](Promise.race) waits for the first to complete

```js
const results = await Promise.all([fetch(url1), fetch(url2)]);
//results is an array of promises results
```
```js
const result = await Promise.race([fetch(url1), fetch(url2)]);
//result will be the first evaluated value 
```

---
### @color[#e49436](Promise) - Ex

- @size[0.5em](1 - Extract data from Github public repositories)
- @size[0.5em](2 - https://api.github.com/repositories)
- @size[0.5em](3 - Grab some github repositories and print for each one the following json:)
- @size[0.5em](4 - Show all users' avatars images in the page)

```js 
{
    id: 210, //repository id
 full_name: 'polanski/fred', 
 avatar_url: 'https://avatars0.githubusercontent.com/u/75?v=4', 
 html_url: 'https://github.com/fred'    
}

//Use fetch(url) which returns a Promise
  fetch(url)
  .then(res => res.json());
}
```
---
### @color[#e49436](Generators)

#### Generators enable us to pause the control flow and resume it when needed
#### In contrast to regular procedural flow where flow is blocked until all data is constructed
#### With generators, data can be consumed in chunks, with full control of the consumer

---
### @color[#e49436](Generators)

Let say we have an array of 100 users, and we're searching for user with id 105595.

We can write function to retrieve'em all like so
```js
function getUsers(){
  //Users from somewhere
  const users = [{id:54520, name: 'Jack'}, {id:32021, name: 'Lori'}, {id:105595, name: 'Shahar'}, 
                 {id:87547, name: 'Moses'}, {id:965412, name: 'Honos'}/*, ....*/];
  return users;
}

for(let user of getUsers()){
  if(user.id == 105595){
    console.log(`Found userid ${user.id} - ${user.name}`);
    break;
  }
}
```
---
### @color[#e49436](Generators)

The thing is getUsers returns ALL the users, which could be large

More than that, we can find what we're looking for much sooner than iterating over all the array

@quote[I wish there was a better solution...]

---
### @color[#e49436](Generators)

```js
function* getUsers(){
  //Users from somewhere
  const users = [{id:54520, name: 'Jack'}, {id:32021, name: 'Lori'}, {id:105595, name: 'Shahar'}, 
                 {id:87547, name: 'Moses'}, {id:965412, name: 'Honos'}/*, ....*/];
  
  for(let user of users){
    yield user;
  }
}

for(let user of getUsers()){
  if(user.id == 105595){
    console.log(`Found userid ${user.id} - ${user.name}`);
    break;
  }
}
```
---
### @color[#e49436](Generators)

If we have an internal collection we don't wanna expose?

We can use generator to encapsulate it

And expose data via iterator+generator

Iterator - Gives The ability to enumerate over a collection

---
### @color[#e49436](Generators)

```js
class UsersAPI {
  getNextQuantaUsersFromSomewhere(){
    return [{id:54520, name: 'Jack'}, {id:32021, name: 'Lori'}, {id:105595, name: 'Shahar'}, {id:87547, name: 'Moses'}, {id:965412, name: 'Honos'}];
  }
  
  *[Symbol.iterator](){
    let quantaUsers = this.getNextQuantaUsersFromSomewhere();
    for(let user of quantaUsers){      
      yield user;
      quantaUsers = this.getNextQuantaUsersFromSomewhere();
    }
  }
}
```
---
### @color[#e49436](Generators)

And the consumer can decide when to quit

```js
const users = new UsersAPI()

for(let user of users){
  if(user.id == 105595){
    console.log(`Found userid ${user.id} - ${user.name}`);
    break;
  }
}
```
---
### @color[#e49436](Generators) - Ex

Convert this to generator

```js
function step (start, stop, by) {
    const characters = [];
    while (start < stop) {
        characters.push(String.fromCharCode(start));
        start += by;
    }
    return characters;
}

var steps = step(65, 91, 2);
for (var i = 0; i < steps.length; i++) {
    console.log(steps[i]); // A, C, E, G, ...
}
```
---
### @color[#e49436](Higher-Order Functions)

Functions that operate on other functions 

Either by taking them as arguments 

Or by returning them

---
### @color[#e49436](Higher-Order Functions)

Most common usages are, for example

Functions that create new functions

Function compositions

---
### @color[#e49436](Higher-Order Functions)

```js
function gt(y) {
  return x => x > y;
}

let gt100 = gt(100);

console.log(gt100(101));
```
---
### @color[#e49436](Higher-Order Functions)

We can 'wrap' functions for pre/post processing

```js
function beforeAfter(func) {
  return (...args) => {
    console.log(`calling ${func.name} with ${args}`);
    let result = func(...args);
    console.log(`${func.name} returned ${result}`);
    return result;
  };
}
beforeAfter(Math.sqrt)(64);
```
---
### @color[#e49436](Higher-Order Functions)

```js
function repeat(until, func) {
  for (let i = 0; i < until; i++) {
    func(i);
  }
}

repeat(5, console.log);
//Or
repeat(5, i => console.log(`Next num is ${i}`));
```

---
### @color[#e49436](Higher-Order Functions)

```js
function repeat(until, func) {
  for (let i = 0; i < until; i++) {
    func(i);
  }
}

function ifnot(condition, perform) {
  if (!condition) perform();
}

repeat(5, x => {
  ifnot(x % 2 == 1, () => {
    console.log(x, "is even");
  });
});
```
---
### @color[#e49436](Higher-Order Functions)

Let's think of a function that format currencies values

For example: You feed it the symbol (Like '$'), The decimal seperator (Like ',') and the value to format, like 312090

And it should format it to $3120,90

Or if you send it '£', '.' and 1009 then -> £10.09

---
### @color[#e49436](Higher-Order Functions)

```js
const formatCurrency = function(currencySymbol, decimalSeparator) {
    return function(value) {
        const wholePart = Math.floor(value/100);
        let agorot = value % 100;        
        return `${currencySymbol}${wholePart}
                ${decimalSeparator}
                ${(''+agorot).padStart(2,0)}`;
    }
}
 
 getTashlum = formatCurrency('$', '.');
 
 //Now we can use getTashlum to format values
```
---
### @color[#e49436](Higher-Order Functions)

So basically we can combine any sort of logic to our demand

Here is a simple array concatenation function

```js
function concat(arr1, arr2){
	return [...arr1, ...arr2];
}
```

Ex - Write flattenArr function getting jagged array 
like [[1, 2, 3], [4, 5], [6]] 
returning [1, 2, 3, 4, 5, 6]

Use concat

---?image=assets/images/grauman-js-at-bancor.png

---