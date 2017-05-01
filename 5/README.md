---
domain: rfc.ethereumclassic
shortname: 5/FEE
name: Gas Cost Changes for IO-heavy Operations
status: deprecated
editor: Wei Tang <hi@that.world>
---

This refers to the IO-gas cost change hard fork. The EIP can be found
at
[EIP-150](https://github.com/ethereum/EIPs/issues/150).

## Fee Schedule

Fees below has changed:

* Increase the gas cost of EXTCODESIZE to 700
* Increase the base gas cost of EXTCODECOPY to 700
* Increase the gas cost of BALANCE to 400
* Increase the gas cost of SLOAD to 200
* Increase the gas cost of CALL, DELEGATECALL, CALLCODE to 700
* Increase the gas cost of SUICIDE to 5000
* Increase the recommended gas limit target to 5.5 million
* If a call asks for more gas than the maximum allowed amount, do not return an OOG error; instead, call with the maximum allowed amount of gas
* If SUICIDE hits a newly created account, it triggers an additional gas cost of 25000 (similar to CALLs)
