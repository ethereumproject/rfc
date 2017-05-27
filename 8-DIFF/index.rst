:editor: Igor Artamonov <splix@ethereumclassic.org>

8-DIFF: Ethereum Blocks, State and Transaction with Difficulty Bomb Delay
=========================================================================

.. toctree::

   explanation

Derived from
`ECIP1010 <https://github.com/ethereumproject/ECIPs/blob/master/ECIPs/ECIP-1010.md>`__.
See ``explanation.md`` for details about this RFC.

Changes
-------

Compared with the EIP-150 revision of the yellow paper, equation (39)
should be replaced by:

::

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

Using constants:

::

    pause_block = 3000000 //15 Jan 2017
    cont_block = 5000000 //15 Dec 2017
    delay = (cont_block - pause_block) / 100000 //20
    fixed_diff = (pause_block / 100000) - 2 //28
