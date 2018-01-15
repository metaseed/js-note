
- typeof: you get a string representation of the object type. 
- instanceof: you are comparing the type, specifically if the property of a constructor is in the objects prototype chain.

``` js
  //objects
  var Person = function() {}

  var gary = new Person();

  console.log(typeof(gary)); // "object"
  gary instanceof Person // true

  //literals
  var str = 'hello world';
  console.log(typeof(str)); // "string"
  str instanceof String // False

  var str1 = new String('hello world');
  console.log(typeof(str1)) // "object"
  str1 instanceof String // true 
  
So in JavaScript, given that strings can be literals or objects, the correct way to test for a string would be to test against both cases.

  
  function isString(str) {
    return typeof(str) == 'string' || str instanceof String;
  }
```
