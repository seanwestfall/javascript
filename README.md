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
- type: set of data value.
- primitive value: member of one of the types Undefined, Null, Boolean, Number, or String.
- object: member of the type Object.
- constructor: Function object that creates and initialises objects.
- prototype: object that provides shared properties for other objects.
- native object: object in an ECMAScript implementation whose semantics are fully defined by this specification rather than by the host environment.
- built-in object: object supplied by an ECMAScript implementation, independent of the host environment, that is present at the start of the execution of an ECMAScript program.
- host object: object supplied by the host environment to complete the execution environment of ECMAScript.
- undefined value: primitive value used when a variable has not been assigned a value.
- Undefined type: type whose sole value is the undefined value.
- null value: primitive value that represents the intentional absence of any object value.
- Null type: type whose sole value is the null value.
- Boolean value: member of the Boolean type. There are only two Boolean values, true and false.
- Boolean type: type consisting of the primitive values true and false.
- Boolean object: member of the Object type that is an instance of the standard built-in Boolean constructor.
- String value: primitive value that is a finite ordered sequence of zero or more 16-bit unsigned integer.
- String type: set of all possible String values.
- String object: member of the Object type that is an instance of the standard built-in String constructor.
- Number value: primitive value corresponding to a double-precision 64-bit binary format IEEE 754 value.
- Number type: set of all possible Number values including the special “Not-a-Number” (NaN) values, positive infinity, and negative infinity.
- Number object: member of the Object type that is an instance of the standard built-in Number constructor.
- Infinity: Number value that is the positive infinite Number value.
- NaN: Number value that is a IEEE 754 “Not-a-Number” value.
- function: member of the Object type that is an instance of the standard built-in Function constructor and that may be invoked as a subroutine.
- built-in function: built-in object that is a function.
- property: association between a name and a value that is a part of an object.
- method: function that is the value of a property.
- built-in method: method that is a built-in function. Sandard built-in methods are defined in the ECMA specification, and an ECMAScript implementation may specify and provide other additional built-in methods.
- attribute: internal value that defines some characteristic of a property.
- own property: property that is directly contained by its object.
- inherited property: property of an object that is not an own property but is a property (either own or inherited) of the object’s prototype.

**[⬆ back to top](#table-of-contents)**
## Using Strict

**[⬆ back to top](#table-of-contents)**
## Using ES6

**[⬆ back to top](#table-of-contents)**
## Types and Syntax
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

### Variable Types
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

### Complex Types

#### Functions
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

#### Arrays
* Use Array and Object literals instead of Array and Object constructors. Array constructors are error-prone due to their arguments, because of this, if someone changes the code to pass 1 argument instead of 2 arguments, the array might not have the expected length. To avoid these kinds of weird cases, always use the more readable array literal.
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

* [Array.prototype.every()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every)

Use `every()` when checking the condition of an array.

or use `some()`

* [Array.prototype.some()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some)

When checking every element in an array for a condition.

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

* Object constructors don't have the same problems, but for readability and consistency object literals should be used.
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
* Objects evaluate to true
* Undefined evaluates to false
* Null evaluates to false
* Booleans evaluate to the value of the boolean
* Numbers evaluate to false if +0, -0, or NaN, otherwise true
* Strings evaluate to false if an empty string '', otherwise true
*  An array is an object, objects evaluate to true
```javascript
if ([0]) {
  // true
}
````
* Use shortcuts
```javascript
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

```javascript
// When only evaluating that an array has length,
// instead of this:
if ( array.length > 0 ) ...

// ...evaluate truthiness, like this:
if ( array.length ) ...

// When only evaluating that an array is empty,
// instead of this:
if ( array.length === 0 ) ...

// ...evaluate truthiness, like this:
if ( !array.length ) ...

// When only evaluating that a string is not empty,
// instead of this:
if ( string !== "" ) ...

// ...evaluate truthiness, like this:
if ( string ) ...

// When only evaluating that a string _is_ empty,
// instead of this:
if ( string === "" ) ...

// ...evaluate falsy-ness, like this:
if ( !string ) ...

// When only evaluating that a reference is true,
// instead of this:
if ( foo === true ) ...

// ...evaluate like you mean it, take advantage of built in capabilities:
if ( foo ) ...

// When evaluating that a reference is false,
// instead of this:
if ( foo === false ) ...

// ...use negation to coerce a true evaluation
if ( !foo ) ...

// ...Be careful, this will also match: 0, "", null, undefined, NaN
// If you _MUST_ test for a boolean false, then use
if ( foo === false ) ...

// When only evaluating a ref that might be null or undefined, but NOT false, "" or 0,
// instead of this:
if ( foo === null || foo === undefined ) ...

// ...take advantage of == type coercion, like this:
if ( foo == null ) ...

// Remember, using == will match a `null` to BOTH `null` and `undefined`
// but not `false`, "" or 0
null == undefined
````

**[⬆ back to top](#table-of-contents)**
## Type Casting & Coercion
A. Actual Types

    String:

        typeof variable === "string"

    Number:

        typeof variable === "number"

    Boolean:

        typeof variable === "boolean"

    Object:

        typeof variable === "object"

    Array:

        Array.isArray( arrayLikeObject )
        (wherever possible)

    Node:

        elem.nodeType === 1

    null:

        variable === null

    null or undefined:

        variable == null

    undefined:

      Global Variables:

        typeof variable === "undefined"

      Local Variables:

        variable === undefined

      Properties:

        object.prop === undefined
        object.hasOwnProperty( prop )
        "prop" in object

B. Coerced Types

Consider the implications of the following...

Given this HTML:

```html
<input type="text" id="foo-input" value="1">
```

```javascript

    // 3.B.1.1

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


    // 3.B.1.2

    // You can preempt issues by using smart coercion with unary + or - operators:

    foo = +document.getElementById("foo-input").value;
    //    ^ unary + operator will convert its right side operand to a number

    // typeof foo;
    // "number"

    if ( foo === 1 ) {

      importantTask();

    }

    // `importantTask()` will be called
```

    Here are some common cases along with coercions:
    
```javascript

    // 3.B.2.1

    var number = 1,
      string = "1",
      bool = false;

    number;
    // 1

    number + "";
    // "1"

    string;
    // "1"

    +string;
    // 1

    +string++;
    // 1

    string;
    // 2

    bool;
    // false

    +bool;
    // 0

    bool + "";
    // "false"
```
    
```javascript
    var number = 1,
      string = "1",
      bool = true;

    string === number;
    // false

    string === number + "";
    // true

    +string === number;
    // true

    bool === number;
    // false

    +bool === number;
    // true

    bool === string;
    // false

    bool === !!string;
    // true
```

```javascript
    var array = [ "a", "b", "c" ];

    !!~array.indexOf("a");
    // true

    !!~array.indexOf("b");
    // true

    !!~array.indexOf("c");
    // true

    !!~array.indexOf("d");
    // false

    // Note that the above should be considered "unnecessarily clever"
    // Prefer the obvious approach of comparing the returned value of
    // indexOf, like:

    if ( array.indexOf( "a" ) >= 0 ) {
      // ...
    }
```

```javascript
    var num = 2.5;

    parseInt( num, 10 );

    // is the same as...

    ~~num;

    num >> 0;

    num >>> 0;

    // All result in 2


    // Keep in mind however, that negative numbers will be treated differently...

    var neg = -2.5;

    parseInt( neg, 10 );

    // is the same as...

    ~~neg;

    neg >> 0;

    // All result in -2
    // However...

    neg >>> 0;

    // Will result in 4294967294
```

// Type coercion and evaluation notes
````javascript
// Prefer `===` over `==` (unless the case requires loose type evaluation)

// === does not coerce type, which means that:

"1" === 1;
// false

// == does coerce type, which means that:

"1" == 1;
// true

// Booleans, Truthies & Falsies

// Booleans:
true, false

// Truthy:
"foo", 1

// Falsy:
"", 0, null, undefined, NaN, void 0
````

**[⬆ back to top](#table-of-contents)**
## Naming
* In general, use 
```javascript
functionNamesLikeThis
variableNamesLikeThis
ClassNamesLikeThis
EnumNamesLikeThis
methodNamesLikeThis
CONSTANT_VALUES_LIKE_THIS
foo.namespaceNamesLikeThis.bar
filenameslikethis.js
```
* Private properties and methods should be named with a trailing underscore.
* Protected properties and methods should be named without a trailing underscore (like public ones).

* From the Google Closure Library Style Guide
```javascript
functionNamesLikeThis;
variableNamesLikeThis;
ConstructorNamesLikeThis;
EnumNamesLikeThis;
methodNamesLikeThis;
SYMBOLIC_CONSTANTS_LIKE_THIS;
```

* Naming strings
```javascript
`dog` is a string
```

* Naming arrays
```javascript
`dogs` is an array of `dog` strings
```

* Naming functions, objects, instances, etc

camelCase; function and var declarations
* Use camelCase when naming objects, functions, and instances
```javascript
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
```
* Naming constructors, prototypes, etc.

PascalCase; constructor function
```javascript
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
```
* Use a leading underscore _ when naming private properties
```javascript
// bad
this.__firstName__ = 'Panda';
this.firstName_ = 'Panda';

// good
this._firstName = 'Panda';
```
* When saving a reference to this use _this.
```javascript
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

// Naming regular expressions

rDesc = //;
```

**[⬆ back to top](#table-of-contents)**
## Proper Spacing
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

**[⬆ back to top](#table-of-contents)**
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
These are known issues with specific popular web browsers:

*All Browsers*
- Combining overflow: hidden and CSS transforms in z-space causes unexpected results. Unfortunately, this is a bug common in the majority of currently available browser implementations. The inclusion of overflow: hidden causes the browser to not interpret z depth correctly when a perspective is set. This issue is referenced on StackOverflow and is blogged about here.

- Frame-rate in the browser will take a serious hit when semi-transparent windows lie over them. Be careful when organizing the windows on your desktop, as this can lead to very confusing performance drops.

*Chrome*

*Firefox*

*Safari*
- Garbage collection in Safari tends to be more pronouced. If an application is performant in Chrome and Firefox but not on Safari, it may be fixable by having more intelligent memory allocation.

*iOS7 iPad*
- iPads that are running iOS7 miscalculate window.innerHeight when they are in landscape orientation. This poses issues for developers relying on the window's size for laying-out components. This issue is referenced on StackOverflow.

*Android*
- 
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
