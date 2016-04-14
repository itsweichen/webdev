## JavaScript cheatsheet

> [Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)

### Intro

* JavaScript vs. ECMAScript


### Grammar and types

**Basics**

* case-sensitive, uses Unicode character set 

**Decalrations**

Three ways

* `var`
  * function scope
  * simply assigning it a value declares a global variable. (not a very good way)
* `let`
  * block scope local variable
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

```
// 【奇幻语言JavaScript之Variable Hoist】
```

* can use a var declared later
* hoisted var will return `undefined` (instead of getting an exception)
  * interpreted as not-initialized
* BEST PRACTICE: `var` statement should be placed as near to the top of the function as possible.

Global Variable

* Global var are properties of the *global object*; `window` is a global object.


Constant

* `const prefix = '212';`
* Read-only. (but object attributes can be changed)

```javascript
const MY_OBJECT = {"key": "value"};
MY_OBJECT.key = "otherValue";
```

**Data structures and types**

Data types

* Six that are primitives
  * Boolean, null, undefined, Number, String, Symbol (new in ECMAScript 6)
* Object

Auto conversion

* Dynamically typed language
* string `+` numerical -> string (not in python)
* but others operators won't

```javascript
"37" - 7 // 30
"37" + 7 // "377"
```

Converting strings -> numbers

* Methods
  * `parseInt()`
    * BEST PRACTICE: always include the radix parameter `parseInt("15*3", 10);`
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

**Exception handling**

* `throw`
* `try...catch`

Utilizing `Error` objects

**Promise***

* New in ECMAScript 6, allowing you to control the flow of deferred and asynchronous operations.

### Loops and iteraction

**`label` statement**

* identifier that lets you refer to it elsewhere in your program.
* can be used to mark a loop and then use `break` or `continue` to indicate which loop (for example, nested loops)

**for...in statement** and **for...of statement**

```javascript
let arr = [3, 5, 7];
arr.foo = "hello";

for (let i in arr) {
   console.log(i); // logs "0", "1", "2", "foo"
}

for (let i of arr) {
   console.log(i); // logs "3", "5", "7"
}
```

* Better to use `for` loop to iterate over arrays, because `for...in` statement will also return the name of user-defined properties (as they are objects).

### Function

* **Primitives are passed by *value* while objects are passed by *reference*.**

**Function expressions**

```javascript
var square = function(number) {return number * number}
var x = square(4)
```

* anonymous
* can also add a name in order to call itself
* convenient when passing a function as an argument to another function

```javascript
function map(f, a){
  var result = [], i;
  for (i=0; i != a.length; i++)
    result[i] = f(a[i])
   return result;
}

map(function(x){return x*x*x}, [0, 1, 2, 5]); // [0, 1, 8, 125]
```

* can use `Function` constructor to create functions from a string a runtime. (Every function is actually a `Function` object in JavaScript.)

**Calling functions**

* Function declaration can be hoisted.

```javascript
// 【奇幻语言JavaScript之Function Hoist】
console.log(square(5));
/* ... */
function square(n) { return n*n }
// log: 25
// won't work with other syntax like square=function(){}
```

> More: call function dynamically, or the number of arguments to a function vary... Functions are objects and they have methods. See apply() method.

**Function scope**

* A function can access all variables and functions defined inside the scope in which it is defined.


```javascript
// 【奇幻语言JavaScript之Nested Call】
function outside(x) {
  function inside(y) {
    return x + y;
  }
  return inside;
}

fn_inside = outside(3); // Think of it like: give me a function that adds 3 to whatever you give it
result = fn_inside(5); // returns 8

result1 = outside(3)(5); // returns 8
```


### Indexed collections





```javascript
// 【奇幻语言JavaScript之Array】
a = []; // [], length=0
a[2] = 1; // [undefined, undefined, 1], length=3
a.length = 2; // [undefined, undefined], length=2
```

### Keyed collections

* `Map` object introduced in ECMAScript 6.
  * Comparisons between using `Map` and `Object`
  * Keys of an object are `Strings` and they can be of any value for `Map`
* `WeakMap`
  * Keys are objects only
  * "weak": target of garbage collection if there is no reference to the key object any more


