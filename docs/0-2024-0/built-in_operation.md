# Operations

See [Convention](convention.md)

- [Stack](#stack)
- [Logic](#logic)
- [Comparsion](#comparsion)
- [Arithmetic](#arithmetic)
- [Branch](#branch-anchor-condition-jump)

## Stack

| Symbol  | Syntax    | Name
| ------- | --------- | ------------------------------
| `^`     | _<>_      | [Pick](#pick-and-put)
| `.`     | _<>_      | [Put](#pick-and-put)
| `:`     | _<1> <2>_ | [Pass](#pass)
| `~`     | _<>_      | [Drop](#drop)
| `&`     | _<>_      | [Peek](#peek)
| `_` `,` | _-_       | [Separate](#separate)
| `\`     | _-_       | [No-Operation](#no-operation)

### Pick and Put

_Pick_ takes a value, \
and _Put_ place it on the stack. \
_Pick_ and _Put_ are mostly used implicitly.

One example is the mathematical operation ``2 3 +``.

#### Explanation (_Pick and Put_)

- The operation _Addition_ `+` causes the values 2 and 3 ...
  - to be picked `^` from the stack
  - passed (applied) to the function _Addition_ `+`
  - finally its result is placed `.` on the stack.

#### Explanation (_Pass_)

```minimaL
6 A :
```

The _hand_ called `A` contains the answer `6`.

See _[On-hand](built-in_on-hand.md)_.

### Drop

_Drop_ discards a value. \
It deletes it from the stack.

#### Explanation (_Drop_)

```minimaL
2 ~ 3 3 +
```

_Answer_ is `6`.

- Stack
  - `2`
  - `~`
  - [`0`]
  - `3`
  - `3`
  - `+`
  - [`6`]

### Peek

| Symbol | Count | Syntax       | Name
| ------ | :---: | ------------ | ---------------------
| `&`    |   1   | _<>var <Sym_ | Peek-Stack-Position-n

_Peek_ copies the n-th _element_ from the _stack_ \
and _passes_ it to the given _variable_ and _removes_ the copy.

#### Explanation (Peek)

```minimaL
20 10 +
76 10 -
10  5 *

2 A &
```

`A` _answeres_ 66.

- Stack
  1. 30   (`20 10 +`)
  2. 66   (`76 10 -`)
  3. 50   (`10  5 *`)
  4. [66] (`2 &`)
  5. 66   (`A :`)

The results of the calculation operations are on the _stack_. \
Therefore, the second _element_ on the _stack_ is the result of the subtraction.

### Pass

| Symbol | Count | Syntax
| ------ | :---: | -----------
| `:`    |   1   | _<> <Sym_

_Pass_ causes a value to be stored '_on-hand_', \
which is like a named _variable_.

```minimaL
6 A :
```

#### Explanation (Pass)

```minimaL
```

### No Operation

| Symbol | Syntax | Name
| ------ | ------ | ---------------------
| `\`    | _-_    | No-Operation
| `_`    | `.`    | [Separate](#separate)

#### Separate

| Symbol | Syntax | Name
| ------ | ------ | -------------------
| `_`    | _-_    | Separator-Universal
| `,`    | _-_    | Separator-Value

1. You can use `_` to separate digits for readability.
2. and `,` to separate values.

The symbols are basically ignored. \
So, the parser interprets `A,B` as `AB` and `1_2` or `1,2` as `12`.

#### Explanation (No Operation)

``1_000``
Is equal to ``1000``.

``A_B_C``
Is equal to ``ABC``.

``1\000`` is invalid.

## Logic

| Symbol     | Count | Syntax         | Name
| ---------- | :---: | -------------- | -------
| `'+`, `'/` |   2   | _<1> <2> <Sym_ | And, Or
| `'-`       |   2   | _<1> <2> <Sym_ | Not

See also [Bit-Operation](#bit-operation)

## Comparsion

| Symbol | Count | Synta          | Name
| ------ | :---: | -------------- | -------
| `=`    |   2   | _<1> <2> <Sym_ | Equal
| `<>`   |   2   | _<1> <2> <Sym_ | Unequal
| `<`    |   2   | _<1> <2> <Sym_ | Less
| `>`    |   2   | _<1> <2> <Sym_ | Greater

```minimaL
2 A :
2 B :
A B = C :
```

`C` _answers_ `1`.

### A Deeper Look

```minimaL
2 A :
1 B :
A B - C :
C 0 = D :
D B - E :
```

- Answers; Step-by-Step
  1. _Pass_ values to `A` and `B`
     - `A` _contains_ `2`
     - `B` _contains_ `1`
  2. _Substract_ `B` and `A`; _answers_ `1`
     - _Pass answer_ to `C`;
  3. _Compares_ `C` and `0`; _answers_ `-1`
     - _Pass answer_ to `D`;
  4. _Substracts_ `B` and `D`;
     - _Pass answer_ to `E`
  5. _Answer_ is `0`

```minimaL
2 1 > L :
2 1 = Q :
```

- Answers
  1. [_L_] 1 (`'t`); is true
  2. [_Q_] 0 (`'f`); is false

## Arithmetic

| Symbol   | Count | Syntax         | Name
| -------- | :---: | -------------- | ----------------
| `+`, `-` |   2   | _<1> <2> <Sym_ | Plus, Minus
| `*`, `/` |   2   | _<1> <2> <Sym_ | Multiply, Divide
| `**`     |   2   | _<1> <2> <Sym_ | To-Power-of

```minimaL
2 3 + 2 *
```

Is equivalent to `(2 + 3) * 2`. \
_Answer_ is `10`.

## Bit-Operation

| Symbol | Syntax       | Name
| ------ | ------------ | ---------------------------------------------
| `'{`   | _Sym> <a?$n_ | Set-Catch-List-alpha_symbol-To-Byte-Size-Of-n
| `'{=`  | _Sym> <$n_   | Set-Default-Catch-List-Byte-Size-To-n

- **Notice**
  - You can use [`$`](built-in_type#bit) to mark a value as a bit-field. \
  `$010` is a short-cut for `010 >bit`.
  - `'{=$4` _(A is size of 4)_ is default size; if not defined otherwise.
  - `'{A$`, `{A$0` use the defined default size.

- See
  - [Set byte-size](#set-byte-size)
  - [Built-in type _Bit_](built-in_type#bit).

| Symbol | Count | Syntax     | Name
| ------ | :---: | ---------- | ------------------
| `shl`  |   1   | _<1> <Sym_ | Bit-Shift-to-Left
| `shr`  |   1   | _<1> <Sym_ | Bit-Shift-to-Right
| `shlc` |   1   | _<1> <Sym_ | `shr`-circular
| `shrc` |   1   | _<1> <Sym_ | `shl`-circular
| `and`  |   2   | _<2> <Sym_ | Bit-And
| `or`   |   2   | _<2> <Sym_ | Bit-Or
| `xor`  |   2   | _<2> <Sym_ | Bit-Or-Exclusive
| `not`  |   1   | _<1> <Sym_ | Bit-Not
| `nand` |   2   | _<2> <Sym_ | Bit-Not-And
| `nor`  |   2   | _<2> <Sym_ | Bit-Not-Or

- **Notice**: The operations `nand` `nor` and `xor` are _[syntatic sugar](built-in_syntactic-sugar)_.
- **Hint**:   You can use [`$`](built-in_type#bit) to mark a value as one bit or as a sequence of bit.
- **Notice**: `$A` and `A` are equal. So you can use `$` as a hint.

- _**Important**_: Typing `$1230` is equal to type `$1110`!
- _**Important**_: To avoid an _overflow_ set byte size great enough. See above.

### Set byte-size

- `$01 shr` results in `$00`.
  - An _underflow_ can be catched by using a _catch-list_ \
    `'{#n` where `#` is an alphabetical symbol and `n` a size. \
    example: `$01 shr : '{A$8`; `'{A$8` answer is `$00000001`. \
    A byte size of '4' is the default size; \
    if not defined otherwise like `'{=$8`.
- `$10 shl` results in `$00`.
  - To avoid an _overflow_ set byte size great enough or use a _catch-list_.

See [Catch-List](built-in_special#catch-list).

#### Logic (Bit)

```minimaL
$0001 $0011 and  : $A
$0011 $0001 xor  : $B
$0011 $0001 or   : $C
$0011 $0001 nand : $D
$0110 not        : $E
$0011 $0110 nor  : $F

{ $01 $11 } $10 and : $G
```

- _answeres_ / and Explanation
  - _`$A`_ `$0001` `=` 1; (_'t_ if _1_ and also _2_).
  - _`$B`_ `$0100` `=` 4; (_'t_ if _1_ or _2_ but not _1_ and _2_).
  - _`$C`_ `$0011` `=` 3; (_'t_ if _1_ or _2_ or _1_ and _2_).
  - _`$D`_ `$0110` `=` 5; (_'t_ if _1_ and not _2_)
  - _`$E`_ `$0011` `=` 3; (_'t_ if none in _-_    / equivalent to `$110 or  $010`)
  - _`$F`_ `$1000` `=` 0; (_'t_ if not _1_ or _2_ / equavalent to `$011 nor $110`)
  - _`$G`_ `{$00 $10}` `=` {0 2}; (see above and below)

### Shift

```minimaL
$0010 shl   : A
$0010 shr   : B
$1000 shlc  : C
$0001 shrc  : D
$0010 2 shl : E
```

**Notice**: `shlc` and `shrc` are _sugar_.

- _answeres_
  - `A` `$0100` `=` 1
  - `B` `$0001` `=` 1
  - `C` `$0001` `=` 1
  - `D` `$1000` `=` 8
  - `E` `$1000` `=` 8

## Sugar (_Value-List_)

| Symbol     | Count | Syntax         | Name
| ---------- | :---: | -------------- | ----------
| `{` .. `}` |   1   | _Sym> <> <Sym_ | Value-List

See also [More Sugar](built-in_more-sugar#value-list).

A value-list ..

```minimaL
{ 0 1 2 3 } 2 ** { A B C D } :
```

- Answers
  A. 0
  B. 2
  C. 4
  D. 9

## Branch (Anchor, Condition, Jump)

In other programming languages, \
an anchor is also known as a label (goto <>).

| Symbol | Count | Syntax        | Name
| ------ | :---: | ------------- | ---------------
| `..`   |   1   | _Sym> <>Anch_ | Set-Anchor
| `?`    |   1   | _<> ~ <Sym_   | Check-Condition
| `::`   |   1   | _>Anch <Sym_  | Jump-To-Anchor

_Note_: See [Label (Flow Control)](built-in_flow-control.md#label).

| Symbol | Count | Syntax    | Name
| ------ | :---: | --------- | -----------
| `f?`   |   1   | _<> <Sym_ | Check-False
| `t?`   |   1   | _<> <Sym_ | Check-True

| Symbol | Alias
| ------ | -----
| `0?`   | `f?`
| `1?`   | `t?`

```minimaL
1 .get Age :

.. Test-for-legal-age
[
  18 : Legal-Age

  Age Legal-Age >= 1? Access-Granted ::
  :: Access-Denied
]
.. Access-Granted [ ]
```

/ End
