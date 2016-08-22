http://stackoverflow.com/questions/586182/how-to-insert-an-item-into-an-array-at-a-specific-index

```javascript
Array.prototype.insert1 = function(index) {
    this.splice.apply(this, [index, 0].concat(
        Array.prototype.slice.call(arguments, 1)));
    return this;
};

// With array-type arguments merging and chaining support
Array.prototype.insert2 = function(index) {
    index = Math.min(index, this.length);
    
    arguments.length > 1 // until the first element that is index
        && this.splice.apply(this, [index, 0].concat([].pop.call(arguments))) //Note: every time using the last element of arguments and arguments is changed every time calling pop
        && this.insert2.apply(this, arguments); // recursive
    return this; // chaining support
};


["a", "b", "c", "d"].insert1(2, "V", ["W", "X", "Y"], "Z").join(" | ");
// a | b | V | W,X,Y | Z | c | d

["a", "b", "c", "d"].insert2(2, "V", ["W", "X", "Y"], "Z").join(" | ");
// a | b | V | W | X | Y | Z | c | d
```