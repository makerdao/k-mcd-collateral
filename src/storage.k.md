```k
syntax Int ::= "#PausableToken.balances" "[" Int "]" [function]
rule #PausableToken.balances[A] => #hashedLocation("Solidity", 0, A)

syntax Int ::= "#PausableToken.approvals" "[" Int "]" "[" Int "]" [function]
rule #PausableToken.approvals[A][B] => #hashedLocation("Solidity", 2, A B)
```
