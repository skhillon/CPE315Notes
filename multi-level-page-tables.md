# Last Quiz Day - Wed, June 6th

## Multi-level page tables
If you have a 32-bit machine with a flat page table containing a 12-bit index, you're going to have 2^20 entries, which is very large.

In a multi-level page table, you split up the non-offset part of the bit into as many levels as you need. Then you have smaller page tables.

ex) `[10 bits][10 bits][12 bit offset]`

Gets you two levels of page tables, each 2^10 size. Worst case, you have each primary index used and you have 2^10^10 --> 2^20. However, the savings is that this usually doesn't happen, and you only use a few of the indices in the first level, keeping you much closer to 2^10 bits used.

Best case scenario, you have 8K. Worst case, you have 4K * 4K * 2^10th, which is way worse, but much more rare.
