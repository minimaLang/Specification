# Data Structure

- [Mark](#mark)
- [Pair](#pair)
- [Sequence](#sequence)
  - [of Value](#of-value)
  - [of Expression](#of-expression)

## Mark

| Symbol     | Syntax         | Name
| ---------- | -------------- | ----
| `"` .. `"` | _Sym> <> <Sym_ | Mark

## Pair

| Symbol    | Count | Syntax                        | Name
| --------- | :---: | ----------------------------- | ----
| `(` ..`)` |   2   | _Sym> <1:Key> <2:Value> <Sym_ | Pair

A pair consists of _key_ and _value_. \
The _key_ must be of type _[Constant](built-in_type#constant)_.

```minimaL
( 'A 31 ; 'B 21 ) : C
C 'A N :
C 'B M :
```

- `N` answers `32`
- `M` answers `21`

## Sequence

| Token
| ----------
| `[` .. `]`

- [Value](#of-value)
- [Expression](#of-expression)

### of Value

| Type  | Token
| ----- | --------
| Begin | `(`
| Infix | _Values_
| End   | `)`

- _Valid_
  1. `[ 1 2 3 ]`
  2. `( [ 1 2 3 ] [ A B C ] )`
  3. `( [ 1 A 5 ] )`
- _Invalid_
  1. `( 1 2 3 )`
  2. `( )`
  3. `[ ]`

```minimaL
1 A :
2 B :
3 C :
[ A B C ] + O :
```

`O` _answers_ `6`

```minimaL
D 1 :
E 2 :
F 3 :
G 2 :
[ D E ] < + / >
```

### of Expression

| Token        | Name
| ------------ | ---------------------
| `{`          | Expression-List-Begin
| _Expression_ | Expression
| `}`          | Expression-List-End

```minimaL
{
  1 A :
  2 B :
}
```
