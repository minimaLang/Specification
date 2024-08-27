# Flow Control

- [Loop](#loop)
- [Branch](#branch)
  - [Define](#define)
  - [Jump](#jump)

## Loop

A _Loop_ is a combination of a _Branch_ (Jump) and a _Comparsion_.

```minimaL
200 : A
10  : B
.. Loop1
  A B - : C
  C 0 ?0 : Loop1 !
```

In other programming language is this equvialent to

```pseudocode
  Do { C = A - B }
  Until { C == 0 }
```

- See
  - [Comparsion](built-in_operation#comparsion)
  - [Branch](built-in_operation#branch)

## Branch

| Name      | Token       |
| --------- | ----------- |
| Condition | `?0`, `?1`  |
| Branch    | _label_ `!` |

| Syntax      |
| ----------- |
| _Condition_ |
| _Value_     |
| _Branch_    |
| _Label_     |

The jump target is a [Label](#label).

- _Example_
  1. `20 21 - 0  ?0 : Jump !`
- _Invalid_
  1. `20 21 - 0  ?0   Jump !`
  2. `20 10 -    ?0 : Jump !`
  3. `20 21 - 0     : Jump !`
  4. `20 21 - 0 ?0  : Jump`

1. Colon missing (`:`)
2. No comparative value
3. Condition missing
4. Branch-Symbol missing (`!`)

## Label

| Token |
| ----- |
| `..`  |

See [Branch](#branch), [Loop](#loop)

- [Define](#define)
- [Jump](#jump)

A _Label_ can be used to ...

1. name a
   - code block
   - jump target
2. to define a
   - function equivalent; like other programming languages
   - See [Tips and Tricks - Simulation a function](tips-and-tricks#simulating-a-function)

### Define

| Token | Syntax     | Name      |
| ----- | ---------- | --------- |
| `..`  | `..` label | Set-Label |
| `..`  | label `..` | Get-Label |

### Jump

| Token | Syntax     | Name    |
| ----- | ---------- | ------- |
| `!`   | label `!`  | Jump-To |
