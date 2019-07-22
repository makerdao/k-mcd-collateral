```k
rule (P *Int pow176 +Int Q *Int pow168 +Int X *Int pow160 +Int A) /Int pow160 => P *Int pow16 +Int Q *Int pow8 +Int X
  requires #rangeBool(P)
  andBool #rangeBool(Q)
  andBool #rangeUInt(8, X)
  andBool #rangeAddress(A)

rule 255 &Int (P *Int pow16 +Int Q *Int pow8 +Int X) => X
  requires #rangeBool(P)
  andBool #rangeBool(Q)
  andBool #rangeUInt(8, X)
```
