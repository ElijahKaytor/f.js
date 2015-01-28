## Function Signatures

### Function Signatures follow these [``EBNF``](https://en.wikipedia.org/wiki/Extended_Backus%E2%80%93Naur_Form)s;

#### ``signature``
![](https://cdn.rawgit.com/ElijahKaytor/f.js/b2a7c806/docs/diagrams/signature.svg)
```ebnf
signature ::= (name '=')? type ';'
```
#### ``name``
![](https://cdn.rawgit.com/ElijahKaytor/f.js/b2a7c806/docs/diagrams/name.svg)
```ebnf
name ::= [a-z] (('.')? [a-zA-Z0-9_])*
```
#### ``type``
![](https://cdn.rawgit.com/ElijahKaytor/f.js/b2a7c806/docs/diagrams/type.svg)
```ebnf
type ::= (
    'Fn' ('(' (name ':')? type (',' (name ':')? type)* (',')? ')')? ('->' type)? ('=' (type | ECMAScriptExpression))?
    | 'Generic'
    | 'List' ('(' type ')')?
    | 'Object'
    | 'Int'
    | 'Float'
    | 'String'
    | [A-Z] [A-Za-z0-9]*
)
```

