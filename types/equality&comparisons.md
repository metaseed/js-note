
* == and === are called equality operators. sometime we call them equality (==) and identity (===) operators.
* === is *strict* equality operator; == is *standard* equality operator.
* for ==: as JavaScript is a weakly typed language

'==': bool ToNumber, string ToNumber, null == undefined, object ToPrimitive (call toString and valueOf)

## Primitave types

```javascript
""           ==   "0"           // false: same type as '==='
0            ==   ""            // true: sting to number
0            ==   "0"           // true: --
1            ==   true          // true: bool to number
false        ==   "false"       // false: bool to number, string(false) to number.(error) ***
false        ==   "0"           // true: bool to number
false        ==   undefined     // false
false        ==   null          // false
null         ==   undefined     // true: null == undefined
" \t\r\n"    ==   0             // true: string to number
10           ==   '10';         // true: string to number
10           ==   '+10 ';       // true: string to number
10           ==   '010';        // true: string to number
isNaN(null)  ==   false;        // true: null to 0
10           ==     010;        //false: 010 is 8.(es5 octal number)
10           ==     '-10';      //false: stirng to number
```

> 1. the use of == is widely regarded as bad practice.
> 2. performance impact of '==': type conversion

```javascript
""           ===   "0"           // false
0            ===   ""            // false
0            ===   "0"           // false
false        ===   "false"       // false
false        ===   "0"           // false
false        ===   undefined     // false
false        ===   null          // false
null         ===   undefined     // false
NaN          ===   NaN           // false  Object.is(NaN, NaN) true
" \t\r\n"    ===   0             // false  Object.is(+0, -0) false
+0           ===   -0            // true
```
## With Objects

```javascript
{} === {};                      // false
var foo = {}; foo === foo;      // true
new String('foo') === 'foo';    // false: object and string
Number(10) === 10;              // True, Number and Number
new Number(10) === 10;          // False, Object and Number
new Number(10) + 0 === 10;      // True, due to implicit conversion

```
## Conclution

1. use ===
2. explicitly convert(coerce, cast) types when need:
    ```javascript
    '' + 10 === '10';       // true: + to sting.
    +'10' === 10;           // true: + to number.
    // to boolean
    !!'foo';                // true
    !!'';                   // false
    !!'0';                  // true
    !!'1';                  // true
    !!'-1'                  // true
    !!{};                   // true
    !!true;                 // true
    ```
##　Sameness Comparisons


// https://developer.mozilla.org/en/docs/Web/JavaScript/Equality_comparisons_and_sameness
// https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Operators/Comparison_Operators