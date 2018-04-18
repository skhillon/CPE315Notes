# Day 8 - Wed, April 18, 2018

## Amdahl's Law

- Speedup due to enhancement E. See slides for formula.
- Design principle is to make the common case fast.


ExecutionTime(with E) = (1-F) + F/S) * ExecutionTime(wihout E)
Speedup(with E) = 1 / ((1-F) + F / S)

Suppose E = 1s, F = 25%, S = 2x.
= 0.875 original execution time

## CPI Example (not in the slides for some reason)
Suppsoe we have 2 implementations of the same instruction set architecture (ISA)

For some program
A: clock cycle 10 ns, CPI 2.0
B: clock cycle 20 ns, CPI 1.2

**Which machine is faster for this program, and by how much?**
For A: (10 ns/cycle) x (2.0 cycles / instruction) = 20 ns/instruction average CPI.
Inverse gets you 8 MIPS (Million Instructions Per Second).

For B: (20 ns/cycle) x (1.2 cycles / instruction) = 24 ns/instruction average CPI.
Inverse gets you 

*Therefore, A is the faster machine*

**If 2 machines have the same ISA for a given program, which of our quantities will always be identical?**
Ans: Number of instructions stays the same. It just might happen faster on a faster version of the same ISA.

## Number of Instructions Example
Trying to decide which sequence of instructions is best for a given machine.
3 different classes of instructions, requiring 1, 2, and 3 cycles, respectively.

Sequence 1 has 5 instructions: 2xA, 1xB, 2xC.
Sequence 2 has 6 instructions: 4xA, 1xB, 1xC.

**Which sequence is faster? By how much?**
Sequence 1: 1x2 + 2x1 + 3x2 = 10 total cycles
Sequence 2: 1x4 + 1x2 + 1x3 = 9 total cycles.

Therefore sequence 2 is faster by 1 cycle. Notice how it has more instructions, but there are more of Instruction A, a less-intense instruction vs in sequence 1 which has more of an intense instruction C.

**What is the CPI for each sequence**
?ok

## MIPS Example
2 different compilers being tested for 3 GHz machine with 3 different classes of instructions: A, B, C. They have the same cycles required as in the previous slide.

First compiler uses 5 million of A, 1 million of B, and 1 million of C.
Second compiler uses 10 million of A, 1 million of B, and 1 million of C.

*(Recall GHz in CPE is billions of instructions per second)*

**Which sequence will be faster according to MIPS?**
Sequence 1 has 7 Million instructions. Sequence 2 has 12 Million instructions.
The first sequence will be faster.

*(Note that this could have easily be done; the only difference between the 2 sequences was in number of instruction A, so you could have easily chosen 1)*

**Which sequence will be faster according to execution time?**
Sequence 1: 5M * 1 + 1 M * 2 + 1 M * 3 = 10 M cycles / 7 M instructions = 1.42 CPI.
Sequence 2: 10M * 1 + 1 M * B + 1 M * 3 = 15 M cycles / 12 M instructions = 1.25 CPI.

Time is 1/Cycles per instruction, so in this case we choose the smaller number. Therefore, sequence 2 is faster according to execution time.

