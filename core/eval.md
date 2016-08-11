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

## setTimeout and setInterval

```javascript
function foo() {
    // will get called
}

function bar() {
    function foo() {
        // never gets called
    }
    setTimeout('foo()', 1000);
}
bar();

// setTimeout and setInterval can also take a string as their first parameter. 
// it internally makes use of eval

```

```javascript
function foo(a, b, c) {}
// NEVER use this, it is a clear sign of really bad code
setTimeout('foo(1, 2, 3)', 1000)

// Instead use an anonymous function
setTimeout(function() {
    foo(1, 2, 3);
}, 1000)
```