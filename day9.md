# Day 9 - Friday, April 20, 2018

## Quiz Review

- Mostly used the correct setup to f1.
- Used .global and a label name.
- Did have to push link register at some point so you could return, otherwise branches would corrupt that register.
- To be able to get address of a for the first call and address of b for the second call, you need to push it onto the stack and then move stack pointer accordingly. Then store those addresses in registers.
- When you're done, you can pop the PC.

## RISC Processor Examples
- For example, to speed things up on ARM, don't have functions with more than 4 arguments because you only have 4 registers for passing args. More requires loads onto stack, which is much slower. This way, you can stay in the ALU.

Ex) How much faster would a machine be if a better data cache reduced the average load time to 2 seconds from 5 seconds?
Now 45% time goes to 25%. CPI goes to 2.2 from 1.6. Speedup of 37.5%.

Ex) How does this compare with using branch prediction to shave off a cycle?
idk

Ex) What if 2 ALU instructions could (always) be executed at once? *(Note: this is different than deleting half the ALU operations!)*
This time, cycles don't change; instead, you're going to halve all the frequencies.

## Example (Amdahl's Law 1)

Execution time after Improvement = Execution Time Unaffected + (Execution Time Affected / Amount of Improvement)

*Ex) Suppose a program runs in 100 s on a machine, with multiplication responsible for 80 s of this time. How much do we have to improve the speed of multiplication if we want the program to run 4 times faster?*

oldtime = 100 s
multtime = 80 s
speedup = 4
x = unknown

100 / 4 = 25 s = (20 s  + 80s / x)
5 = 80 / x
x = 16 times faster.

Therefore, multiplication needs to be improved by a factor of 16 to speed up the whole program by 4x.

*Ex) Suppose we enhance a machine making all floating point instructions to run 5x faster. IF the execution time of some benchmark before the floating point enhancement is 10 seconds, what will the speedup be if half of the 10 seconds is spent executing floating point instructions?*

oldtime = 10s
floatingpointtime = 5s
speedup = 5
x = unknown

(5 - 5/5) = 4

## Example (Compiler Optimization)
You want to understand the performance of a specific program on your 3.3 GHz machine. You collect the following stats for the instruction mix:
(See slides)

