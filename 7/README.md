---
domain: rfc.ethereumclassic
shortname: 7/EXP
name: EXP Cost Increase
status: raw
editor: Wei Tang <hi@that.world>
---

This refers to the EXP cost increase hard fork. The EIP can be found
at [EIP-160](https://github.com/ethereum/EIPs/issues/160).

## Fee Schedule

If `block.number >= FORK_BLKNUM`, increase the gas cost of EXP from
10 + 10 per byte in the exponent to 10 + 50 per byte in the exponent.
