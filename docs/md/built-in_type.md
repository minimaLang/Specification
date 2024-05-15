# Type

- [Variable](#variable)
- [Literal](#literal)
- [Character](#character)

Read about the syntax convention used [Syntax Convention](syntax-convention).

## Variable

| Token           | Length | **Case-Sensitive?** | Allowed Infix Character |
| :-------------: | :----- | :------------------ | :---------------------  |
| _Alpha-Numeric_ | 2..*   | No                  | `-`, `_`                |
| _Alpha-Numeric_ | 1      | Yes                 |                         |

- _Valid_
  - `A`, `AB`
  - `AB1`, `A1B`, `1AB`
  - `1A`, `AB-1`,
  - `1A_`, `AB_1`
  - `VARIABLENAME`
  - `Variable-Name`
  - `Name_`
- _Invalid_
  - `1 A`
  - `1?A`
  - `A_B`
  - `A-B`

## Literal

| Name       | Token           |
| :--------: | :-------------- |
| Symbol     | `'`             |
| Identifier | _Alpha-Numeric_ |
| Dash       | `-`             |
| Underscore | `_`             |

| Syntax                |
| :-------------------: |
| <1> `'`               |
| <1..*> _Identifier_   |
| (<0..1> `Dash`)       |
| (<0..*> _Identifier_) |
| (<0..1> `Underscore`) |

- _Valid_
  - `'A0`
  - `'0`
  - `'0A`
  - `A`
- _Invalid_
  - `'!`
  - `'A:`

## Character

| Syntax | Token       |
| :----- | :---------: |
| Begin  | `"`         |
| ...    | _Character_ |
| End    | `"`         |
