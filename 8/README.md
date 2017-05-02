---
domain: rfc.ethereumclassic
shortname: 8/DIFF
name: Ethereum Blocks, State and Transaction with Difficulty Bomb Delay
status: stable
editor: Igor Artamonov <splix@ethereumclassic.org>
---

Derived
from
[ECIP1010](https://github.com/ethereumproject/ECIPs/blob/master/ECIPs/ECIP-1010.md). See
`explanation.md` for details about this RFC.

## Changes

Compared with the EIP-150 revision of the yellow paper, equation (39) should be replaced by:

````
if (block.number < pause_block) {
    explosion = (block.number / 100000) - 2    
} else if (block.number < cont_block) {
    explosion = fixed_diff
} else { // block.number >= cont_block    
    explosion = (block.number / 100000) - delay - 2
}

block_diff = parent_diff
      + parent_diff / 2048 * max(1 - (block_timestamp - parent_timestamp) / 10, -99)
      + int(2**explosion)
````

With this changes min difficulty value will become:
* Block 2,500,000 == 2**23 == 8,388,608
* Block 3,000,000 == 2**28 == 268,435,456
* Block 4,000,000 == 2**28 == 268,435,456
* Block 5,000,000 == 2**28 == 268,435,456
* Block 5,200,000 == 2**30 == 1 TH
* Block 6,000,000 == 2**38 == 274 TH

## Links

Difficulty growth model: https://docs.google.com/spreadsheets/d/1ZXNrSCNV0HGWU7zOTUyIIRUGv5M44P6wiAZclpY4Y2Q/edit
