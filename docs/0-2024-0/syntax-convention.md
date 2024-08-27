# Syntax

- [Suggestions](concention.md)

1. [Overview](#overview)
2. [Basics](#basics)
   - Token
     1. [Template](#basics-token-template)
     2. [Definition](#basics-token-definition)

## Overview

| Syntax
| --------------------
| <1> `'`
| <1..*>_Identifier_
| (<0..1>`Dash`)
| (<0..*>_Identifier_)
| (<0..1>`Underscore`)

1. Symbols enclosed in round brackets are optional.
2. One number enclosed in `<` `>` shows the mandatory length.
3. The Symbol `..` between numbers indicates the permitted frequency.
   - `..*` indicates an unlimited frequency.

## Basics

1. ← [Overview](#overview)
2. [Token](#token)

### Token

1. [Template](#basics-token-template)
2. [Definition](#basics-token-definition)

#### Basics (Token Template)

1. <_TokenTemplateName_=(_Range_)>
2. <_TokenTemplateName_=_TokenList_>
3. in {_Token_}, in {_TokenTemplateName_}

#### Basics (Token Definition)

| Token              | Syntax                      | Name
| ------------------ | --------------------------- | ------------
| <_numeric_=(0..0)> | _Token_ _Token_*            | Numeric
| <_nocap_=(a..z)>   | (_Token_?  _Token_*)+       | Alpha-NoCap
| <_allcap_=(A..Z)>  | (_Token_? _Token_*)+        | Alpha-AllCap
| <_alpha_>=(A..z)>  | _in_ {_allcap_ & _nocap_}+  | Alpha
| _alpha_numeric_    | _numeric_? (in {_alpha_}+)  | AlphaNumeric
