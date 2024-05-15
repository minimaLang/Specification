# Data Structure

- [Pair](#pair)
- [Sequence](#sequence)
  - [of Value](#of-value)
  - [of Expression](#of-expression)

## Pair

| Token       |
| :---------: |
| `(` `;` `)` |

A pair consists of _key_ and _value_. \
The _key_ must be of type _[Constant](built-in_type#constant)_.

| Syntax  |
| :-----: |
| `(`     |
| _Key_   |
| _Value_ |
| `;`     |
| ...     |
| `)`     |

```minimaL
( 'A 31 ; 'B 21 ) : C
C 'A N :
C 'B M :
```

- `N` answers `32`
- `M` answers `21`

## Sequence

| Token      |
| :--------: |
| `[` .. `]` |
| `{` .. `}` |

- [Value](#of-value)
- [Expression](#of-expression)

### of Value

| Type  | Token    |
| :---: | :------: |
| Begin | `(`      |
| Infix | _Values_ |
| End   | `)`      |

- _Valid_
  1. `[ 1 2 3 ]`
  2. `( [ 1 2 3 ] [ A B C ] )`
  3. `( [ 1 A 5 ] )`
- _Invalid_
  1. `( 1 2 3 )`
  2. `( )`
  3. `[ ]`

```minimaL
A 1 :
B 2 :
C 3 :
> [ A B C ] + > O :
```

`O` answers `6`

```minimaL
D 1 :
E 2 :
F 3 :
G 2 :
[ D E ] < + / >
```

### of Expression

| Type  | Token        |
| :---: | :----------: |
| Begin | `{`          |
| Infix | _Expression_ |
| End   | `}`          |

```minimaL
{
  A 1 :
  B 2 :
}
```

```minimaL
.. L { A 1 : }
```

See [Label](flow-control#label)
