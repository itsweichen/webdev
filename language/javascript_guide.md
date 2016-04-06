## JavaScript

> [Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)

### Intro

* JavaScript vs. ECMAScript


### Grammar and types

**Basics**

* case-sensitive, uses Unicode character set 

**Decalrations**

Three ways

* `var`
  * simply assigning it a value declares a global variable. (x)
* `let` - block scope local variable
* `const`

Evaluating variables

* no initial value -> `undefined`
  * converts to `NaN` when used in numeric context
* `null` variable - 0 in numeric contexts and false in boolean contexts

Variable scope

* *global* variable (declared outside of any function) vs. *local* var (declared within a function)
* JavaScript before ECMAScript 6 does not have block statement scope; variable within a block is local to the *function*
* `let` in ECMAScript 6

Variable hoisting

* can use a var declared later
* hoisted var will return `undefined` (instead of getting an exception)
  * interpreted as not-initialized
* BEST PRACTICE: `var` statement should be placed as near to the top of the function as possible.

Global Variable

* Global var are properties of the *global object*; `window` is a global object.


Constant

* `const prefix = '212';`
* Read-only; but object attributes can be changed.

```javascript
const MY_OBJECT = {"key": "value"};
MY_OBJECT.key = "otherValue";
```

**Data structures and types**

Data types

* Six that are primitives: Boolean, null, undefined, Number, String, Symbol (new in ECMAScript 6)
* OBject

Auto conversion

* Dynamically typed language
* `+`: numerical -> string () // not in python
* but others operators won't

```javascript
"37" - 7 // 30
"37" + 7 // "377"
```

Converting strings -> numbers

* Methods
  * `parseInt()`
    * Best practice: always include the radix parameter `parseInt("15*3", 10);`
  * `parseFloat()`
* Use `+`
* A stricter way to parse int (use regexp)

> [The differences](http://stackoverflow.com/questions/175739/is-there-a-built-in-way-in-javascript-to-check-if-a-string-is-a-valid-number)

**Literals**

> You use literals to represent values in JavaScript. These are **fixed** values, not variables, that you *literally* provide in your script. 

* Array
* Boolean
* Floating-point
* Integers
* Object
* RegExp
* String

Array

* Extra commas (except for the last one) -> an item that is `undefined`

Boolean

* Object wrapper for a boolean value
* DO NOT USE IT FOR CONDITIONAL STATEMENT - Any object whose value is not `undefined` or `null` evaluates to `true`.

Integers

Floating-point literals

Object literals

* pairs of key-value

```javascript
var car = { manyCars: {a: "Saab", "b": "Jeep"}, 7: "Mazda" };

console.log(car.manyCars.b); // Jeep
console.log(car[7]); // Mazda
```

RegExp

* pattern enclosed between slashes.

String literals

* Can call any methods of the String object on a string literal value - JavaScript auto converts it to a temporary String object.


### Control flow and error handling
