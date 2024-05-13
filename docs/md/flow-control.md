# Flow Control

- [Loop](#loop)
- [Branch](#branch)
  - [Define](#define)
  - [Jump](#jump)

## Loop

A _Loop_ is a combination of a _Branch_ and a _Comparsion_.

```minimaL
A 200 :
B  10 :
.. Loop1
  A B - : C
  C 0 ?0 : Loop1 ..
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

| Name      | Token      |
| :-------- | :--------: |
| Condition | `?0`, `?1` |
| Branch    | `:`        |

| Syntax      |
| :---------: |
| _Condition_ |
| _Value_     |
| _Branch_    |
| _Label_     |

The jump target is a [Label](#label).

- _Valid_
  1. `20 21 - 0 = ?0 : Jump ..`
  2. `5 5 - 0 = : A ?0 : Jump ..`
- _Invalid_
  1. `20 21 - 0 = ?0 Jump ..`
  2. `20 21 - 0 = :`

## Label

| Token |
| :---: |
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

| Syntax            |
| :---------------: |
| _Token_ LabelName |

### Jump

| Syntax            |
| :---------------: |
| LabelName _Token_ |
