# Day 7 -- Performance Optimization -- Monday, April 16

## Definitions
- Performance is in units of things-per-time (mph, MB/s). Bigger is better.
- Performance = 1 / Execution time.
- "X is n times faster than Y" means
    - n = Performance(x) / Performance(y)
    - 1.yz times faster means yz% faster

## Latency vs Throughput
- **Latency** is how long it takes to complete a single task.
- **Throughput** is how many tasks you can complete in a given amount of time.

If you upgrade one computer in a lab, you increased **latency** because it takes less time to do ONE thing.
If you upgrade all the computers in a lab, then you increased **throughput**.

Throughput is not always a raw integer higher than latency.

## Clock Cycles
Instead of reporting execution time in seconds, we usually report in cycles.

seconds / program = (cycles / program) * (seconds / cycle)

- Clock "ticks" indicate when to start activities.
- Cycle time is time between ticks, which is seconds per cycle.
- Clock rate (frequency, Hz), is cycles per second.
    - 200 MHz clock has a cycle time of (1/(200x10^6)) x 10^9 = 5 nanoseconds.

## How many cycles in a program?
You would be wrong in assuming that # of cycles = # of instructions.

- Different instructions take different amounts of time on different machines, even with the same instruction set.
- This could be because processor is faster, architecture of processor is optimized for different things.

## Different number of cycles for different instructions
- Multiplication takes more time than addition.
- Floating point operations take longer than integer ones.
- Accessing memory takes more time than accessing registers.
- *Important*: Changing the cycle time often changes the number of cycles required for various instructions. Buying a faster processor doesn't mean everything will be faster. Faster processors might have a quicker clock speed but take more cycles per instruction. Overall performance is better.

## CPI
How many clock cycles, *on average*, does it take for every instruction executed? This is called **cycles per instruction**.
Its inverse is called **IPC**, or **Instructions per cycle**.

CISC machines have higher CPI, RISC machines have lower CPI. x86 would be a CISC machine, ARM is a RISC machine. RISC optimized to do one thing only, CISC optimized to do a lot of big things.

## The Performance Equation
Time = (Cycle Time) * (CPI) * (Instruction Count)

"The only reliable measure of computer performance is time."

## Remember
- Performance is specific to a particular program. Total execution time is a consistent summary of performance.
- Performance increases on the same architecture can come from:
    - Increases in clock rate
    - Improvements that lower CPI
    - Compiler enhancements that lower CPI and/or instruction count.

Just because you improve one aspect of a machine does not mean it will be better for everything. You might, in fact, trade off.

