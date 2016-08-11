
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

> the use of == is widely regarded as bad practice.
> performance impact of '==': a string has to be converted to a number before it can be compared to another number.

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