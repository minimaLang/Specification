# Operations

See [Convention](convention)

- [Stack](#stack)
- [Logic](#logic)
- [Comparsion](#comparsion)
- [Math](#math)

## Stack

| Token              |
| :----------------- |
| `^`, `.`, `~`, `:` |

- Pick-up a value  ([`^` 'Pick'](#pick-and-put))
- Put-down a value ([`.` 'Put'](#pick-and-put))
- Discard a value  ([`~` 'Drop'](#drop))
- Pass a value     ([`:` 'Pass'](#pass))

### Pick and Put

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

### Drop

_Drop_ discards a value. \
It deletes it from the stack.

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

### Pass

_Pass_ causes a value to be stored '_on-hand_', \
which is like (but not equal to) a named _variable_.

```minimaL
6 A :
```

The _hand_ called `A` contains the answer `6`.

There are two type of _hands_ ...

- a value _bearer_ <!-- (also called a __) -->
- and a value _accumulator_ (also called a _collector_)

_On-hand_ will be discussed later.

## Logic

| Token      | Syntax                                    |
| :--------: | :---------------------------------------: |
| `'+`, `'/` | _Operand1_ _Operand2_ **Binary-Operator** |
| `'-`       | _Operand_ **Unary-Operator**              |

- `'+` And
- `'/` Or
- `'-` Not

## Comparsion

| Token | Syntax                                    |
| :---: | :---------------------------------------: |
| `=`   | _Operand1_ _Operand2_ **Binary-Operator** |

```minimaL
2 A :
2 B :
A B = C :
```

`C` _Answers_ `1`.

```minimaL
2 A :
1 B :
A B - C :
C 0 = D :
D B - E :
```

- Answers; Step-by-Step
  1. _Pass Values to_ `A` and `B`
     - `A` _Contains_ `2`
     - `B` _Contains_ `1`
  2. _Substract `B` from `A`_; _Answer_ is `1`
     - _Pass_ _Answer_ to `C`;
  3. _Compare `C` with `0`; _Answer_ is_ `-1`
     - _Pass_ _Answer_ to `D`;
  4. _Substract_ `B` from `D`;
     - _Pass_ _Answer_ to `E`
  5. _Answer_ is `0`

## Math

| Token              | Syntax                                    |
| :----------------: | :---------------------------------------: |
| `+`, `-`, `*`, `/` | _Operand1_ _Operand2_ **Binary-Operator** |
| `{` .. `}`         | _Operand_ { _Unary-Operator_ }            |

```minimaL
2 3 + 2 *
```

Is equivalent to `(2 + 3) * 2`. \
_Answer_ is `10`.
