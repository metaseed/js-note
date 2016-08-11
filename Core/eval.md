The use of eval should be avoided. 99.9% of its "uses" can be achieved without it.

> eval only executes in the local scope when it is being called directly and 
> when the name of the called function is actually eval

```javascript
var number = 1;
function test() {
    var number = 2;
    eval('number = 3');
    return number;
}
test(); // 3
number; // 1
```

```javascript
var number = 1;
function test() {
    var number = 2;
    var copyOfEval = eval;
    copyOfEval('number = 3');
    return number;
}
test(); // 2
number; // 3
```
## Security
it executes any code given to it

refer to setTimeout and setInterval