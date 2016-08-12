## Delete Operator

1. it's impossible to delete global variables, functions and some other stuff in JavaScript which have a DontDelete attribute set.
2. it has nothing to do with directly freeing memory (it only does indirectly via breaking reference).
3. it removes the property from the object entirely. However, if a property with the same name exists on the object's prototype chain, the object will inherit that property from the prototype.