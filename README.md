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
  1. [Bitwise Operators](#bitwise) 
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

# Official Documentation
### [Annotated ECMAScript 5.1](http://es5.github.com/)
### [EcmaScript Language Specification, 5.1 Edition](http://ecma-international.org/ecma-262/5.1/)
### [EcmaScript Language Specification, ECMA-262 6th Edition *Draft*](https://people.mozilla.org/~jorendorff/es6-draft.html)

# JavaScript Books Worth Reading:
Secrets of the JavaScript Ninja by John Resig and Bear Bibeault
JavaScript: The Good Parts by Douglas Crockford
Effective JavaScript: 68 Specific Ways to Harness the Power of JavaScript by David Herman
High Performance JavaScript by Nicholas C. Zakas
Eloquent JavaScript: A Modern Introduction to Programming by Marijn Haverbeke
JavaScript Patterns by Stoyan Stefanov
Functional JavaScript: Introducing Functional Programming with Underscore.js by Michael Fogus

# JavaScript Blogs Worth Reading:
http://perfectionkills.com/
http://raganwald.com/
http://jlongster.com/

# Other Awesome Styles Guides You Should Read
https://github.com/rwaldron/idiomatic.js/
https://github.com/airbnb/javascript
https://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml

## Types:
Primitives: When you access a primitive type you work directly on its value
 * string
 * number
 * boolean
 * null
 * undefined
````
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
````
var foo = [1, 2],
    bar = foo;

bar[0] = 9;
````

## Syntax
###Objects
````
// bad
var item = new Object();

// good
var item = {};
````

###Arrays
````
// bad
var items = new Array();

// good
var items = [];
````
````
var someStack = [];
// bad
someStack[someStack.length] = 'abracadabra';
// good
someStack.push('abracadabra');
````
````
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

### Functions

// 2.B.1.2
// Using only one `var` per scope (function) promotes readability
// and keeps your declaration list free of clutter (also saves a few keystrokes)
````
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
````
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

* Assign variables at the top of their scope. This helps avoid issues with variable declaration and assignment hoisting related issues.
````
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

* Never declare a function in a non-function block (if, while, etc). Assign the function to a variable instead. Browsers will allow you to do it, but they all interpret it differently, which is bad news bears.
````
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
````
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
````
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

````
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
````
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
````
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
// 2.B.2.1
````
// Named Function Declaration
function foo( arg1, argN ) {

}

// Usage
foo( arg1, argN );
````

// 2.B.2.2
````
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
````
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
````
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
````
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
````
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
````
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
````
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
````
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
* Prefix jQuery object variables with a $.
````
// bad
var sidebar = $('.sidebar');

// good
var $sidebar = $('.sidebar');
````
* Cache jQuery lookups.
````
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
````
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
````
foo(function() {
  // Note there is no extra space between the first paren
  // of the executing function call and the word "function"
});

// Function accepting an array, no space
foo([ "alpha", "beta" ]);
````
// 2.C.1.2
````
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
````
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
````
function example() {
  console.log(anonymous); // => undefined

  anonymous(); // => TypeError anonymous is not a function

  var anonymous = function() {
    console.log('anonymous function expression');
  };
}
````
* Named function expressions hoist the variable name, not the function name or the function body.
````
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
````
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
````
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
````
// bad
var errorMessage = 'This is a super long error that was thrown because of Batman. When you stop to think about how Batman had anything to do with this, you would get nowhere fast.';

// bad
var errorMessage = 'This is a super long error that was thrown because \
                    of Batman. When you stop to think about how Batman had anything to do \
                    with this, you would get nowhere \
                    fast.';

// good
var errorMessage = 'This is a super long error that was thrown because ' +
                   'of Batman. When you stop to think about how Batman had anything to do ' +
                   'with this, you would get nowhere fast.';
````
* When programmatically building up a string, use Array#join instead of string concatenation. Mostly for IE
````
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
````
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
````
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
* Always use var to declare variables. Not doing so will result in global variables. We want to avoid polluting the global namespace.
````
// bad
superPower = new SuperPower();

// good
var superPower = new SuperPower();
````

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
````
Array:
Array.isArray( arrayLikeObject )
````
````
Node:
elem.nodeType === 1
````
````
null:
variable === null
````
````
null or undefined:
variable == null
````
````
Global Variables:
typeof variable === "undefined"
````
````
Local Variables:
variable === undefined
````
````
Properties:
object.prop === undefined
object.hasOwnProperty( prop )
"prop" in object
````

B. Coerced Types
// 3.B.1.1
````
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
````
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
* Objects evaluate to true
* Undefined evaluates to false
* Null evaluates to false
* Booleans evaluate to the value of the boolean
* Numbers evaluate to false if +0, -0, or NaN, otherwise true
* Strings evaluate to false if an empty string '', otherwise true
*  An array is an object, objects evaluate to true
````
if ([0]) {
  // true
}
````
* Use shortcuts
````
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


````
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
````
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

## Comments
* Use /** ... */ for multiline comments. Include a description, specify types and values for all parameters and return values.
````
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
````
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
````
function Calculator() {

  // FIXME: shouldn't use a global here
  total = 0;

  return this;
}
````
* Use // TODO: to annotate solutions to problems
````
function Calculator() {

  // TODO: total should be configurable by an options param
  this.total = 0;

  return this;
}
````

## Whitespaces
* Use soft tabs set to 2 spaces. Never mix tabs and spaces.
````
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
````
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
````
// bad
var x=y+5;

// good
var x = y + 5;
````
* End files with a single newline character.
````
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
````
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
````
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

## Naming
````
// 6.A.3.1
// Naming strings

`dog` is a string


// 6.A.3.2
// Naming arrays

`dogs` is an array of `dog` strings


// 6.A.3.3
// Naming functions, objects, instances, etc

camelCase; function and var declarations
* Use camelCase when naming objects, functions, and instances
````
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
````
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
````
// bad
this.__firstName__ = 'Panda';
this.firstName_ = 'Panda';

// good
this._firstName = 'Panda';
````
* When saving a reference to this use _this.
````
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
````

// 6.A.3.5
// Naming regular expressions

rDesc = //;


// 6.A.3.6
// From the Google Closure Library Style Guide

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
````
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

