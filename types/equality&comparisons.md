* == and === are called equality operators.
* === is strict equality operator.
## Primitave types
bool -> string -> number
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
```

> 1. the use of == is widely regarded as bad practice.
> 2. performance impact of '==': type conversion: bool -> string -> number

```javascript
""           ===   "0"           // false
0            ===   ""            // false
0            ===   "0"           // false
false        ===   "false"       // false
false        ===   "0"           // false
false        ===   undefined     // false
false        ===   null          // false
null         ===   undefined     // false
" \t\r\n"    ===   0             // false
```
## With Objects
```javascript
{} === {};                   // false
new String('foo') === 'foo'; // false
new Number(10) === 10;       // false
var foo = {};
foo === foo;                 // true
```
## Conclution
1. use ===
2. explicitly convert(coerce) types with need

