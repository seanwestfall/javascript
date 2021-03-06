JavaScript
==========

A Practical Style Guide to Everyday JavaScript.

Here in lies a guide to writing principled, consistent, and idiomatic JavaScript.

There are many ways to write good JavaScript. This guide takes a strong stance on syntactic style. Whereas other guides will say, you can do things _this_ way, or _that_ way -- this guide says do it _this_ way. Though the more debatable sections will be made noted. The most important aspect of writing good JavaScript syntatically is _consistency_. Ultimately, whichever style you do choose to use, be sure to stick to it.

For the most part this guide contains a compliation of style guides from various online and book sources. Please refer to the resources section for the list of all sources for this document. I also used the MLA style for citations. Please refer to the MLA style guide for an explanation of how MLA style citations are formated.

This document is licensed under a Creative commons MIT license, please feel free to fork a copy and make modifications, but keep the license with it so others can use it as well.

By Sean Westfall

## Table of Contents preliminary

0. [Official Documentation](#official-documentation)
	+ ECMAScript
	+ Browser Compatibility
1. [Terminology](#terminology)
2. [Using Strict](#using-strict)
3. [Using ES6](#using-es6)
3. [Syntax](#syntax)
  + [Primative Types](#primative-types)
      + [Strings]
      + [Numbers]
      + [Booleans]
      + [Undefined]
      + [Null]
      + [Symbol ES6]
  + [Complex Types](#complex-types)
    + [Functions](#functions)
      + [Properties](#properties)
    + [Arrays](#arrays)
    + [Objects](#objects)
      + [Accessors]
      + [Constructors]
  + [Other]
    + [NaN]
    + [Infinity]
4. [Conditional Evaluation]
5. [Type Casting & Coercion]
6. [Naming](#naming)
7. [Proper Spacing](#whitespaces)
8. [Comments](#comments)
9. [Commonly Used Objects]
     + Regular Expression
     + Date
     + Math
     + Promises
10. [Generators ES6] 
     + Combined with Promises
11. [Events]
12. [Exceptions]
13. [Modules]
14. [JSON]
15. [jQuery](#jquery)
      + [When to use jQuery and when not to]
16. [Bitwise Operators]
18. [Misc]
      + [Hoisting]
      + [Callbacks]
      + [Semicolons]
      + [Anonymous Functions]
      + [Eval]
19. [Testing]
20. [Considerations for Production]
21. [Resources](#Resources)
      + [Essential Reading]
      + [Books Worth Reading]
      + [Blogs Worth Following]
      + [Linters]
      + [Build Tools]
      + [Other]
22. [Performance and Memory](#Performance-and-Memory-Tuning)
23. [Security]
24. [Considerations for JS Engine Performance]
      + V8
      + SpiderMonkey
      + IE
25. [IE Issues and Compatibility]
26. [License]
27. [Bibliography]

## Table of Contents

  1. [Resources](#Resources)
  1. [Using Strict](#usestrict)
  1. [Whitespace](#whitespace)
  1. [Beautiful Syntax](#spacing)
  1. [Type Checking (Courtesy jQuery Core Style Guidelines)](#type)
  1. [Conditional Evaluation](#cond)
  1. [Practical Style](#practical)
  1. [Naming](#naming)
  1. [Misc](#misc)
  1. [Native & Host Objects](#native)
  1. [Comments](#comments)
  1. [Bitwise Operators](#bitwise)
  1. [Things to Consider for Production](#production) 
  1. [ES6 Modules](#modules)
  1. [One Language Code](#language)
  1. [When to Use jQuery](#whentousejquery)
  1. [jQuery Style Guide](#jquerystyle)
  1. [Types](#types)
  1. [Objects](#objects)
  1. [Arrays](#arrays)
  1. [Strings](#strings)
  1. [Functions](#functions)
  1. [Properties](#properties)
  1. [Variables](#variables)
  1. [Hoisting](#hoisting)
  1. [Conditional Expressions & Equality](#conditional-expressions--equality)
  1. [Blocks](#blocks)
  1. [Comments](#comments)
  1. [Whitespace](#whitespace)
  1. [Commas](#commas)
  1. [Semicolons](#semicolons)
  1. [Type Casting & Coercion](#type-casting--coercion)
  1. [Naming Conventions](#naming-conventions)
  1. [Accessors](#accessors)
  1. [Constructors](#constructors)
  1. [Events](#events)
  1. [Modules](#modules)
  1. [jQuery](#jquery)
  1. [ECMAScript 5 Compatibility](#ecmascript-5-compatibility)
  1. [Testing](#testing)
  1. [IE compatibility](#ie-issues) 
  1. [Performance](#performance)
  1. [Resources](#resources)
  1. [In the Wild](#in-the-wild)
  1. [Translation](#translation)
  1. [The JavaScript Style Guide Guide](#the-javascript-style-guide-guide)
  1. [Contributors](#contributors)
  1. [License](#license)

## Resources

## Official Documentation
### [Annotated ECMAScript 5.1](http://es5.github.com/)
### [EcmaScript Language Specification, 5.1 Edition](http://ecma-international.org/ecma-262/5.1/)
### [EcmaScript Language Specification, ECMA-262 6th Edition *Draft*](https://people.mozilla.org/~jorendorff/es6-draft.html)

# Essential Reading
+ http://msdn.microsoft.com/en-us/library/ie/yek4tbz0(v=vs.94).aspx
+ https://developer.mozilla.org/en-US/docs/Web/JavaScript
+ http://contribute.jquery.org/style-guide/js/

# JavaScript Books Worth Reading:
+ Secrets of the JavaScript Ninja by John Resig and Bear Bibeault
+ JavaScript: The Good Parts by Douglas Crockford
+ Effective JavaScript: 68 Specific Ways to Harness the Power of JavaScript by David Herman
+ High Performance JavaScript by Nicholas C. Zakas
+ Eloquent JavaScript: A Modern Introduction to Programming by Marijn Haverbeke
+ JavaScript Patterns by Stoyan Stefanov
+ Functional JavaScript: Introducing Functional Programming with Underscore.js by Michael Fogus

# JavaScript Blogs Worth Mentioning:
+ http://perfectionkills.com/
+ http://raganwald.com/
+ http://jlongster.com/

# Other Awesome Styles Guides You Should Read
+ https://github.com/rwaldron/idiomatic.js/
+ https://github.com/airbnb/javascript
+ https://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml
+ http://contribute.jquery.org/style-guide/js/ (The jQuery style guide also contains a general JS style guide)

## Terminology
These are the terms used through this guide, aswell as the ECMAScript standard. Please refer to this section for the correct and exact usage:
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

## Using Strict
Declare with
`"use strict";`
at the top of your JavaScript to declare your JavaScript to run in strict mode.


Strict mode makes it easier to write "secure" JavaScript.


Strict mode changes previously accepted "bad syntax" into real errors.

As an example, in normal JavaScript, mistyping a variable name creates a new global variable. In strict mode, this will throw an error, making it impossible to accidentally create a global variable.

In normal JavaScript, a developer will not receive any error feedback assigning values to non-writable properties.

In strict mode, any assignment to a non-writable property, a getter-only property, a non-existing property, a non-existing variable, or a non-existing object, will throw an error.

Here is a list of changes strict enforces on your code:

## Using ES6
Throughout this guide I mention which features are apart of the future planned ES6 standard. Though, if you do use an ES6 feature, such as Symbols, or .map(), you must make a note of it, ES6 features are still experimental and NOT a standard yet. Untill these features of official drafted in the the spec, you must let other developers know you're using them. Mention at the top of the js file, where experimental ES6 features are being used, and in the code where it is being used.
````javascript
// example

// example ES6 code

````
https://6to5.github.io/

## Syntax

## Primative Types
Primitives: When you access a primitive type you work directly on its value
 * string
 * number
 * boolean
 * null
 * undefined
````javascript
var foo = 1,
    bar = foo;

bar = 9;

console.log(foo, bar); // => 1, 9
````
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

### Variable Declarations

// 2.B.1.2
// Using only one `var` per scope (function) promotes readability
// and keeps your declaration list free of clutter (also saves a few keystrokes)
````javascript
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
````
* Declare unassigned variables last. This is helpful when later on you might need to assign a variable depending on one of the previous assigned variables.
````javascript
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
````

### Complex Types

## Objects

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
* Matching indentation also improves readablity 
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

* Object constructors don't have the same problems, but for readability and consistency object literals should be used.
* Should be written as:

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

* Object.keys()
Use [Object.keys()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys) to get an array of an object's keys, and then iterate through that object using array functions.

````javascript
// good
var obj = { 
  a:'item one',
  b:'item two'
};

var keys = Object.keys(obj);

keys.forEach(function(i) {
  console.log(obj[i]);
});
/*  => prints:
 *  item one
 *  item two
 */  
````


````javascript
// another elegant way to go through an objects direct properties 
for (var key in obj) {
  if (obj.hasOwnProperty(key)) { // only look at direct properties
    var value = obj[key];
    // do stuff...
  }
}
`````


To get only an object keys that it owns, use this version of object keys.

###Arrays
* Use Array and Object literals instead of Array and Object constructors.
* Array constructors are error-prone due to their arguments.
* Because of this, if someone changes the code to pass 1 argument instead of 2 arguments, the array might not have the expected length.
* To avoid these kinds of weird cases, always use the more readable array literal.
````javascript
// bad
// Length is 3.
var a1 = new Array(x1, x2, x3);

// Length is 2.
var a2 = new Array(x1, x2);

// If x1 is a number and it is a natural number the length will be x1.
// If x1 is a number but not a natural number this will throw an exception.
// Otherwise the array will have one element with x1 as its value.
var a3 = new Array(x1);

// Length is 0.
var a4 = new Array();

// good
var a = [x1, x2, x3];
var a2 = [x1, x2];
var a3 = [x1];
var a4 = [];
````
* 


````javascript
// bad
var items = new Array();

// good
var items = [];
````
* Use [Array.prototype.push()](#https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push) to add elements to the end of an array:
````javascript
var someStack = [];
// bad
someStack[someStack.length] = 'abracadabra';
// good
someStack.push('abracadabra');
````
* Likewise use [Array.prototype.unshift()](#https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift) to add elements to the beginning of an array:
* but don't forget that the function returns the length of the array, not the new array
````javascript
someStack.unshift('abracadabra');
````
* Use [Array.prototype.splice()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice) to copy and remove elements from an array.
* Here's how to properly copy and array
````javascript
var len = items.length,
    itemsCopy = [],
    i;
// bad
for (i = 0; i < len; i++) {
  itemsCopy[i] = items[i];
}
// good
itemsCopy = items.slice();
````

Array.prototype.every()
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every

Use every when checking the condition of an array.

or use 

Array.prototype.some()
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some

When checking every element in an array for a condition.

### Loops
for-in loops are often incorrectly used to loop over the elements in an Array. This is however very error prone because it does not loop from 0 to length - 1 but over all the present keys in the object and its prototype chain. Here are a few cases where it fails:
````javascript
\\ bad
function printArray(arr) {
  for (var key in arr) {
    print(arr[key]);
  }
}

printArray([0,1,2,3]);  // This works.

var a = new Array(10);
printArray(a);  // This is wrong.

a = document.getElementsByTagName('*');
printArray(a);  // This is wrong.

a = [0,1,2,3];
a.buhu = 'wine';
printArray(a);  // This is wrong again.

a = new Array;
a[3] = 3;
printArray(a);  // This is wrong again.

\\ good
function printArray(arr) {
  var l = arr.length;
  for (var i = 0; i < l; i++) {
    print(arr[i]);
  }
}
\\ or the forEach is also typically faster and cleaner without having to worry about an index.
````



### Functions
* Assign variables at the top of their scope. This helps avoid issues with variable declaration and assignment hoisting related issues.
````javascript
// bad
function() {
  test();
  console.log('doing stuff..');

  //..other stuff..

  var name = getName();

  if (name === 'test') {
    return false;
  }

  return name;
}

// good
function() {
  var name = getName();

  test();
  console.log('doing stuff..');

  //..other stuff..

  if (name === 'test') {
    return false;
  }

  return name;
}

// bad
function() {
  var name = getName();

  if (!arguments.length) {
    return false;
  }

  return true;
}

// good
function() {
  if (!arguments.length) {
    return false;
  }

  var name = getName();

  return true;
}
````
* Only sometimes hoisting is okay, but usually not: see below for when it's appropriate.

* Never declare a function in a non-function block (if, while, etc). Assign the function to a variable instead. Browsers will allow you to do it, but they all interpret it differently, which is bad news bears.
````javascript
// anonymous function expression
var anonymous = function() {
  return true;
};

// named function expression
var named = function named() {
  return true;
};

// immediately-invoked function expression (IIFE)
(function() {
  console.log('Welcome to the Internet. Please follow me.');
})();
````
* Never name a parameter arguments, this will take precedence over the arguments object that is given to every function scope. 'arguments' is a reserved word in all browsers.
````javascript
// bad
function nope(name, options, arguments) {
  // ...stuff...
}

// good
function yup(name, options, args) {
  // ...stuff...
}
````
* ECMA-262 defines a block as a list of statements. A function declaration is not a statement.
````javascript
// bad
if (currentUser) {
  function test() {
    console.log('Nope.');
  }
}

// good
var test;
if (currentUser) {
  test = function test() {
    console.log('Yup.');
  };
}
````

// 2.B.1.3
// var statements should always be in the beginning of their respective scope (function).

````javascript
// Bad
function foo() {

  // some statements here

  var bar = "",
    qux;
}

// Good
function foo() {
  var bar = "",
    qux;

  // all statements after the variables declarations.
}
````
* Name your functions. This is helpful for stack traces.
````javascript
// bad
var log = function(msg) {
  console.log(msg);
};

// good
var log = function log(msg) {
  console.log(msg);
};
````


## ES6 Standard 
// 2.B.1.4
// const and let, from ECMAScript 6, should likewise be at the top of their scope (block).
````javascript
// Bad
function foo() {
  let foo,
    bar;
  if (condition) {
    bar = "";
    // statements
  }
}
// Good
function foo() {
  let foo;
  if (condition) {
    let bar = "";
    // statements
  }
}
````
* do not use function declarations within blocks
* While most script engines support Function Declarations within blocks it is not part of ECMAScript (see ECMA-262, clause 13 and 14). Worse implementations are inconsistent with each other and with future EcmaScript proposals. ECMAScript only allows for Function Declarations in the root statement list of a script or function. Instead use a variable initialized with a Function Expression to define a function within a block:
````javascript
\\ bad
if (x) {
  function foo() {}
}
\\ good
if (x) {
  var foo = function() {};
}
````




// 2.B.2.1
````javascript
// Named Function Declaration
function foo( arg1, argN ) {

}

// Usage
foo( arg1, argN );
````

// 2.B.2.2
````javascript
// Named Function Declaration
function square( number ) {
  return number * number;
}

// Usage
square( 10 );

// Really contrived continuation passing style
function square( number, callback ) {
  callback( number * number );
}

square( 10, function( square ) {
  // callback statements
});
````

// 2.B.2.3
````javascript
// Function Expression
var square = function( number ) {
  // Return something valuable and relevant
  return number * number;
};

// Function Expression with Identifier
// This preferred form has the added value of being
// able to call itself and have an identity in stack traces:
var factorial = function factorial( number ) {
  if ( number < 2 ) {
    return 1;
  }

  return number * factorial( number - 1 );
};
````
// 2.B.2.4
````javascript
// Constructor Declaration
function FooBar( options ) {

  this.options = options;
}

// Usage
var fooBar = new FooBar({ a: "alpha" });

fooBar.options;
// { a: "alpha" }
````

* Assign methods to the prototype object, instead of overwriting the prototype with a new object. Overwriting the prototype makes inheritance impossible: by resetting the prototype you'll overwrite the base!
````javascript
function Jedi() {
  console.log('new jedi');
}

// bad
Jedi.prototype = {
  fight: function fight() {
    console.log('fighting');
  },

  block: function block() {
    console.log('blocking');
  }
};

// good
Jedi.prototype.fight = function fight() {
  console.log('fighting');
};

Jedi.prototype.block = function block() {
  console.log('blocking');
};
````
* Methods can return this to help with method chaining.
````javascript
// bad
Jedi.prototype.jump = function() {
  this.jumping = true;
  return true;
};

Jedi.prototype.setHeight = function(height) {
  this.height = height;
};

var luke = new Jedi();
luke.jump(); // => true
luke.setHeight(20); // => undefined

// good
Jedi.prototype.jump = function() {
  this.jumping = true;
  return this;
};

Jedi.prototype.setHeight = function(height) {
  this.height = height;
  return this;
};

var luke = new Jedi();

luke.jump()
  .setHeight(20);
````

### toString() methods
* It's okay to write a custom toString() method, just make sure it works successfully and causes no side effects.
````javascript
function Jedi(options) {
  options || (options = {});
  this.name = options.name || 'no name';
}

Jedi.prototype.getName = function getName() {
  return this.name;
};

Jedi.prototype.toString = function toString() {
  return 'Jedi - ' + this.getName();
};
````

### Events
* When attaching data payloads to events (whether DOM events or something more proprietary like Backbone events), pass a hash instead of a raw value. This allows a subsequent contributor to add more data to the event payload without finding and updating every handler for the event. For example, instead of:
````javascript
// bad
$(this).trigger('listingUpdated', listing.id);

...

$(this).on('listingUpdated', function(e, listingId) {
  // do something with listingId
});

// good
$(this).trigger('listingUpdated', { listingId : listing.id });

...

$(this).on('listingUpdated', function(e, data) {
  // do something with data.listingId
});
````

### Modules
* The module should start with a !. This ensures that if a malformed module forgets to include a final semicolon there aren't errors in production when the scripts get concatenated. 
* The file should be named with camelCase, live in a folder with the same name, and match the name of the single export.
* Add a method called noConflict() that sets the exported module to the previous version and returns this one.
* Add a method called noConflict() that sets the exported module to the previous version and returns this one.
````javascript
// fancyInput/fancyInput.js

!function(global) {
  'use strict';

  var previousFancyInput = global.FancyInput;

  function FancyInput(options) {
    this.options = options || {};
  }

  FancyInput.noConflict = function noConflict() {
    global.FancyInput = previousFancyInput;
    return FancyInput;
  };

  global.FancyInput = FancyInput;
}(this);
````
# jQuery
There are 182 functions in jQuery as of version 1.11. I can't cover all of it here in this guide, though keep in mind that there are other equally valid libraries out there that can do much of the same thing. jQuery is just the most popular client side scripting HTML library as of today, so no javascrpt guide would be complete without it.

Here are just a few generalized principles to use when writing jQuery code:
* Don't do
````javascript
````

### When not to use jQuery:
http://youmightnotneedjquery.com/

### How to use jQuery:
* Prefix jQuery object variables with a $.
````javascript
// bad
var sidebar = $('.sidebar');

// good
var $sidebar = $('.sidebar');
````
* Cache jQuery lookups.
````javascript
// bad
function setSidebar() {
  $('.sidebar').hide();

  // ...stuff...

  $('.sidebar').css({
    'background-color': 'pink'
  });
}

// good
function setSidebar() {
  var $sidebar = $('.sidebar');
  $sidebar.hide();

  // ...stuff...

  $sidebar.css({
    'background-color': 'pink'
  });
}
````
* For DOM queries use Cascading $('.sidebar ul') or parent > child $('.sidebar > ul').
````javascript
// bad
$('ul', '.sidebar').hide();

// bad
$('.sidebar').find('ul').hide();

// good
$('.sidebar ul').hide();

// good
$('.sidebar > ul').hide();

// good
$sidebar.find('ul').hide();
````

C. Exceptions, Slight Deviations

// 2.C.1.1
// Functions with callbacks
````javascript
foo(function() {
  // Note there is no extra space between the first paren
  // of the executing function call and the word "function"
});

// Function accepting an array, no space
foo([ "alpha", "beta" ]);
````
// 2.C.1.2
````javascript
// Function accepting an object, no space
foo({
  a: "alpha",
  b: "beta"
});

// Single argument string literal, no space
foo("bar");

// Inner grouping parens, no space
if ( !("foo" in obj) ) {

}
````

### When Hoisting is Appropriate
* Variable declarations get hoisted to the top of their scope, their assignment does not.
````javascript
// we know this wouldn't work (assuming there
// is no notDefined global variable)
function example() {
  console.log(notDefined); // => throws a ReferenceError
}

// creating a variable declaration after you
// reference the variable will work due to
// variable hoisting. Note: the assignment
// value of `true` is not hoisted.
function example() {
  console.log(declaredButNotAssigned); // => undefined
  var declaredButNotAssigned = true;
}

// The interpreter is hoisting the variable
// declaration to the top of the scope.
// Which means our example could be rewritten as:
function example() {
  var declaredButNotAssigned;
  console.log(declaredButNotAssigned); // => undefined
  declaredButNotAssigned = true;
}
````
* Anonymous function expressions hoist their variable name, but not the function assignment.
````javascript
function example() {
  console.log(anonymous); // => undefined

  anonymous(); // => TypeError anonymous is not a function

  var anonymous = function() {
    console.log('anonymous function expression');
  };
}
````
* Named function expressions hoist the variable name, not the function name or the function body.
````javascript
function example() {
  console.log(named); // => undefined

  named(); // => TypeError named is not a function

  superPower(); // => ReferenceError superPower is not defined

  var named = function superPower() {
    console.log('Flying');
  };
}

// the same is true when the function name
// is the same as the variable name.
function example() {
  console.log(named); // => undefined

  named(); // => TypeError named is not a function

  var named = function named() {
    console.log('named');
  }
}
````
* Function declarations hoist their name and the function body.
````javascript
function example() {
  superPower(); // => Flying

  function superPower() {
    console.log('Flying');
  }
}
````
E. Quotes

// Whether you prefer single or double shouldn't matter, there is no difference in how JavaScript parses them. What ABSOLUTELY MUST be enforced is consistency. Never mix quotes in the same project. Pick one style and stick with it.

* Use single quotes '' for strings
````javascript
// bad
var name = "Bob Parr";

// good
var name = 'Bob Parr';

// bad
var fullName = "Bob " + this.lastName;

// good
var fullName = 'Bob ' + this.lastName;
````
* Strings longer than 80 characters should be written across multiple lines using string concatenation. (and maintain indentation)

* If overused, long strings with concatenation could impact performance. jsPerf & Discussion

* The whitespace at the beginning of each line can't be safely stripped at compile time; whitespace after the slash will result in tricky errors; and while most script engines support this, it is not part of ECMAScript.

Use string concatenation instead:
````javascript
// bad
var errorMessage = 'This is a super long error that was thrown because of Batman. When you stop to think about how Batman had anything to do with this, you would get nowhere fast.';

// bad
var errorMessage = 'This is a super long error that was thrown because \
                    of Batman. When you stop to think about how Batman had anything to do \
                    with this, you would get nowhere \
                    fast.';
                    
// bad
var myString = 'A rather long string of English text, an error message \
                actually that just keeps going and going -- an error \
                message to make the Energizer bunny blush (right through \
                those Schwarzenegger shades)! Where was I? Oh yes, \
                you\'ve got an error and all the extraneous whitespace is \
                just gravy.  Have a nice day.';

// good
var errorMessage = 'This is a super long error that was thrown because ' +
                   'of Batman. When you stop to think about how Batman had anything to do ' +
                   'with this, you would get nowhere fast.';
// good
var myString = 'A rather long string of English text, an error message ' +
    'actually that just keeps going and going -- an error ' +
    'message to make the Energizer bunny blush (right through ' +
    'those Schwarzenegger shades)! Where was I? Oh yes, ' +
    'you\'ve got an error and all the extraneous whitespace is ' +
    'just gravy.  Have a nice day.';
````
* When programmatically building up a string, use Array#join instead of string concatenation. Mostly for IE
````javascript
var items,
    messages,
    length,
    i;

messages = [{
  state: 'success',
  message: 'This one worked.'
}, {
  state: 'success',
  message: 'This one worked as well.'
}, {
  state: 'error',
  message: 'This one did not work.'
}];

length = messages.length;

// bad
function inbox(messages) {
  items = '<ul>';

  for (i = 0; i < length; i++) {
    items += '<li>' + messages[i].message + '</li>';
  }

  return items + '</ul>';
}

// good
function inbox(messages) {
  items = [];

  for (i = 0; i < length; i++) {
    items[i] = messages[i].message;
  }

  return '<ul><li>' + items.join('</li><li>') + '</li></ul>';
}
````

## Properties
* Use dot notation when accessing properties.
````javascript
var luke = {
  jedi: true,
  age: 28
};

// bad
var isJedi = luke['jedi'];

// good
var isJedi = luke.jedi;
````
* Only use subscript notation [] when accessing properties with a variable.
````javascript
var luke = {
  jedi: true,
  age: 28
};

function getProp(prop) {
  return luke[prop];
}

var isJedi = getProp('jedi');
````

### Variables
* Use NAMES_LIKE_THIS for constant values.
* Use @const to indicate a constant (non-overwritable) pointer (a variable or property).
* Never use the const keyword as it's not supported in Internet Explorer.

*If a value is intended to be constant and immutable, it should be given a name in CONSTANT_VALUE_CASE. ALL_CAPS additionally implies @const (that the value is not overwritable).
Primitive types (number, string, boolean) are constant values.
Objects' immutability is more subjective — objects should be considered immutable only if they do not demonstrate observable state change. This is not enforced by the compiler.

* Always use var to declare variables. Not doing so will result in global variables. We want to avoid polluting the global namespace.
````javascript
// bad
superPower = new SuperPower();

// good
var superPower = new SuperPower();
````

F. End of Lines and Empty Lines

## Type Checking
````javascript
String:
typeof variable === "string"
````
````javascript
Number:
typeof variable === "number"
````
````javascript
Boolean:
typeof variable === "boolean"
````
````javascript
Object:
typeof variable === "object"
````
````javascript
Array:
Array.isArray( arrayLikeObject )
````
````javascript
Node:
elem.nodeType === 1
````
````javascript
null:
variable === null
````
````javascript
null or undefined:
variable == null
````
````javascript
Global Variables:
typeof variable === "undefined"
````
````javascript
Local Variables:
variable === undefined
````
````javascript
Properties:
object.prop === undefined
object.hasOwnProperty( prop )
"prop" in object
````

B. Coerced Types
// 3.B.1.1
````javascript
// `foo` has been declared with the value `0` and its type is `number`
var foo = 0;

// typeof foo;
// "number"
...

// Somewhere later in your code, you need to update `foo`
// with a new value derived from an input element
foo = document.getElementById("foo-input").value;

// If you were to test `typeof foo` now, the result would be `string`
// This means that if you had logic that tested `foo` like:
if ( foo === 1 ) {
  importantTask();
}
// `importantTask()` would never be evaluated, even though `foo` has a value of "1"
````

// 3.B.1.2
````javascript
// You can preempt issues by using smart coercion with unary + or - operators:
foo = +document.getElementById("foo-input").value;
//    ^ unary + operator will convert its right side operand to a number
// typeof foo;
// "number"

if ( foo === 1 ) {
  importantTask();
}
// `importantTask()` will be called
````

## 4. Conditional Evaluation
###Syntax
* keep the else clause in a if else condtional on the same line and the closing brace:
````javascript
// good
if ( condition ) {
    doSomething();
} else if ( otherCondition ) {
    somethingElse();
} else {
    otherThing();
}
````

* Lines should be broken into logical groups if it improves readability, such as splitting each expression of a ternary operator onto its own line even if both will fit on a single line.
````javascript
var baz = firstCondition( foo ) && secondCondition( bar ) ?
    qux( foo, bar ) :
    foo;
````
* When a conditional is too long to fit on one line, successive lines must be indented one extra level to distinguish them from the body.
````javascript
   if ( firstCondition() && secondCondition() &&
            thirdCondition() ) {
        doStuff();
    }
````

* Objects evaluate to true
* Undefined evaluates to false
* Null evaluates to false
* Booleans evaluate to the value of the boolean
* Numbers evaluate to false if +0, -0, or NaN, otherwise true
* Strings evaluate to false if an empty string '', otherwise true
*  An array is an object, objects evaluate to true
````javascript
if ([0]) {
  // true
}
````
* Use shortcuts
````javascript
// bad
if (name !== '') {
  // ...stuff...
}

// good
if (name) {
  // ...stuff...
}

// bad
if (collection.length > 0) {
  // ...stuff...
}

// good
if (collection.length) {
  // ...stuff...
}
````


````javascript
// 4.1.1
// When only evaluating that an array has length,
// instead of this:
if ( array.length > 0 ) ...

// ...evaluate truthiness, like this:
if ( array.length ) ...


// 4.1.2
// When only evaluating that an array is empty,
// instead of this:
if ( array.length === 0 ) ...

// ...evaluate truthiness, like this:
if ( !array.length ) ...


// 4.1.3
// When only evaluating that a string is not empty,
// instead of this:
if ( string !== "" ) ...

// ...evaluate truthiness, like this:
if ( string ) ...


// 4.1.4
// When only evaluating that a string _is_ empty,
// instead of this:
if ( string === "" ) ...

// ...evaluate falsy-ness, like this:
if ( !string ) ...


// 4.1.5
// When only evaluating that a reference is true,
// instead of this:
if ( foo === true ) ...

// ...evaluate like you mean it, take advantage of built in capabilities:
if ( foo ) ...


// 4.1.6
// When evaluating that a reference is false,
// instead of this:
if ( foo === false ) ...

// ...use negation to coerce a true evaluation
if ( !foo ) ...

// ...Be careful, this will also match: 0, "", null, undefined, NaN
// If you _MUST_ test for a boolean false, then use
if ( foo === false ) ...


// 4.1.7
// When only evaluating a ref that might be null or undefined, but NOT false, "" or 0,
// instead of this:
if ( foo === null || foo === undefined ) ...

// ...take advantage of == type coercion, like this:
if ( foo == null ) ...

// Remember, using == will match a `null` to BOTH `null` and `undefined`
// but not `false`, "" or 0
null == undefined
````
// 4.2.1
// Type coercion and evaluation notes
````javascript
// Prefer `===` over `==` (unless the case requires loose type evaluation)

// === does not coerce type, which means that:

"1" === 1;
// false

// == does coerce type, which means that:

"1" == 1;
// true


// 4.2.2
// Booleans, Truthies & Falsies

// Booleans:
true, false

// Truthy:
"foo", 1

// Falsy:
"", 0, null, undefined, NaN, void 0
````

## Switch Statements
* The usage of switch statements is generally discouraged, but can be useful when there are a large number of cases - especially when multiple cases can be handled by the same block, or fall-through logic (the default case) can be leveraged.
- Use a break for each case other than default.
- Align case statements with the switch.
````javascript
switch ( event.keyCode ) {
case $.ui.keyCode.ENTER:
case $.ui.keyCode.SPACE:
    x();
    break;
case $.ui.keyCode.ESCAPE:
    y();
    break;
default:
    z();
}
````

## Comments
* Comments are always preceded by a blank line. Comments start with a capital first letter, but don't require a period at the end, unless you're writing full sentences. There must be a single space between the comment token and the comment text.

Single line comments go over the line they refer to:
````javascript
// We need an explicit "bar", because later in the code foo is checked.
var foo = "bar";
 
// Even long comments that span
// multiple lines use the single
// line comment form.
````
* Inline comments are allowed as an exception when used to annotate special arguments in formal parameter lists or when needed to support a specific development tool:
````javascript
function foo( types, selector, data, fn, /* INTERNAL */ one ) {
    // Do stuff
}
````

* Use /** ... */ for multiline comments. Include a description, specify types and values for all parameters and return values.
````javascript
// bad
// make() returns a new element
// based on the passed in tag name
//
// @param <String> tag
// @return <Element> element
function make(tag) {

  // ...stuff...

  return element;
}

// good
/**
 * make() returns a new element
 * based on the passed in tag name
 *
 * @param <String> tag
 * @return <Element> element
 */
function make(tag) {

  // ...stuff...

  return element;
}
````
* Use // for single line comments. Place single line comments on a newline above the subject of the comment. Put an empty line before the comment.
````javascript
// bad
var active = true;  // is current tab

// good
// is current tab
var active = true;

// bad
function getType() {
  console.log('fetching type...');
  // set the default type to 'no type'
  var type = this._type || 'no type';

  return type;
}

// good
function getType() {
  console.log('fetching type...');

  // set the default type to 'no type'
  var type = this._type || 'no type';

  return type;
}
````
* Prefixing your comments with FIXME or TODO helps other developers quickly understand if you're pointing out a problem that needs to be revisited, or if you're suggesting a solution to the problem that needs to be implemented. These are different than regular comments because they are actionable. The actions are FIXME -- need to figure this out or TODO -- need to implement.
* Use // FIXME: to annotate problems
````javascript
function Calculator() {

  // FIXME: shouldn't use a global here
  total = 0;

  return this;
}
````
* Use // TODO: to annotate solutions to problems
````javascript
function Calculator() {

  // TODO: total should be configurable by an options param
  this.total = 0;

  return this;
}
````

The @const annotation on a variable or property implies that it is not overwritable. This is enforced by the compiler at build time. This behavior is consistent with the const keyword (which we do not use due to the lack of support in Internet Explorer).

A @const annotation on a method additionally implies that the method cannot not be overridden in subclasses.

A @const annotation on a constructor implies the class cannot be subclassed (akin to final in Java).
````javascript
\\ good
/**
 * Request timeout in milliseconds.
 * @type {number}
 */
goog.example.TIMEOUT_IN_MILLISECONDS = 60;

/**
 * Map of URL to response string.
 * @const
 */
MyClass.fetchedUrlCache_ = new goog.structs.Map();
/**
 * Class that cannot be subclassed.
 * @const
 * @constructor
 */
sloth.MyFinalClass = function() {};
````

## Whitespaces
* Use soft tabs set to 2 spaces. Never mix tabs and spaces.
````javascript
// bad
function() {
∙∙∙∙var name;
}

// bad
function() {
∙var name;
}

// good
function() {
∙∙var name;
}
````
* Place 1 space before the leading brace.
````javascript
// bad
function test(){
  console.log('test');
}

// good
function test() {
  console.log('test');
}

// bad
dog.set('attr',{
  age: '1 year',
  breed: 'Bernese Mountain Dog'
});

// good
dog.set('attr', {
  age: '1 year',
  breed: 'Bernese Mountain Dog'
});
````
* Set off operators with spaces.
````javascript
// bad
var x=y+5;

// good
var x = y + 5;
````
* End files with a single newline character.
````javascript
// bad
(function(global) {
  // ...stuff...
})(this);

// bad
(function(global) {
  // ...stuff...
})(this);↵
↵

// good
(function(global) {
  // ...stuff...
})(this);↵
````

* Use indentation when making long method chains.
````javascript
// bad
$('#items').find('.selected').highlight().end().find('.open').updateCount();

// good
$('#items')
  .find('.selected')
    .highlight()
    .end()
  .find('.open')
    .updateCount();

// bad
var leds = stage.selectAll('.led').data(data).enter().append('svg:svg').class('led', true)
    .attr('width',  (radius + margin) * 2).append('svg:g')
    .attr('transform', 'translate(' + (radius + margin) + ',' + (radius + margin) + ')')
    .call(tron.led);

// good
var leds = stage.selectAll('.led')
    .data(data)
  .enter().append('svg:svg')
    .class('led', true)
    .attr('width',  (radius + margin) * 2)
  .append('svg:g')
    .attr('transform', 'translate(' + (radius + margin) + ',' + (radius + margin) + ')')
    .call(tron.led);
````

### Semicolons
* Semicolons are optional, but you should always use them.
````javascript
// bad
(function() {
  var name = 'Skywalker'
  return name
})()

// good
(function() {
  var name = 'Skywalker';
  return name;
})();

// good (guards against the function becoming an argument when two files with IIFEs are concatenated)
;(function() {
  var name = 'Skywalker';
  return name;
})();
````

* Example of what happens when you don't use a semicolon
````javascript
// 1.
MyClass.prototype.myMethod = function() {
  return 42;
}  // No semicolon here.

(function() {
  // Some initialization code wrapped in a function to create a scope for locals.
})();


var x = {
  'i': 1,
  'j': 2
}  // No semicolon here.

// 2.  Trying to do one thing on Internet Explorer and another on Firefox.
// I know you'd never write code like this, but throw me a bone.
[ffVersion, ieVersion][isIE]();


var THINGS_TO_EAT = [apples, oysters, sprayOnCheese]  // No semicolon here.

// 3. conditional execution a la bash
-1 == resultOfOperation() || die();
````
1. JavaScript error - first the function returning 42 is called with the second function as a parameter, then the number 42 is "called" resulting in an error.
2. You will most likely get a 'no such property in undefined' error at runtime as it tries to call x[ffVersion, ieVersion][isIE]().
3. die is always called since the array minus 1 is NaN which is never equal to anything (not even if resultOfOperation() returns NaN) and THINGS_TO_EAT gets assigned the result of die().

Why this happened:
* JavaScript requires statements to end with a semicolon, except when it thinks it can safely infer their existence. In each of these examples, a function declaration or object or array literal is used inside a statement. The closing brackets are not enough to signal the end of the statement. Javascript never ends a statement if the next token is an infix or bracket operator.

This has really surprised people, so make sure your assignments end with semicolons.

* Semicolons should be included at the end of function expressions, but not at the end of function declarations. The distinction is best illustrated with an example:
````javascript
var foo = function() {
  return true;
};  // semicolon here.

function foo() {
  return true;
}  // no semicolon here.
````
## Naming
* In general, use functionNamesLikeThis, variableNamesLikeThis, ClassNamesLikeThis, EnumNamesLikeThis, methodNamesLikeThis, CONSTANT_VALUES_LIKE_THIS, foo.namespaceNamesLikeThis.bar, and filenameslikethis.js.
* Private properties and methods should be named with a trailing underscore.
* Protected properties and methods should be named without a trailing underscore (like public ones).

// 6.A.3.1
// Naming strings
````javascript
`dog` is a string
````

// 6.A.3.2
// Naming arrays
````javascript
`dogs` is an array of `dog` strings
````

// 6.A.3.3
// Naming functions, objects, instances, etc

camelCase; function and var declarations
* Use camelCase when naming objects, functions, and instances
````javascript
// bad
var OBJEcttsssss = {};
var this_is_my_object = {};
function c() {}
var u = new user({
  name: 'Bob Parr'
});

// good
var thisIsMyObject = {};
function thisIsMyFunction() {}
var user = new User({
  name: 'Bob Parr'
});
````


// 6.A.3.4
// Naming constructors, prototypes, etc.

PascalCase; constructor function
````javascript
// bad
function user(options) {
  this.name = options.name;
}

var bad = new user({
  name: 'nope'
});

// good
function User(options) {
  this.name = options.name;
}

var good = new User({
  name: 'yup'
});
````
* Use a leading underscore _ when naming private properties
````javascript
// bad
this.__firstName__ = 'Panda';
this.firstName_ = 'Panda';

// good
this._firstName = 'Panda';
````
* When saving a reference to this use _this.
````javascript
// bad
function() {
  var self = this;
  return function() {
    console.log(self);
  };
}

// bad
function() {
  var that = this;
  return function() {
    console.log(that);
  };
}

// good
function() {
  var _this = this;
  return function() {
    console.log(_this);
  };
}

// 6.A.3.5
// Naming regular expressions

rDesc = //;
```

// 6.A.3.6
// From the Google Closure Library Style Guide
````javascript
functionNamesLikeThis;
variableNamesLikeThis;
ConstructorNamesLikeThis;
EnumNamesLikeThis;
methodNamesLikeThis;
SYMBOLIC_CONSTANTS_LIKE_THIS;
````

## Using This

// 6.B.3
As a last resort, create an alias to this using self as an Identifier. This is extremely bug prone and should be avoided whenever possible.
````javascript
function Device( opts ) {
  var self = this;

  this.value = null;

  stream.read( opts.path, function( data ) {

    self.value = data;

  });

  setInterval(function() {

    self.emit("event");

  }, opts.freq || 100 );
}
````

### Performance and Memory Tuning
Always start with a server rendered page.

#Why?

tl;DR: Server rendering is not about SEO, it’s about performance. Consider the additional roundtrips to get scripts, styles, and subsequent API requests. In the future, considering HTTP 2.0 PUSH of resources.
The first thing I’m compelled to point out is a fairly common false dichotomy. That of “server-rendered apps vs single-page apps”. If we want to optimize for the best possible user experience and performance, giving up one or the other is never a good idea.

The reasons are fairly straightforward. The medium by which pages are transmitted, the internet, has a theoretical speed limit. This has been memorably illustrated by the famous essay/rant “It’s the latency, stupid” by Stuart Cheshire:

The distance from Stanford to Boston is 4320km.
The speed of light in vacuum is 300 x 10^6 m/s.
The speed of light in fibre is roughly 66% of the speed of light in vacuum.
The speed of light in fibre is 300 x 10^6 m/s * 0.66 = 200 x 10^6 m/s.
The one-way delay to Boston is 4320 km / 200 x 10^6 m/s = 21.6ms.
The round-trip time to Boston and back is 43.2ms.
The current ping time from Stanford to Boston over today’s Internet is about 85ms (…)
So: the hardware of the Internet can currently achieve within a factor of two of the speed of light.

The cited 85ms round-trip time between Boston and Stanford will certainly improve over time, and your own experiments right now might already show it. But it’s important to note that there’s a theoretical minimum of about 50ms between the two coasts.

The bandwidth capacity of your users’ connections might improve noticeably, as it steadily has, but the latency needle won’t move much at all. This means that minimizing the number of roundtrips you make to display information on page is essential to great user experience and responsiveness.

This becomes particularly relevant to point out considering the rise of JavaScript-driven applications that usually consist of no markup other than \<script\> and \<link\> tags beside an empty \<body\>. This class of application has received the name of “Single Page Applications” or “SPA”. As the name implies, there’s only one page the server consistently returns, and all the rest is figured out by your client side code.

Consider the scenario where the user navigates to http://app.com/orders/ after following a link or typing in the URL. At the time your application receives and processes the request, it already has important information about what’s going to be shown on that page. It could, for example, pre-fetch the orders from the database and include them in the response. In the case of most SPAs, a blank page and a \<script\> tag is returned instead, and another roundtrip will be made to get the scripts contents. So that then another roundtrip can be made to get the data needed for rendering.

Analysis of the HTML sent by the server for every page of a SPA in the wild
Analysis of the HTML sent by the server for every page of a SPA in the wild

At this point many developers consciously accept this tradeoff because they make sure the extra network hops happen only once for their users by sending the proper cache headers in the script and stylesheet responses. The general consensus is that it’s an acceptable tradeoff because once the bundle is loaded, you can then handle most of the user interaction (like transitions to other pages) without requesting additional pages or scripts.

However, even in the presence of a cache, there’s a performance penalty when considering script parsing and evaluation time. “Is jQuery Too Big For Mobile?” describes how even for jQuery alone this could be in the order of hundreds of milliseconds for certain mobile browsers.

What’s worse, usually no feedback whatsoever is given to the user while the scripts are loading. This results in a blank page displaying and then a sudden transition to a fully loaded page.

Most importantly, we usually forget that the current prevailing transport of internet data (TCP) starts slowly. This pretty much guarantees that most script bundles won’t be fetched in one roundtrip, making the situation described above even worse.

A TCP connection starts with an initial roundtrip for the handshake. If you’re using SSL, which happens to be important for safe script delivery, an additional two roundtrips are used (only one if the client is resuming a session). Only then can the server start sending data, but as it turns out, it does so slowly and incrementally.

A congestion control mechanism called slow start is built into the TCP protocol to send the data in a growing number of segments. This has two serious implications for SPAs:

Large scripts take a lot longer to download than it seems. As explained in the book “High Performance Browser Networking” by Ilya Grigorik, it takes “four roundtrips (…) and hundreds of milliseconds of latency, to reach 64 KB of throughput between the client and server”. In this example, considering a great internet connection between London and New York, it takes 225ms before TCP is able to reach the maximum packet size.
Since this rule applies also for the initial page download, it makes the initial content that comes rendered with the page all that much more important. As Paul Irish concludes in his presentation “Delivering the Goods”, the first 14kb are crucially important. This is a helpful illustration of the amount of data the server can send in each round-trip over time:

How many KB a server can send for each phase of the connection by segments.
How many KB a server can send for each phase of the connection by segments

Websites that deliver content (even if it’s only the basic layout without the data) within this window will seem extremely responsive. In fact, to many authors of fast server-side applications JavaScript is deemed unneeded or as something to be used sparingly. This bias is further strengthened if the app has a fast backend and data sources and its servers located near users (CDN).

The role of the server in assisting and speeding up content presentation is certainly application-specific. The solution is not always as straightforward as “render the entire page on the server”.

In some cases, parts of the page that are not essential to what the user is likely after are better left out of the initial response and fetched later by the client. Some applications, for example, opt to render the “shell” of the page to respond immediately. Then they fetch different portions of the page in parallel. This allows for great responsiveness even in a situation with slow legacy backend services. For some pages, pre-rendering the content that’s “above the fold” is also a viable option.

Making a qualitative assessment of scripts and styles based on the information the server has about the the session, the user and the URL is absolutely crucial. The scripts that deal with sorting orders will obviously be more important to /orders than the logic to deal with the settings page. Maybe less intuitively, one could also make a distinction between “structural CSS” and the “skin/theme CSS”. The former might be required by the JavaScript code, so it should block, but the latter could be loaded asynchronously.

A neat example of a SPA that does not incur in extra roundtrip penalties is a proof-of-concept clone of StackOverflow in 4096 bytes (which can theoretically be delivered on the first post-handshake roundtrip of a TCP connection!). It manages to pull this off at the expense of cacheability, by inlining all the assets within the response. With SPDY or HTTP/2 server push, it should be theoretically possible to deliver client code that’s cacheable in a single hop. For the time being, rendering part or all of the page on the server is the most common solution to avoiding extra roundtrips.

Proof-of-concept SPA with inlined CSS and JS\<br /\>
that doesn’t incur in extra roundtrips
Proof-of-concept SPA with inlined CSS and JS that doesn’t incur in extra roundtrips

A flexible enough system that can share rendering code between browser and server and provides tools for progressively loading scripts and styles will probably eliminate the colloquial distinction between websites and webapps. Both are reigned by the same UX principles. A blog and a CRM are fundamentally not that different. They have URLs, navigation, they show data to the user. Even a spreadsheet application, which traditionally relies a lot more on client side functionality, first needs to show the user the data he’s interested in modifying. And doing so in the least number of network roundtrips is paramount.

In my view, the major tradeoffs in performance seen in many widely deployed systems these days have to do with the progressive accumulation of complexity in the stack. Technologies like JavaScript and CSS were added over time. Their popularity increased over time as well. Only now can we appreciate the impact of the different ways they’ve been applied. Some of this is addressed by improving protocols (as shown by the ongoing enhancements seen in SPDY and QUIC), but the application layer is where most of the benefits will come from.

It’s helpful to refer to some of the initial discussions around the design of the initial WWW and HTML to understand this. In particular, this mailing list thread from 1997 proposing the addition of the <img> tag to HTML. Marc Andreessen re-iterates the importance of serving information fast:

“If a document has to be pieced together on the fly, it could get arbitrarily complex, and even if that were limited, we’d certainly start experiencing major hits on performance for documents structured in this way. This essentially throws the single-hop principle of WWW out the door (well, IMG does that too, but for a very specific reason and in a very limited sense) — are we sure we want to do that?”

### Security

https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project
A1 Injection
A2 Broken Authentication and Session Management (was formerly 2010-A3)
A3 Cross-Site Scripting (XSS) (was formerly 2010-A2)
A4 Insecure Direct Object References
A5 Security Misconfiguration (was formerly 2010-A6)
A6 Sensitive Data Exposure (2010-A7 Insecure Cryptographic Storage and 2010-A9 Insufficient Transport Layer Protection were merged to form 2013-A6)
A7 Missing Function Level Access Control (renamed/broadened from 2010-A8 Failure to Restrict URL Access)
A8 Cross-Site Request Forgery (CSRF) (was formerly 2010-A5)
A9 Using Components with Known Vulnerabilities (new but was part of 2010-A6 – Security Misconfiguration)
A10 Unvalidated Redirects and Forwards

## Production Topics
* Modifying builtins like Object.prototype and Array.prototype are strictly forbidden. Modifying other builtins like Function.prototype is less dangerous but still leads to hard to debug issues in production and should be avoided.

## License

(The MIT License)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the 'Software'), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
