es6 definition syntax:
```js
var obj = {
  foo() {},
  bar() {}
};
```

### Function constructor vs. function declaration vs. function expression
A function defined with the Function constructor assigned to the variable multiply:
```JavaScript
function multiply(x, y) { //multiply is not changable
   return x * y;
}
```
A function expression of an anonymous function assigned to the variable multiply:
```js
return x * y;
var multiply = function(x, y) { //mutiply can be reasigned
};
```
A function expression of a function named func_name assigned to the variable multiply:
```js
var multiply = function func_name(x, y) { // func_name can only be used in side function
   return x * y;
};
alert(func_name); // throws an error
```


### Determining whether a function exists
```JavaScript
if ('function' == typeof window.noFunc) {
   // use noFunc()
 } else { //'function'!='undefined'
   // do something else
 }
```
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions