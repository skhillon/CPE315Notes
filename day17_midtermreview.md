# Day 17 -- Midterm Review -- Friday, May 11

## Quiz Review
TBH I missed most of the quiz review lmao

## Pipeline stuff (See 16.2 for table)
**The following are in separate pipelines, but may end up writing to the same registers. Requires locks.**

ARITHMETIC: SH      ALU     SAT     WB

LOAD/STORE: ADDR    M1      M2      WB

```assembly
ldr     r1, [r2, #0]
ldr     r3, [r1, #3]
add     r0, r3, #4
```

Of the 3 instructions, add will finish first because ADD will be issued to ALU pipeline, but LDR will be delayed by the other LDR that was using the pipeline before it.

## Midterm Review

### Q1
There were 4 main problems, of which you needed to list 3:
1) `push` and `pop` don't match.
2) Didn't push `lr` and pop `lr`.
3) `r4` is used in code, is popped but doesn't get pushed. Not doing callee-save correctly.
4) After `bl myarray`, `r2` is being used while assuming its value was not changed during the call to `myarray`. You cannot assume that `r0` through `r3` will stay the same when pushing a new frame onto the stack.

### Q2
Noice. 100%.

### Q3 (RIP)
With size=10, you're gonna go through the inner loop 100 times and outer loop 10 times.

So it's going to be 10(9xinner + 1 miss (x6)) 

- The more iterations you have, the branch mispredicts become a smaller percentage of the whole instructions, and the CPI converges as n->\infty
- Assumption on loops is that it will always go back up instead of going down.
