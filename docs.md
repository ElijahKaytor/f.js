# F – A *fun*ctional ECMAScript Library

## Functions


### ``f.done(F=)``
#### Description
Returns the first argument

Calls ``callback`` with the first argument

#### Signature
```js
f.done Fn(
    callback    Fn(firstArgument Generic) -> Generic
) -> Generic
```


---
### ``f.tee(F=)``
#### Description
Returns the arguments as a ``List``

Passes the arguments to ``callback``'s first argument as a ``List``

#### Signature
```js
f.tee Fn(
    callback    F(args List) -> Generic = f.done()
) -> ArgumentList
```


---
### ``f.List.map(F, F=)``
#### Description
Returns a function that maps ``input`` to ``iterator`` and passes the result to ``callback``

#### Signature
```js
f.List.map Fn(
    iterator    Fn(element Generic, index Int, array List) -> Generic
    callback    Fn(result List) -> Generic = f.done()
) -> Fn(input List)
```

#### Example
```js
var addOne = function(n) { return n + 1 };
var double = function(n) { return n * 2 };

var addOneEach = f.List.map(addOne);
addOneEach([1, 2, 3]); // [2, 3, 4]

var doubleEach = f.List.map(double);
doubleEach([1, 2, 3]); // [1, 4, 6]

var addOneThenDoubleEach = f.List.map(addOne, f.List.map(double));
addOneThenDoubleEach([1, 2, 3]); // [4, 6, 8]
```
