## Delete Operator

1. delete is only effective on an object's properties.  It has no effect on variable or function names.
2. it has nothing to do with directly freeing memory (it only does indirectly via breaking reference).
3. when delete a property, it removes the property from the object. However, if a property with the same name exists on the object's prototype chain, the object will inherit that property from the prototype.

```JavaScript
x = 42;         // creates the property x on the global object
var y = 43;     // creates the property y on the global object, and marks it as non-configurable
myobj = {
  h: 4,
  k: 5
};

// x is a property of the global object and can be deleted
delete x;       // returns true

// y is not configurable, so it cannot be deleted                
delete y;       // returns false 

// delete doesn't affect certain predefined properties
delete Math.PI; // returns false 

// user-defined properties can be deleted
delete myobj.h; // returns true 

// myobj is a property of the global object, not a variable,
// so it can be deleted
delete myobj;   // returns true

function f() {
  var z = 44;

  // delete doesn't affect local variable names
  delete z;     // returns false
}
```

```JavaScript
function Foo(){}
Foo.prototype.bar = 42;
var foo = new Foo();

// returns true, but with no effect, 
// since bar is an inherited property
delete foo.bar;           

// logs 42, property still inherited
console.log(foo.bar);

// deletes property on prototype
delete Foo.prototype.bar; 

// logs "undefined", property no longer inherited
console.log(foo.bar);
```
```JavaScript
var trees = ["redwood","bay","cedar","oak","maple"];
delete trees[3];
if (3 in trees) {
    // this does not get executed
}
```