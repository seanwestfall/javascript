javascript
==========

A Practical Style Guide to Everyday Javascript.

Here in lies a guide to writing principled, consistent, and idiomatic JavaScript.

By Sean Westfall

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
  1. [Performance](#performance)
  1. [Resources](#resources)
  1. [In the Wild](#in-the-wild)
  1. [Translation](#translation)
  1. [The JavaScript Style Guide Guide](#the-javascript-style-guide-guide)
  1. [Contributors](#contributors)
  1. [License](#license)

## Resources

# Official Documentation
### [Annotated ECMAScript 5.1](http://es5.github.com/)
### [EcmaScript Language Specification, 5.1 Edition](http://ecma-international.org/ecma-262/5.1/)
### [EcmaScript Language Specification, ECMA-262 6th Edition *Draft*](https://people.mozilla.org/~jorendorff/es6-draft.html)

## Syntax
// 2.B.1.2
// Using only one `var` per scope (function) promotes readability
// and keeps your declaration list free of clutter (also saves a few keystrokes)
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

// 2.B.1.3
// var statements should always be in the beginning of their respective scope (function).


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

## ES6 Standard 
// 2.B.1.4
// const and let, from ECMAScript 6, should likewise be at the top of their scope (block).

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

// 2.B.2.1
// Named Function Declaration
function foo( arg1, argN ) {

}

// Usage
foo( arg1, argN );


// 2.B.2.2
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


// 2.B.2.3
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

// 2.B.2.4
// Constructor Declaration
function FooBar( options ) {

  this.options = options;
}

// Usage
var fooBar = new FooBar({ a: "alpha" });

fooBar.options;
// { a: "alpha" }

C. Exceptions, Slight Deviations

// 2.C.1.1
// Functions with callbacks
foo(function() {
  // Note there is no extra space between the first paren
  // of the executing function call and the word "function"
});

// Function accepting an array, no space
foo([ "alpha", "beta" ]);

// 2.C.1.2
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

E. Quotes

// Whether you prefer single or double shouldn't matter, there is no difference in how JavaScript parses them. What ABSOLUTELY // MUST be enforced is consistency. Never mix quotes in the same project. Pick one style and stick with it.

F. End of Lines and Empty Lines

## Type Checking
````
String:
typeof variable === "string"
````
````
Number:
typeof variable === "number"
````
````
Boolean:
typeof variable === "boolean"
````
````
Object:
typeof variable === "object"
````
Array:
Array.isArray( arrayLikeObject )
````
