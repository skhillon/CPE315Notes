## Day 15 - Pipeline Quiz Review

## Number 1
You end up with data hazards with every `ldr` and `add` since `add` depends on a value that isn't done yet. That's why you move `ldr`s up above the additions so you don't waste clock cycles.

## Number 2
**Original**
Extra 5 cycles on the last iteration of the loop comes from incorrect prediction penalty (see manual). The 6 cycles is the 6 instructions before the branch in the loop.

Same principle for next one.
