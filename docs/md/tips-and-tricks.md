# Tips and Tricks

## Simulating a function

_minimaL_ does not provide a routine syntax. \
If you need one you must 'simulate' it.

```minimaL
.. SetName {
  O "" = ?1 : O "Alice" :
  "Hi, " O ++ R :
}

O "Bob" :
SetName ..
O "Alice" = ?1 : Exit ..
?0 : OK ..
```

`R` _Answers_ `Bob`.
