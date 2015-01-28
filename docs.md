# F – A *fun*ctional ECMAScript Library


## Types

### L – List, Array, Iterable
### A – Argument List
### F – Function
### O – Object
### * – Type-agnostic


---
## Functions


### ``f.done(F)``
#### Description
Returns the first argument

Calls ``callback`` with the first argument

#### Signature
```js
f.done(
    callback    F(firstArgument *)
) returns *;
```


---
### ``f.tee(F)``
#### Description
Returns the arguments as a ``List``

Passes the arguments to ``callback``'s first argument as a ``List``

#### Signature
```js
f.tee(
    callback    F(args A)
) returns A;
```


---
### ``f.List.map(F, F)``
#### Description
Returns a function that maps ``input`` to ``iterator`` and passes the result to ``callback``

#### Signature
```js
f.List.map(
    iterator    F(element *, index I, array L)
    callback    F(result L)
) returns F(input L);
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
