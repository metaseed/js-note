## undefined

1. undefined is a **type** with exactly one value: *undefined*. 
2. undefined is a global **variable**(a property of the global object) that has the value of *undefined*.
   in ES5, it is a non-configurable, non-writable property.(before ES5 is overidable).
   ```javascript
   typeof undefined // 'undefined'
   ```
3. Cases that return *undefined*:
    * Accessing the (unmodified) global variable undefined.
    * Accessing a declared but not yet initialized variable.
    ```javascript
    var x; 
    typeof x // undefined
    ```
    * typeof undecleared variable. 
    ```javascript
    // x has not been declared before
    typeof x // 'undefined'
    ```
    * Function call that implicit returns due to missing return statements.
    * Function call with the return statements that do not explicitly return anything.
    * Function parameters that do not have any explicit value passed.
    * Lookups of non-existent properties.
    * Anything that has been set to the value of undefined.
    * Any expression in the form of void(expression)

### Attention

```javascript
//DON'T DO THIS
// it is possible to use it as an identifier (variable name) in any scope
// other than the global scope (because undefined is not a reserved word)
(function(){ var undefined = 'foo'; console.log(undefined, typeof undefined); })(); // logs "foo string"
(function(undefined){ console.log(undefined, typeof undefined); })('foo');// logs "foo string"
```

```javascript
// x has not been declared before
if (typeof x === 'undefined') {
    console.log('these statements execute');
}
if(x === undefined){ // throws a ReferenceError

}
```

```javascript
// void operator and undefined
var x;
if (x === void 0) {
   // these statements execute
}

// y has not been declared before
if (y === void 0) {
   // throws a ReferenceError (in contrast to `typeof`)
}
```

## null
* it's not an identifer for a property of the global object like undefined can be.

```javascript
// foo does not exist. It is not defined and has never been initialized:
foo // "ReferenceError: foo is not defined"

// foo is known to exist now but it has no *type* or *value*:
var foo = null; foo // "null"
```
## Diffenence
```javascript
typeof null        // object (bug in ECMAScript, should be null)
typeof undefined   // undefined
null === undefined // false
null  == undefined // true
```