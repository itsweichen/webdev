# JavaScript

> [Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)


## Intro

* JavaScript vs. ECMAScript


## Grammar and types

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

* *global* variable vs. *local* var (declared within a function)
* JavaScript before ECMAScript 6 does not have block statement scope; variable within a block is local to the *function*
* `let` in ECMAScript 6

Variable hoisting

* can use a var declared later
* hoisted var will return `undefined` (instead of getting an exception)
  * interpreted as not-initialized
* BEST PRACTICE: `var` statement should be placed as near to the top of the function as possible.


