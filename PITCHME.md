# Introduction

Our Group: 
https://www.facebook.com/groups/WobbiNodeJS2018

Tools: 
VSCode, Browser

---

## Node.js @ Wobi

@color[#e49436](GRAUMAN) dev courses for R&D teams
https://www.grauman.co.il

---

## Part 1 - *JavaScript*
## Part 2 - *Node.js*

---

## In order to know @color[#e49436](Node)
## understand @color[#e49436](JavaScript)

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

---