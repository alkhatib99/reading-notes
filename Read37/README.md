# React I (Part 1)

## Table Of Content

## React ES6

### What is ES6?

**ES6** stands for ECMAScript 6.

ECMAScript was created to standardize JavaScript, and ES6 is the 6th version of ECMAScript, it was published in 2015, and is also known as ECMAScript 2015.

### Why Should I Learn ES6?

React uses ES6, and you should be familiar with some of the new features like:

* Classes- ["Read Here"](https://www.w3schools.com/react/react_es6_classes.asp)
* Arrow Functions- ["Read Here"](https://www.w3schools.com/react/react_es6_arrow.asp)
* Variables `(let, const, var)`- ["Read Here"](https://www.w3schools.com/react/react_es6_variables.asp)
* Array Methods like `.map()`- ["Read Here"](https://www.w3schools.com/react/react_es6_array_methods.asp)
* Destructuring- ["Read Here"](https://www.w3schools.com/react/react_es6_destructuring.asp)
* Modules- ["Read Here"](https://www.w3schools.com/react/react_es6_modules.asp)
* Ternary Operator- ["Read Here"](https://www.w3schools.com/react/react_es6_ternary.asp)
* Spread Operator- ["Read Here"](https://www.w3schools.com/react/react_es6_spread.asp)
  
### Variables and constant feature comparison

I found an clearly resource that explains the concepts of scope and the differences between let, var, and const in the [Understanding Variables, Scope, and Hoisting in JavaScript](https://www.digitalocean.com/community/tutorials/understanding-variables-scope-hoisting-in-javascript) resource on DigitalOcean. This table provides a brief overview.

#### Variable declaration

ES6 introduced the let keyword, which allows for block-scoped variables which cannot be hoisted or redeclared.

```ES5
var x = 0
```

```ES6
let x = 0
```

[MDN Reference: let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)

#### Constant declaration

ES6 introduced the const keyword, which cannot be redeclared or reassigned, but is not immutable.

```ES6
const CONST_IDENTIFIER = 0 // constants are uppercase by convention
```

[MDN Reference: const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)

#### Arrow functions

The arrow function expression syntax is a shorter way of creating a function expression. Arrow functions do not have their own this, do not have prototypes, cannot be used for constructors, and should not be used as object methods.

```ES5
function func(a, b, c) {} // function declaration
var func = function (a, b, c) {} // function expression
```

```ES6
let func = (a) => {} // parentheses optional with one parameter
let func = (a, b, c) => {} // parentheses required with multiple parameters
```

[MDN Reference: Arrow functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

#### Template literals

Concatenation/string interpolation
Expressions can be embedded in template literal strings.

```ES5
var str = 'Release date: ' + date
```
```ES6
let str = `Release Date: ${date}`
```
[MDN Reference: Expression interpolation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals#Expression_interpolation)

#### Multi-line strings

Using template literal syntax, a JavaScript string can span multiple lines without the need for concatenation.

```ES5
var str = 'This text ' + 'is on ' + 'multiple lines'
```

```ES6
let str = `This text
            is on
            multiple lines`
```

>Note: Whitespace is preserved in multi-line template literals. See [Removing leading whitespace in ES6 template strings.](https://muffinresearch.co.uk/removing-leading-whitespace-in-es6-template-strings/)
[MDN Reference: Multi-line strings](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals#multi-line_strings)

#### Implicit returns

The return keyword is implied and can be omitted if using arrow functions without a block body.

```ES5
function func(a, b, c) {
  return a + b + c
}
```

```ES6
let func = (a, b, c) => a + b + c // curly brackets must be omitted
```

[MDN Reference: Function body](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions#function_body)

#### Key/property shorthand

ES6 introduces a shorter notation for assigning properties to variables of the same name.

```ES5
var obj = {
  a: a,
  b: b,
}
```

```ES6
let obj = {
  a,
  b,
}
```

[MDN Reference: Property definitions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer#property_definitions)

#### Method definition shorthand

The function keyword can be omitted when assigning methods on an object.

```ES5
var obj = {
  a: function (c, d) {},
  b: function (e, f) {},
}
```

```ES6
let obj = {
  a(c, d) {},
  b(e, f) {},
}
obj.a() // call method a
```

[MDN Reference: Method definitions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Method_definitions).

#### Destructuring (object matching)

Use curly brackets to assign properties of an object to their own variable.
```
var obj = {a: 1, b: 2, c: 3}
```

```ES5
var a = obj.a
var b = obj.b
var c = obj.c
```

```ES6
let {a, b, c} = obj
```

[MDN Reference: Object initializer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer#new_notations_in_ecmascript_2015)

#### Array iteration (looping)

 A more concise syntax has been introduced for iteration through arrays and other iterable objects.

```var arr = ['a', 'b', 'c']
```

```ES5
for (var i = 0; i < arr.length; i++) {
  console.log(arr[i])
}
```

```ES6
for (let i of arr) {
  console.log(i)
}
```

[MDN Reference: for...of](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of)

#### Default parameters

Functions can be initialized with default parameters, which will be used only if an argument is not invoked through the function.

```ES5
var func = function (a, b) {
  b = b === undefined ? 2 : b
  return a + b
}
```

```ES6
let func = (a, b = 2) => {
  return a + b
}
func(10) // returns 12
func(10, 5) // returns 15
```

[MDN Reference: Default paramters](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Default_parameters)

## Resources & Related Topics 

### ES6 Overview

- [ES6 Syntax and Feature Overview](https://www.taniarascia.com/es6-syntax-and-feature-overview/)

### React

- [React - Hello World](https://reactjs.org/docs/hello-world.html)
- [React - JSX](https://reactjs.org/docs/introducing-jsx.html)
- [React - Rendering Elements](https://reactjs.org/docs/rendering-elements.html)
- [React - Components & Props](https://reactjs.org/docs/components-and-props.html)
- [React - State & Lifecycle](https://reactjs.org/docs/state-and-lifecycle.html)
- [React - Handling Events](https://reactjs.org/docs/handling-events.html)

### Tailwind CSS

- [Utility First CSS](https://tailwindcss.com/docs/utility-first)
- [Tailwind in 15 minutes](https://www.youtube.com/watch?v=6zIuAyLZPH0)

### Next.js

- [Learn Next.js](https://nextjs.org/learn/basics/create-nextjs-app)
- [Why to use Next.js](https://www.youtube.com/watch?v=rtgbaKBhdkk)
