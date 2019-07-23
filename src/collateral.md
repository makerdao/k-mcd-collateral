```act
behaviour transferFrom of PausableToken
interface transferFrom(address from, address to, uint256 value)

types
  Approval : uint256
  FromBal  : uint256
  ToBal    : uint256
  Paused   : uint8
  Filler   : uint8
  Fillerr  : uint8
  Fillerrr : address

storage
  balances[from]             |-> FromBal => FromBal - value
  balances[to]               |-> ToBal => ToBal - value
  approvals[from][CALLER_ID] |-> Approval => Approval - value
  filler_paused_fillerr_fillerrr |-> #WordPackUInt8UInt8UInt8Addr(Filler, Paused, Fillerr, Fillerrr)

iff in range uint256
  FromBal - value
  ToBal + value
  Approval - value

iff
  Paused == 0
  VCallValue == 0
  to =/= 0

if
  from =/= to

returns 1
```

```act
behaviour transfer of PausableToken
interface transfer(address to, uint256 value)

types
  FromBal : uint256
  ToBal   : uint256

storage
  balances[CALLER_ID] |-> FromBal => FromBal - value
  balances[to]        |-> ToBal => ToBal + value

iff in range uint256
  FromBal - value
  ToBal + value

iff
  VCallValue == 0
  to =/= 0

if 
  CALLER_ID =/= to

returns 1 
```
