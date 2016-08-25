
## Closures

```javascript
var Module = (function(){
    var privateProperty = 'foo';

    function privateMethod(args){
        // do something
    }

    return {

        publicProperty: '',

        publicMethod: function(args){
            // do something
        },

        privilegedMethod: function(args){
            return privateMethod(args);
        }
    };
})();
// or 
(function(window){
          
    var foo, bar;

    function private(){
        // do something
    }

    window.xModule = {

        public: function(){
            // do something 
        }
    };

})(this);
```