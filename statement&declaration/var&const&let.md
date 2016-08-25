
## var

* function-scoped
* hoist to the top of its function
* redeclarations of the same name in the same scope are no-ops

## const

* function-scoped
* hoist to the top of its function
* redeclarations of the same name in the same scope are rejected

## let

* block-scoped
* hoist to the top of its block (not in ECMAScript 6!)
* redeclarations illegal
* behaves exactly the same as vars at function top-level (i.e. can be redeclared at function top-level even though cannot be elsewhere)

```javascript
var a = 1;
var b = 2;
if (a === 1) {
  var a = 11; // the scope is global
  let b = 22; // the scope is inside the if-block
  console.log(a);  // 11
  console.log(b);  // 22
} 
console.log(a); // 11
console.log(b); // 2

function letTest() {
  let x = 1;
  if (true) {
    let x = 2;  // different variable
    console.log(x);  // 2
  }
  console.log(x);  // 1
}
```

```javascript
var x = 'global';
let y = 'global';
console.log(this.x); // "global"
console.log(this.y); // undefined --let, unlike var, does not create a property on the global object.
```
```javascript
if (x) {
  let foo;
  let foo; // SyntaxError thrown.
}

switch (x) {
  case 0:
    let foo;
    break;
    
  case 1:
    let foo; // SyntaxError for redeclaration.
    break;
}

switch (x) {
  case 0:{
    let foo;
    break;
  }
  case 1:
    let foo; // OK
    break;
}
```

```javascript
function go(n){
  for (let n of n.a) { //ReferenceError: n (2nd n, in n.a) is not defined
    console.log(n);
  }
}

go({a:[1,2,3]});
```

### reference
https://developer.mozilla.org/en-US/docs/Archive/Web/Scope_Cheatsheet