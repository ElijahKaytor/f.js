## Function Signatures

### Function Signatures follow these [``EBNF``](https://en.wikipedia.org/wiki/Extended_Backus%E2%80%93Naur_Form)s;

#### ``signature``
![](diagrams/signature.svg)
```ebnf
signature ::= (name '=')? type ';'
```
#### ``name``
![](diagrams/name.svg)
```ebnf
name ::= [a-z] (('.')? [a-zA-Z0-9_])*
```
#### ``type``
![](diagrams/type.svg)
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

