function's this keyword 

### Global context

```JavaScript
console.log(this.document === document); // true
// In web browsers, the window object is also the global object:
console.log(this === window); // true
this.a = 37;
console.log(window.a); // 37
```

### Function context

```JavaScript
function f1(){
  return this;
}
f1() === window; // global object

function f2(){
  "use strict"; // strict mode: 'this' remains at whatever it's set to when entering the execution context
  return this;
}
f2() === undefined; // true
window.f2() === window // true

let obj = {
  fun:function (){
  'use stric';
   return this;
   }
}
obj.fun() === obj;
```

### Arrow functions

```JavaScript
var globalObject = this;
var foo = (() => this);
var obj = {foo: foo};

console.log(foo() === globalObject); // true

// Call as a method of an object
console.log(obj.foo() === globalObject); // true

// Attempt to set this using call
console.log(foo.call(obj) === globalObject); // true

// Attempt to set this using bind
foo = foo.bind(obj);
console.log(foo() === globalObject); // true
```

```JavaScript
var obj = { bar : function() {
                    var x = (() => this); // its this is permanently bound to the this of its enclosing function.
                    return x;
                  }
          };
var fn = obj.bar();

// Call fn without setting this, would normally default
// to the global object or undefined in strict mode
console.log(fn() === obj); // true
```

### In an object method
```JavaScript
var o = {
  prop: 37,
  f: function() {
    return this.prop;
  }
};
console.log(o.f()); // logs 37

var o = {prop: 37};
function independent() {
  return this.prop;
}
o.f = independent;
console.log(o.f()); // logs 37
o.b = {g: independent, prop: 42};
console.log(o.b.g()); // logs 42
```
#### this on the object's prototype chain
```JavaScript
var o = {a: 3, b: 6, f:function(){ return this.a + this.b; }};
var p = Object.create(o);
p.a = 1;
p.b = 4;
console.log(p.f()); // 5
```

```JavaScript
function sum(){
  return this.a + this.b + this.c;
}
var o = {
  a: 1,
  b: 2,
  c: 3,
  get average(){
    return (this.a + this.b + this.c) / 3;
  }
};

Object.defineProperty(o, 'sum', {get: sum, enumerable:true, configurable:true});

console.log(o.average, o.sum); // logs 2, 6
```

### As a constructor

```JavaScript
function C(){
  this.a = 37;
}

var o = new C();
console.log(o.a); // logs 37


function C2(){
  this.a = 37;
  return {a:38};
}

o = new C2();
console.log(o.a); // logs 38

function foo(){
    alert(this);
}
foo() // window
new foo() // foo

//-----------
function f(){
  this.b = 1;
}

function C3(){
  this.b =2;
  f(); // this object is window
}

function C4(){
  this.b =2;
  f.call(this); //call function that has this in constructor
}

console.log(new C3().b); // 2;
console.log(new C4().b); // 1;
//----------

```

### call, apply and bind
```JavaScript
function add(c, d){
  return this.a + this.b + c + d;
}

var o = {a:1, b:3};

// The first parameter is the object to use as
// 'this', subsequent parameters are passed as 
// arguments in the function call
add.call(o, 5, 7); // 1 + 3 + 5 + 7 = 16

// The first parameter is the object to use as
// 'this', the second is an array whose
// members are used as the arguments in the function call
add.apply(o, [10, 20]); // 1 + 3 + 10 + 20 = 34

function bar() {
  console.log(Object.prototype.toString.call(this));
}

bar.call(7); // [object Number] //7 is not an object, convert it to an object using the internal ToObject operation

function f(){
  return this.a;
}
var g = f.bind({a:"azerty"});
console.log(g()); // azerty

var o = {a:37, f:f, g:g};
console.log(o.f(), o.g()); // 37, azerty
```

### As a DOM event handler
this is set to the element the event fired from.
```JavaScript
// When called as a listener, turns the related element blue
function bluify(e){
  // Always true
  console.log(this === e.currentTarget); 
  // true when currentTarget and target are the same object
  console.log(this === e.target);
  this.style.backgroundColor = '#A5D9F3';
}

// Get a list of every element in the document
var elements = document.getElementsByTagName('*');

// Add bluify as a click listener so when the
// element is clicked on, it turns blue
for(var i=0 ; i<elements.length ; i++){
  elements[i].addEventListener('click', bluify, false);
}
```
### In an in–line event handler
```html
<button onclick="alert(this.tagName.toLowerCase());">
  Show this
</button>

<button onclick="alert((function(){return this})());"> //the inner function's this isn't set so it returns the global/window object 
  Show inner this
</button>
```
//https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this