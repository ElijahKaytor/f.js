## Function Signatures

### Function Signatures follow these [``EBNF``](https://en.wikipedia.org/wiki/Extended_Backus%E2%80%93Naur_Form)s;

Generated with Gunther Rademacher's Railroad Diagram Generator (http://bottlecaps.de/rr/ui)

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
![](https://cdn.rawgit.com/ElijahKaytor/f.js/08469d2/docs/diagrams/type.svg)
```ebnf
type ::= ('...')? (
    function
    | 'Generic'
    | 'List' ('(' type ')')?
    | 'Object'
    | 'Int'
    | 'Float'
    | 'String'
    | 'Boolean'
    | custom-type
) ('=' (type | ECMAScriptExpression))?
```
### ``function``
![](https://cdn.rawgit.com/ElijahKaytor/f.js/0d11caa/docs/diagrams/function.svg)
```ebnf
function ::= (
    'Fn' ('('
        ( (name ':')? type (',' (name ':')? type)* (',')? )?
    ')')?
    ('->' type)?
)
```
### ``custom-type``
![](https://cdn.rawgit.com/ElijahKaytor/f.js/5fe7697/docs/diagrams/custom-type.svg)
```ebnf
custom-type ::= (name '.')? [A-Z] [A-Za-z0-9]*
```
