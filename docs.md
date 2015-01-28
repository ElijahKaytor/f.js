# f – A *fun*ctional ECMAScript Library

## Functions


### ``f.done(=Fn)``
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
### ``f.tee(=Fn)``
#### Description
Returns the arguments as a ``List``

Passes the arguments to ``callback`` as a ``List``

#### Signature
```js
f.tee Fn(
    callback    F(args List) -> Generic = f.done
) -> ArgumentList
```


---
### ``f.List.map(Fn, =Fn)``
#### Description
Maps ``input`` to ``iterator`` then passes the the result to ``callback``

#### Signature
```js
f.List.map Fn(
    iterator    Fn(element Generic, index Int, array List) -> Generic
    callback    Fn(output List) -> Generic = f.done
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
### ``f.Object.filterProperties(String..., =Fn)``
#### Description
Deletes ``properties``s from ``input`` then passes the result to ``callback``

#### Signature
```js
f.Object.filterProperties Fn(
    properties  String...
    callback    Fn(output Object) -> Generic = f.done
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
