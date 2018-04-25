# Day 11 - Wednesday, April 25

## Loop Unrolling
Instead of using branches, copy and paste your code for the amount of loops required. See if the lack of expensive branching operations makes your program faster.

## Pipelining Continued
(Time of longest stage) * (Number of instructions) + (Times of running stages).

On a processor, instead of talking about loads in washer and dryer (from analogy), the stages of the pipeline are phases of the instruction cycle (recall 225), e.g. load, instruction fetch, fetch operands, read to registers, etc.

On the ARM, the phases of the instruction cycle are as follows:
1. Fetch
2. Decde
3. Execute (this comes before accessing memory because this stays in the ALU).
4. Access Memory
5. Write Back (update registers)

## Where you can run into problems.

Let's say you have code like this.

```assembly
add     r1, r2, r3
sub     r4, r1, r3
eor     r5, r4, r1
```

Now let's examine the cycles.

|    | FETCH | DECODE | EXEC | MEM | WB |
|----|-------|-------|-----|-----|----|
| C1 | add   |        |      |     |    |
| C2 | sub   | add    |      |     |    |
| C3 |       | sub    | add  |     |    |

... and so on...

**What's the problem with the above pipeline?**
Notice how `add` stores the result in r1, and then `sub` uses that result to do its own operation. However, if you were to pipeline like in the table above, r1 would not be updated for `sub`. *This is called a DATA HAZARD*, or a *read-after-write* hazard. Common hazard on RISC architecture like ARM.

What's the solution?
- **Stall Cycles**: Pause the execute (computing) instruction and insert "stall cycles" (copies of the execute phase to fill cycles until the previous instruction is done). This method will fix any kind of data hazard and is very safe, but it's barely any faster and kind of a "waste" of pipelining. You're essentially just waiting slightly less than a synchronous solution. Downside is that CPI goes way up by definition of inserting stall cycles.
- **Forwarding**: The result for `add` is done by the Execute phase of its instruction cycle. Instead of waiting for cycle 1 to complete, cycle 2 for `sub` can just feed the output from the Execute phase to where r1 should be. The delay of this is much smaller than stall cycles. Some sort of hardware switch that intercepts output and redirects to input, so the delay is really just the amount of time electrons need to travel from the end of the switch to the beginning.
