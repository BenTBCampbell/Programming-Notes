<p style="text-align: center">+JMJ+</p>

## Prolog

- [Basic Defintions](#basic-defintions)
- [Interpreter: SWI Prolog](#interpreter-swi-prolog)
- [Useful swipl Commands](#useful-swipl-commands)
  - [Queries](#queries)
- [Prolog Basics](#prolog-basics)
  - [Facts](#facts)
  - [Rules](#rules)
  - [Lists](#lists)
    - [Iterating Lists](#iterating-lists)
  - [Other Syntax](#other-syntax)


### Basic Definitoins

In Prolog, there are two basic things you deal with: your database, in a `.pl` file, and the interpreter, which is a program that runs in a console that is used to search and answer questions about the database.

There are various basic terms and building blocks that make up prolog:

- **[Facts](#facts)**: A relationship between terms. This is what the database is made up of.
- **Terms**: A 'thing' in the database that you can describe relationships between. They are either atoms or numbers.
  - *atoms*: 	A text term. It must start with a lowercase letter.
  - *numbers*: A numer term. It can either be ints or floats.
- **Predicates**: A boolean function that describes a retlationship between terms.
  - *[rules](#rules)*: A predicate with an if statement.
- Other stuff
  - *variables*: Can be used in place of terms in predicate statements to define the predicate between several terms. Must start with an uppercase letter.
  - *[query](#queries)*: A T/F question posed to the interpreter to try to answer using the database.
  - *lists*: A list. Each list is either a head and a tail, or empty. The head is a term, the tail is another list (sometimes an empty one).

Here's a table to describe their syntax and an object-oriented equalivent:

| Name           | Syntax                                  | Object-Oriented Equalivent                                    |
| :------------- | :-------------------------------------- | :------------------------------------------------------------ |
| **facts**      | n/a                                     | statement/line of code                                        |
|                |                                         |                                                               |
| **terms**      | n/a                                     | static variable                                               |
| atoms          | `an_atom`                               | string                                                        |
| numbers        | `123.45`                                | number                                                        |
|                |                                         |                                                               |
| **predicates** | `predicate(term_1, term_2, ...)`        | boolean functions                                             |
| rules          | `p(t1, t2, ...) :- p2(t3, t4), p3(...)` | `if (p2(t3, t4) AND p3(...) AND ...) return true;`            |
|                |                                         |                                                               |
| variables      | `My_Variable`                           | index variable in for loops                                   |
| query          | n/a                                     | boolean function in interactive console                       |
| lists          | `[H\|T]` or `[t1,t2,...]`* or `[]`      | linked lists (kinda)                                         |

\* when lists are in the form `[t1,t2,t3]`, it's really interpreted as `[t1 | [t2 | [t3 | [] ] ]` (each term is just the head of the next embedded list).

### Interpreter: SWI Prolog

The interpreter that I use, and lots of people seem to recomment is [SWI-Prolog](https://www.swi-prolog.org/Download.html).

in order to use, run `swipl` in a command prompt:<br>
```bash
> swipl
```

#### Useful swipl Commands
Note: ALL commands (in interactive console or in `.pl` file) must end in `.` or else it won't execute. It's like `;` in Java.

- `consult(file_name)`: import a `.pl` file (w/o extension)
- `halt`: exit swipl

##### Queries
Ways to get info about your database.

Syntax: `?- predicate(argument_1, [argument_2, ...])`
```prolog
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

```prolog
male(Ben)
age(Ben, 21)
parent(Jeff, Ben)
```

#### Rules
Syntax: `predicate(argument_1, [arg_2, ...]) :- pred_2(arg_3, ...), pred_3(arg_4, ...)`

It is a way to define a relation as long as other relations are true. You can think of `r(X, Y) :- r1(X), r2(Y)' as "X is a Y if X is an r1, and Y is an r2".

```prolog
father(X, Y) :- parent(X, Y), male(X).

% recursion works too:
ancestor(X, Y) :- parent(X,Y).
ancestor(X, Y) :- parent(X, Z), ancestor(Z, Y).
```

#### Lists
Syntax: 
- `[]` (empty list)
- `[Head | Tail]`
- `[t]` (which is really `[t | []]`)
- `[t1,t2...]` (which is really `[t1 | [t2 | [t3]]`)

Lists are either empty lists, or they are made up of two parts: a head and a tail. The head is a term, and the tail is another list (sometimes an empty one).

##### Iterating lists
Lists can be queried and manipulated using predicates and rules. The basic way to iterate through a list is to have a recusive rule that has some base case with an empty list, and a recursive step of passing the tail of the list into itself. It's expressed like this:
```prolog
iterate([]). % base case: when you try to iterate through an empty list, you're done. Return true.
iterate([Head | Tail]) :- iterate(Tail). % recursive step: plug the tail back into the predicate.
```
(iterate() is actually a rule that checks if what you plug into it is a list, as opposed to just an atom or a number.)

expressed in C++, it would look like this:
```cpp
bool iterate(list) {

  // iterate([]).
  if (list == []) {
    return true
  }

  // iterate([Head | Tail]) :- iterate(Tail).
  return iterate(list.Tail)
}
```

You could have other terms for variables if you like as well. Here's a rule that checks if a term is in the list:

```prolog
member(Head, [Head|Tail]). % the head of a list is in the list.
member(Term, [Head|Tail]) :- member(Term, Tail). % Term is a member if it's a member of the tail.
```

#### Other Syntax
- **Comments**: `%` for single-line, `/* ... */` for multi-line
