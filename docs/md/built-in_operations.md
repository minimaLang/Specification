# Built-in Operations

> [^1] The syntax is reverse polish notation (RPN). \
> [^2] Any white-space is ignored by the parser.

- [Basics](#basics)
  - [Unary](#unary)
  - [Stack](#stack)
  - [Logic](#logic)
  - [Math](#math)
- [Flow Control](#flow-control)
  - [Loop](#loop)
  - [Branch](#branch)

## Basics

### Overview

[Unary](#unary)
| Category | Type  | Token    |
| :------: | :---: | :------: |
| Any      | Unary | `{`, `}` |

[Stack](#stack)
| Type   | Token             |
| :----: | :---------------: |
| Binary |`^`, `.`, `~`, `:` |

[Logic](#logic)
| Type   | Token       |
| :----: | :---------: |
| Binary | `and`, `or` |
| Unary  | `not`       |

[Math](#math)
| Type   | Token              |
| :----: | :----------------: |
| Binary | `+`, `-`, `*`, `/` |

### Unary

| Token    | Syntax                      |
| -------- | :-------------------------: |
| `{`, `}` | `{` **operator symbol** `}` |

#### Example (1)

```minimaL
2 { - } 2 +
```

- Stack
  - `2`
    - `{`
      - `-`
    - `}`
  - [`-2`]
  - `2`
  - `+`
  - [`0`]

The stack contains the answer `0`. \
Is equivalent to ``(-2) + 2``.

### Stack

| Token              | Syntax                                   |
| :----------------: | :--------------------------------------: |
| `^`, `.`, `~`, `:` | _Operand1_ _Operand2_ **Stack Operator** |

In addition to the [mathematical operations](#math), \
_minimaL_ also has **stack operations**.

The operations are ...

- Pick-up value  (`^` 'Pick')
- Put-down value (`.` 'Put')
- Discard value  (`~` 'Drop')
- Pass value     (`:` 'Pass')

#### Pick (^) and Put (.)

_Pick_ takes a value, \
and _Put_ place it on the stack.

_Pick_ and _Put_ are mostly used implicitly. \

One example is the mathematical operation

```minimaL
2 3 +
```

The operation _Addition_ `+` causes the values 2 and 3 ...

- to be picked `^` from the stack
- applied to the function _Addition_ `+`
- and its result is placed on `.` the stack.

#### Drop (~)

_Drop_ discards a value. \
It deletes it from the stack.

##### Example (2)

```minimaL
2 ~ 3 3 +
```

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

```minimaL
6 A :
```

The _hand_ called `A` contains the answer `6`.

There are two type of _hands_ ...

- a value _bearer_
- and a value _accumulator_ (also called a _collector_)

_On-hand_ will be discussed later.

### Logic

| Token              | Syntax                                   |
| :----------------: | :--------------------------------------: |
| `and`, `or`, `not` | _Operand1_ _Operand2_ **Stack Operator** |

(_Work in progress_)

### Math

| Token              | Syntax                                   |
| :----------------: | :--------------------------------------: |
| `+`, `-`, `*`, `/` | _Operand1_ _Operand2_ **Stack Operator** |

- Also See [Unary](#unary).

#### Example (3)

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

## Flow Control

_Comming soon_.

### Loop

_Comming soon_.

### Branch

[^0]: See /
[^1]: See [Introduction](main.md)
[^2]: See [Introduction](main.md)
