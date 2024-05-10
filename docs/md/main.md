# Specification for minimaLang

_minimaLang_, or _minimaL_ for short, is a stack-based programming language with minimal syntax. \
The syntax is reverse polish notation (RPN).

## Built-in Operations

### Math Operations

The values in square brackets represent the _**intermediate** answers_ (results).

Example

```minimaL
  2 3 + 2 *
```

- Stack
  - `2`
  - `3`
  - `+`
  - [`5`]
  - `2`
  - `*`
  - [`10`]

The stack contains the answer `10`. \
Is equivalent to ``(2 + 3) * 2``.

---
As usual in maths, the calculation sequence can be changed using round brackets.

Example

```minimaL
  2 (3 2 *) +
```

- Stack
  - `2`
  - `(`
    - `3`
    - `2`
    - `*`
    - [`6`]
  - `)`
  - `+`
  - [`6`]
  - [`2`]
  - [`8`]

The stack contains the answer `8`. \
Is equivalent to ``2 + (3 * 2)``.

### Stack Operations

In addition to the mathematical operations, \
_minimaL_ also has 'stack operations'.

The operations are ...

- Pick-up value  (`^` 'Pick')
- Put-down value (`.` 'Put')
- Discard value  (`~` 'Drop')
- Pass value     (`:` 'Pass')

#### Pick (^) and Put (.)

_Pick_ takes a value, \
and _Put_ place it on the stack.

_Pick_ and _Put_ are mostly used implicitly. \
One example is the mathematical operation: \
`2 3 +`. \
The operation _Addition_ `+` causes the values 2 and 3 ...

- to be picked `^` from the stack
- applied to the function _Addition_ `+`
- and its result is placed on `.` the stack.

#### Drop (~)

_Drop_ discards a value. \
It deletes it from the stack.

##### Examples (2)

`2 ~ 3 3 +`

- Stack
  - `2`
  - `~`
  - [`0`]
  - `3`
  - `3`
  - `+`
  - [`6`]

The answer `6` is on the stack.

#### Pass (:)

_Pass_ causes a value to be stored '_on-hand_', which is like (but not equal to) a named _variable_.

Syntax ``6 A :``. \
The _hand_ called `A` contains the answer `6`.

There are two type of _hands_

- a value _bearer_
- and a value _accumulator_ (also called a _collector_)

_On-hand_ will be discussed later.
