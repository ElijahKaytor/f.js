# F – A *fun*ctional ECMAScript Library

## Signatures
Signatures follow the following format

## Functions


### ``f.done(=Fn)``
#### Description
Calls ``callback`` with the first argument.

Returns the first argument.

Ignores the result from ``callback``.

#### Signature
```js
f.done Fn(
    callback    Fn(firstArgument Generic) -> Generic = function(){}
) -> Fn(firstArgument Generic) -> Generic
```


---
### ``f.tee(=Fn)``
#### Description
Passes the arguments to ``callback`` as a ``List``.

Returns the arguments as a ``List``.

Ignores the result from ``callback``.

#### Signature
```js
f.tee Fn(
    callback    Fn(args List) -> Generic = f.done()
) -> Fn(args Generic...) -> List
```


---
### ``f.List.map(Fn, =Fn)``
#### Description
Maps ``input`` to ``iterator`` then passes the the result to ``callback``.

Returns the result from ``callback``.

#### Signature
```js
f.List.map Fn(
    iterator    Fn(element Generic, index Int, array List) -> Generic
    callback    Fn(output List) -> Generic = f.done()
) -> Fn(input List) -> Generic
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

---
### ``f.List.reduce(Fn, =Generic, =Fn)``
#### Description
Reduces ``input`` throughj ``iterator`` then passes the the result to ``callback``.

Returns the result from ``callback``.

#### Signature
```js
f.List.reduce Fn(
    iterator    Fn(previousValue Generic, currentValue Generic, index Int, array List) -> Generic
    firstValue  Generic = null
    callback    Fn(output List) -> Generic = f.done()
) -> Fn(input List) -> Generic
```


---
### ``f.Object.filterProperties(String..., =Fn)``
#### Description
Deletes ``properties`` from ``input`` then passes the result to ``callback``.

Returns the result from ``callback``.

#### Signature
```js
f.Object.filterProperties Fn(
    properties  String...
    callback    Fn(output Object) -> Generic = f.done()
) -> Fn(input Object) -> Generic
```

#### Example
```js
var removeSensitiveFields = f.Object.filterProperties('password', 'isAdmin');
Object.keys(removeSensitiveFields({
    id: 1,
    username: 'Elijah',
    password: '$2y$10$bpI4uLZfRG39MLVuWexVvuzWK2kXI1FEmFrgVVZn1FMwxeYMQoEE2',
    isAdmin: true,
    createdAt: 1422409318922,
    updatedAt: 1422409318922,
})); // ['id', 'username', 'createdAt', 'updatedAt']

// Express.js + Knex.js example (http://expressjs.com/, http://knexjs.org/)
app.route('/api/users').get(function(request, response) {
    knex('Users').select().then(
        f.List.map(
            f.Object.filterProperties('password', 'isAdmin'),
            response.json
        )
    );
});
```
