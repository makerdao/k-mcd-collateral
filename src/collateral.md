```act
behaviour transferFrom of PausableToken
interface transferFrom(address from, address to, uint256 value)

types
  Approval : uint256
  FromBal  : uint256
  ToBal    : uint256

storage
  balances[from]             |-> FromBal => FromBal - value
  balances[to]               |-> ToBal => ToBal - value
  approvals[from][CALLER_ID] |-> Approval => Approval - value

iff in range uint256
  FromBal - value
  Approval - value

iff
  VCallValue == 0
  to =/= 0

if
  from =/= to

returns 1
```

```act
behaviour transfer of PausableToken
interface function transfer(address to, uint256 value)


````
