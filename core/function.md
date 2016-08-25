es6 definition syntax:
var obj = {
  foo() {},
  bar() {}
};

### Function constructor vs. function declaration vs. function expression
```JavaScript
A function defined with the Function constructor assigned to the variable multiply:
function multiply(x, y) { //multiply is not changable
   return x * y;
}
A function expression of an anonymous function assigned to the variable multiply:
var multiply = function(x, y) { //mutiply can be reasigned
   return x * y;
};
A function expression of a function named func_name assigned to the variable multiply:
var multiply = function func_name(x, y) { // func_name can only be used in side function
   return x * y;
};
alert(func_name); // throws an error
```


### Determining whether a function exists
```JavaScript
if ('function' == typeof window.noFunc) {
   // use noFunc()
 } else {
   // do something else
 }
```
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions