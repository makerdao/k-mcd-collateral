```k
rule (X *Int pow176 +Int Y *Int pow168 +Int Z *Int pow160 +Int A) /Int pow160 => X *Int pow16 +Int Y *Int pow8 +Int Z
  requires #rangeUInt(8, X)
  andBool #rangeUInt(8, Y)
  andBool #rangeUInt(8, Z)
  andBool #rangeAddress(A)

// specialised
rule (Y *Int pow168 +Int Z *Int pow160 +Int A) /Int pow160 => Y *Int pow8 +Int Z
  requires #rangeUInt(8, Y)
  andBool #rangeUInt(8, Z)
  andBool #rangeAddress(A)

rule 255 &Int (X *Int pow16 +Int Y *Int pow8 +Int Z) => Z
  requires #rangeUInt(8, X)
  andBool #rangeUInt(8, Y)
  andBool #rangeUInt(8, Z)

// specialised
rule 255 &Int (Y *Int pow8 +Int Z) => Z
  requires #rangeUInt(8, Y)
  andBool #rangeUInt(8, Z)

// specialised
rule (X *Int pow176 +Int Y *Int pow160 +Int A) /Int pow160 => X *Int pow16 +Int Y
  requires #rangeUInt(8, Y)
  andBool #rangeUInt(8, X)
  andBool #rangeAddress(A)

rule 255 &Int (X *Int pow16 +Int Y) => Y
  requires #rangeUInt(8, Y)
  andBool #rangeUInt(8, X)

rule (pow176 *Int X +Int pow168 *Int Y +Int A) /Int pow160 => pow16 *Int X +Int pow8 *Int Y
  requires #rangeUInt(8, X)
  andBool  #rangeUInt(8, Y)
  andBool  #rangeAddress(A)

rule 255 &Int (pow16 *Int X +Int pow8 *Int Y) => 0
  requires #rangeUInt(8, X)
  andBool  #rangeUInt(8, Y)
```
