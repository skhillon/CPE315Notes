# Day 21 - Caches Quiz

He skipped the Hit/Miss chart thing

## 1
(a) Byte offset, 16 bytes per block requires 4 bits to be able to identify any block (2^4 = 16).
(b) Index -- need to figure out how many blocks. 16 bytes per block, 128 KB available. 128KB = 2^17, 16 = 2^4, 2^(17-4) = 2^13, so 13 bits required.
(c) Bits for tag is whatever is remaining. We had 32 bits, used 4 for the offset, and used 13 for the index. 32-17 = 15 bits for tag.

## 2
(c) Key is figuring out the denominator. 100% of the time, instruction cache will be accessed. 20% of instructions are loads and stores to data, so we get a 1/1.2 ratio for instruction and 0.2/1.2 for data.

## 3
Penalties are all part of the smaller layer. Memory is penalty for layer 3, layer 3 is penalty for l2, and so on.

