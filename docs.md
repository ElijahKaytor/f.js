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
```
var addOneToEach = f.List.map(function(n) { return n + 1 });
addOneToEach([1, 2, 3]); // [2, 3, 4]

var doubleEach = f.List.map(function(n) { return n * 2 });
doubleEach([1, 2, 3]); // [1, 4, 6]
```
