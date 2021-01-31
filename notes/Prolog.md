+JMJ+
## Prolog

- [How to Use](#how-to-use)  
- [Useful swipl Commands](#useful-swipl-commands)  
  - [Queries](#queries)  
- [Prolog Basics](#prolog-basics)  
  - [Facts](#facts)  
  - [Rules](#rules)  
  - [Other Syntax](#other-syntax)  


### How to Use

Install an interpreter. The one I used is [SWI-Prolog](https://www.swi-prolog.org/Download.html).

In a command prompt, run  
```
> swipl
```

### Useful swipl Commands
Note: ALL commands (in interactive console or in `.pl` file) must end in `.` or else it won't execute. It's like `;` in Java.

- `consult(file_name)`: import a `.pl` file (w/o extension)
- `halt`: exit swipl

#### Queries
Ways to get info about your database.

Syntax: `?- predicate(argument_1, [argument_2, ...])`
```
?- male(ben).
true.

?- male(ben), age(ben, 21).
true.

% with this type of query, use ; to continue, or (Enter) or . to quit
?- age(X, 21).
X = ben;
false.
```


### Prolog Basics

#### Facts
Syntax: `relation(entity1, entity2, ....k'th entity).`

Think of `r(X, Y)` as "X is an r of Y"

```
male(Ben)
age(Ben, 21)
parent(Jeff, Ben)
```

#### Rules
Syntax: `predicate(argument_1, [arg_2, ...]) :- pred_2(arg_3, ...), pred_3(arg_4, ...)`

It is a way to define a relation as long as other relations are true. You can think of `r(X, Y) :- r1(X), r2(Y)' as "X is a Y if X is an r1, and Y is an r2".

```
father(X, Y) :- parent(X, Y), male(X).

% recursion works too:
ancestor(X, Y) :- parent(X,Y).
ancestor(X, Y) :- parent(X, Z), ancestor(Z, Y).
```

#### Other Syntax
- **Comments**: `%` for single-line, `/* ... */` for multi-line  
