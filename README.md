JavaScript
============
A Practical Style Guide to Everyday JavaScript.

Here in lies a guide to writing principled, consistent, and idiomatic JavaScript.

There are many ways to write good JavaScript. This guide takes a strong stance on syntactic style. Whereas other guides will say, you can do things _this_ way, or _that_ way -- this guide says do it _this_ way. Though the more debatable sections will be made noted. The most important aspect of writing good JavaScript syntatically is _consistency_. Ultimately, whichever style you do choose to use, be sure to stick to it.

For the most part this guide contains a compliation of style guides from various online and book sources. Please refer to the resources section for the list of all sources for this document. I also used the MLA style for citations. Please refer to the MLA style guide for an explanation of how MLA style citations are formated.

This document is licensed under a Creative commons MIT license, please feel free to fork a copy and make modifications, but keep the license with it so others can use it as well.

By Sean Westfall

## Table of Contents
  1. [Official Documentation](#official-documentation)
       + [ECMAScript](#ecmascript)
       + [Browser Compatibility](#browser-compatibility)
  1. [Terminology](#terminology)
  1. [Using Strict](#using-strict)
  1. [Using ES6](#using-es6)
  1. [Syntax](#syntax)
       + [Primative Types](#primative-types)
         + [Strings](#strings)
         + [Numbers](#numbers)
         + [Booleans](#booleans)
         + [Undefined](#undefined)
         + [Null](#null)
         + [Symbol _ES6_](#Symbol)
       + [Complex Types](#complex-types)
         + [Functions](#functions)
           + [Properties](#properties)
         + [Arrays](#arrays)
         + [Objects](#objects)
           + [Accessors](#accessors)
           + [Constructors](#constructors)
       + [Other](#other)
  1. [Conditional Evaluation](#conditional-evaluation)
  1. [Type Casting & Coercion](#type-casting-&-coercion)
  1. [Naming](#naming)
  1. [Proper Spacing](#whitespaces)
  1. [Comments](#comments)
  1. [Commonly Used Objects](#commonly-used-objects)
       + [Regular Expression](#regular-expression)
       + [Date](#date)
       + [Math](#math)
       + [Promises](#promises)
  1. [Generators _ES6_](#generators)
       + [Combined with Promises](#combined-with-promises)
  1. [Events](#events)
  1. [Exceptions](#exceptions)
  1. [Modules](#modules)
  1. [JSON](#json)
  1. [jQuery](#jQuery)
       + [When to use jQuery and when not to](#when-to-use-jquery-and-when-not-to)
  1. [Bitwise Operators](#bitwise-operators)
  1. [Misc](#misc)
       + [Hoisting](#hoisting)
       + [Callbacks](#callbacks)
       + [Semicolons](#semicolons)
       + [Anonymous Functions](#anonymous-functions)
       + [Eval](#eval)
  1. [Testing](#testing)
  1. [Considerations for Production](considerations-for-production)
  1. [Resources](#Resources)
       + [Essential Reading](#essential-reading)
       + [Books Worth Reading](#books-worth-reading)
       + [Blogs Worth Following](#blogs-worth-following)
       + [Linters](#linters)
       + [Build Tools](#build-tools)
       + [Other](#other)
  1. [Performance and Memory](#Performance-and-Memory-Tuning)
  1. [Security](#secutiry)
  1. [Considerations for JS Engine Performance](#considerations-for-js-engine-performance)
       + [V8](#v8)
       + [SpiderMonkey](#spidermonkey)
       + [IE](#ie)
  1. [IE Issues and Compatibility](#ie-issues-and-compatibility)
  1. [License](#license)
  1. [Bibliography](#bibliography)

## Official Documentation
- [Annotated ECMAScript 5.1](http://es5.github.com/)
- [EcmaScript Language Specification, 5.1 Edition](http://ecma-international.org/ecma-262/5.1/)
- [EcmaScript Language Specification, ECMA-262 6th Edition *Draft*](https://people.mozilla.org/~jorendorff/es6-draft.html)

**[⬆ back to top](#table-of-contents)**
## Terminology
- type
- primitive value
- object
- constructor
- prototype
- native object
- built-in object
- host object
- undefined value
- Undefined type
- null value
- Null type
- Boolean value
- Boolean type
- Boolean object
- String value
- String type
- String object
- Number value
- Number type
- Number object
- Infinity
- NaN
- function
- built-in function
- property
- method
- built-in method
- attribute
- own property
- inherited property

**[⬆ back to top](#table-of-contents)**
## Using Strict

**[⬆ back to top](#table-of-contents)**
## Using ES6

**[⬆ back to top](#table-of-contents)**
## Types and Syntax
Javascript splits all variables types into two camps, primative types and complex types:
* [Primative](#primative-types)
  + string
  + number
  + boolean
  + null
  + undefined

When you access a primitive type you work directly on its value.
```javascript
var foo = 1,
    bar = foo;

bar = 9;

console.log(foo, bar); // => 1, 9
```
* [Complex](#complex-types)
  + object
  + array
  + function
  + symbol (ES6)

When you access a complex type you work on a reference to its value.
```javascript
var foo = [1, 2],
    bar = foo;

bar[0] = 9;
```

### Variable Declarations
Using only one `var` per scope (function) promotes readability
and keeps your declaration list free of clutter (also saves a few keystrokes).
```javascript
// Bad
var foo = "";
var bar = "";
var qux;

// Good
var foo = "",
  bar = "",
  qux;

// or..
var // Comment on these
foo = "",
bar = "",
quux;
```
Declare unassigned variables last. This is helpful when later on you might need to assign a variable depending on one of the previous assigned variables.
```javascript
// bad
var i, len, dragonball,
    items = getItems(),
    goSportsTeam = true;

// bad
var i, items = getItems(),
    dragonball,
    goSportsTeam = true,
    len;

// good
var items = getItems(),
    goSportsTeam = true,
    dragonball,
    length,
    i;
```
### Complex Types
Complex: When you access a complex type you work on a reference to its value
 * object
 * array
 * function
 * symbol (ES6)
````javascript
var foo = [1, 2],
    bar = foo;

bar[0] = 9;
````

#### Objects

````javascript
var arr = [1, 2, 3];  // No space after [ or before ].
var obj = {a: 1, b: 2, c: 3};  // No space after { or before }.

// depending on the number of characters, and the length of the data (~10 char or more), 
// consider spacing on multiple lines:
var obj = {a:1,b:2}; // short
var obj = {a:'item one', b:'item two'}; // short

// long
var obj = {
  'one':'Hey I am a long line! aaaaaaaaaaaaaaaaa',
  'two':'Hey I am a long line too! aaaaaaaaaaaaaaaaa'
};
````
Matching indentation also improves readablity 
````javascript
// bad
CORRECT_Object.prototype = {
  a: 0,
  b: 1,
  lengthyName: 2
};
// good
WRONG_Object.prototype = {
  a          : 0,
  b          : 1,
  lengthyName: 2
};
````

Object constructors don't have the same problems, but for readability and consistency object literals should be used.
Should be written as:

````javascript
// bad
var item = new Object();

// good
var item = {};
````

````javascript
// bad
var o = new Object();

var o2 = new Object();
o2.a = 0;
o2.b = 1;
o2.c = 2;
o2['strange key'] = 3;

// good
var o = {};

var o2 = {
  a: 0,
  b: 1,
  c: 2,
  'strange key': 3
};
````
Using the `for (var key in obj)` loop is the most elegant way to go through an objects direct properties.
Use the `obj.hasOwnProperty(key)` to only go through an object direct properties, but keep in mind
that doing so will slow down the interation significantly.
````javascript
for (var key in obj) {
  if (obj.hasOwnProperty(key)) { // only look at direct properties
    var value = obj[key];
    // do stuff...
  }
}
`````


**[⬆ back to top](#table-of-contents)**
## Conditional Evaluation

**[⬆ back to top](#table-of-contents)**
## Type Casting & Coercion

**[⬆ back to top](#table-of-contents)**
## Naming

**[⬆ back to top](#table-of-contents)**
## Proper Spacing

**[⬆ back to top](#table-of-contents)**
## Comments

**[⬆ back to top](#table-of-contents)**
## Commonly Used Objects

**[⬆ back to top](#table-of-contents)**
## Generators _ES6_

**[⬆ back to top](#table-of-contents)**
## Events

**[⬆ back to top](#table-of-contents)**
## Exceptions

**[⬆ back to top](#table-of-contents)**
## Modules

**[⬆ back to top](#table-of-contents)**
## JSON

**[⬆ back to top](#table-of-contents)**
## jQuery

**[⬆ back to top](#table-of-contents)**
## Bitwise Operators

**[⬆ back to top](#table-of-contents)**
## Misc

**[⬆ back to top](#table-of-contents)**
## Testing

**[⬆ back to top](#table-of-contents)**
## Considerations for Production

**[⬆ back to top](#table-of-contents)**
## Resources
### Essential Reading
+ http://msdn.microsoft.com/en-us/library/ie/yek4tbz0(v=vs.94).aspx
+ https://developer.mozilla.org/en-US/docs/Web/JavaScript
+ http://contribute.jquery.org/style-guide/js/

### JavaScript Books Worth Reading:
+ Secrets of the JavaScript Ninja by John Resig and Bear Bibeault
+ JavaScript: The Good Parts by Douglas Crockford
+ Effective JavaScript: 68 Specific Ways to Harness the Power of JavaScript by David Herman
+ High Performance JavaScript by Nicholas C. Zakas
+ Eloquent JavaScript: A Modern Introduction to Programming by Marijn Haverbeke
+ JavaScript Patterns by Stoyan Stefanov
+ Functional JavaScript: Introducing Functional Programming with Underscore.js by Michael Fogus

### JavaScript Blogs Worth Mentioning:
+ http://perfectionkills.com/
+ http://raganwald.com/
+ http://jlongster.com/

### Other Awesome Styles Guides You Should Read
+ https://github.com/rwaldron/idiomatic.js/
+ https://github.com/airbnb/javascript
+ https://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml
+ http://contribute.jquery.org/style-guide/js/ (The jQuery style guide also contains a general JS style guide)

**[⬆ back to top](#table-of-contents)**
## Performance and Memory Tuning

**[⬆ back to top](#table-of-contents)**
## Security

**[⬆ back to top](#table-of-contents)**
## Considerations for JS Engine Performance

**[⬆ back to top](#table-of-contents)**
## IE Issues and Compatibility

**[⬆ back to top](#table-of-contents)**
## License

(The MIT License)

Copyright (c) 2014 Sean Westfall

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

**[⬆ back to top](#table-of-contents)**

## Bibliography

**[⬆ back to top](#table-of-contents)**
