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

### @color[#e49436](var scope - hoisting)

This solution is very commonly used

```js
function loopsi2(){
    var numbers = [];

    for(var i = 0; i < 5; i++){
        numbers.push((function(n){
            return function () { return n; }
        })(i));
    }

    numbers.forEach(item => console.log(item()));
}

loopsi2();
```
It uses *Closure* and *IIFE*

---
### @color[#e49436](let - not hoisted)

```js
function loopsi3(){
    var numbers = [];

    for(let i = 0; i < 5; i++){
        numbers.push(function () { return i; });
    }

    numbers.forEach(item => console.log(item()));
}

loopsi3();
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

@snap[west sidebar]
```js
function calc(num) {
    return num * 2;
}

let calcF = calc;

console.log(calcF(3));
console.log(calc(3));
```
@snapend

@snap[east sidebar]
```js
let calcF2 = function calc2(num) {
    return num * 3;
}

console.log(calcF2(3));
//console.log(calc2(2));
```
@snapend

---



---