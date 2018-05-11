# Day 14 - Wed, May 2

## Quiz review

### Q1
- Basically, compute CPI of both and compare the two.
- Cindy = (2/3 cycles * 1 cycle/instruction) + (1/3 cycles * 7 Cycle/Instruction) = 9/3 = 3 CPI
- Ramon = (2/3 cycles * 1 cycle/instruction) + (1/3 cycles * 20 cycle/instruction) = 22/3 CPI = 7.333... CPI

(22/3) / 3 = 22/9 = 2.4444..... x faster. Cindy has more cycles completed per instruction. Therefore, Cindy's program's overall runtime will be 2.44x faster than Ramon's program.

### Q2
Don't have to worry about clock speed since you're on the same processor.

Cindy IPC = 1/CPI = 1/3
Ramon IPC = 1/CPI = 1/1 = 1

IPS = CS + 1 PC

Therefore, regardless of actual number of cycles required, Ramon's IPS will be 3 times higher than Cindy's program.

## Things to know for quiz
- **Cycles**: Minimum cycles to complete instruction.
- **Result latency**: Number of cycles before results are ready for forwarding.
- **Early register**: Values needed before operation. Can cause pipeline stalls.
- **Late register**: Values needed after the operation. Not impacted by any forwarding conflict.

## Common Cycle times for instructions
- LDR takes 1 cycle. Shift register is an early register.

