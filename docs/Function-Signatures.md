## Function Signatures

### Function Signatures follow the following format ([``EBNF``](https://en.wikipedia.org/wiki/Extended_Backus%E2%80%93Naur_Form));

#### ``signature``
![](diagrams/signature.png)
```ebnf
signature ::= (name '=')? type ';'
```
#### ``name``
![](diagrams/name.png)
```ebnf
name ::= [a-z] (('.')? [a-zA-Z0-9_])*
```
#### ``type``
![](diagrams/type.png)
```ebnf
type ::= (
    ('Fn' '(' (name ':')? type (',' (name ':')? type)* (',')? ')')
    | 'Generic'
    | 'List' ('(' type ')')?
    | 'Object'
    | 'Int'
    | 'Float'
)
```

