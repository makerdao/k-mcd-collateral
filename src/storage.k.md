```k
syntax Int ::= "pow8"                                                [function]
syntax Int ::= "pow168"                                              [function]
syntax Int ::= "pow176"                                              [function]
rule pow8   => 256                                                   [macro]
rule pow168 => 374144419156711147060143317175368453031918731001856   [macro]
rule pow176 => 95780971304118053647396689196894323976171195136475136 [macro]

syntax Int ::= "#PausableToken.balances" "[" Int "]" [function]
rule #PausableToken.balances[A] => #hashedLocation("Solidity", 0, A)

syntax Int ::= "#PausableToken.approvals" "[" Int "]" "[" Int "]" [function]
rule #PausableToken.approvals[A][B] => #hashedLocation("Solidity", 2, A B)

syntax Int ::= "#PausableToken.filler_paused_fillerr_fillerrr" [function]
rule #PausableToken.filler_paused_fillerr_fillerrr => 3

syntax Int ::= "#WordPackUInt8UInt8UInt8Addr" "(" Int "," Int "," Int "," Int ")" [function]
rule #WordPackUInt8UInt8UInt8Addr(X, Y, Z, A) => X *Int pow176 +Int Y *Int pow168 +Int Z *Int pow160 +Int A
  requires #rangeUInt(8, X)
  andBool #rangeUInt(8, Y)
  andBool #rangeUInt(8, Z)
  andBool #rangeAddress(A)
```
