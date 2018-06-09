# Professor Lupo Final Review Session - June 9, 2018
Content is also in CHEMISTRY section of paper notes and in Toby tabs

## 3a) See paper notes

## Last problem, pipeline hw

BTAC (Branch Target Access Cache): purpose is which instruction to fetch next, use last 3 bits.

0 - WT - loop

For the second one, we assume forward branches are weakly not taken and backwards are strongly taken.
The address after this branch would be L2

**BTAC**

|Position | Branch type | Destination|
| ------- | --------- | ------- |
|0 | Weakly Taken | loop |
| 6 | Strongly Taken | L2 |

## Final, Problem 5: See paper notes

## 3b) Caches -- see paper notes

## Register Usage
Assuming `func1(a, b, c, d, e, f, g)`:
- a --> r0, b --> r1, ... d --> r3
- e --> sp
- f --> sp + 4
- g --> sp + 8

Even though when you `push`, it's `sp - 4` normally. This is because technically you're pushing in reverse order from the caller function, so it's `sp + 4`.

Now imagine you did `push { r7, lr }` --> lr and then -4 --> r7 (this is all below the stuff above)

So now it's `g, f, e, lr, r7`. Then, for example, `ldr r7, [sp, #16]` gets `g`.

## Performance HW, #8 (find MIPS and type of processor).
