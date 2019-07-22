```k
syntax Int ::= "pow8"  [function]
syntax Int ::= "pow16" [function]
syntax Int ::= "pow80" [function]
rule pow8    => 256     [macro]
rule pow16   => 65536   [macro]
rule pow80   => 1208925819614629174706176 [macro]

syntax Int ::= "#PausableToken.paused_filler_fillerr_fillerrr"
rule #PausableToken.paused_filler_fillerr_fillerrr => 3

syntax Int ::= "#PausableToken.balances" "[" Int "]" [function]
rule #PausableToken.balances[A] => #hashedLocation("Solidity", 0, A)

syntax Int ::= "#PausableToken.approvals" "[" Int "]" "[" Int "]" [function]
rule #PausableToken.approvals[A][B] => #hashedLocation("Solidity", 2, A B)

syntax Int ::= "#WordPackBoolBoolUInt8Addr" "(" Int "," Int "," Int "," Int ")" [function]
rule #WordPackBoolBoolUInt8Addr(A,B,X,Y) => Y *Int pow80 +Int X *Int pow16 +Int B *Int pow8 +Int A
  requires #rangeBool(A)
  andBool #rangeBool(B)
  andBool #rangeUInt(8,X)
  andBool #rangeAddress(Y)
```
