# Day 10 -- Introduction to Pipelines
Fun fact--it comes from Henry Ford's production line, not from CS.

## Laundry analogy
Let's say you have to do laundry. It takes 30 minutes to wash clothes, 30 minutes to dry clothes, and another 30 to fold your clothes. Your latency is 90 minutes. Doing this 4 times takes 360 minutes, or 6 hours.

However, no one actually does this sequentially. If you have 2 loads, and you move clothes to the dryer, then your washer is not doing anything. You can start a new load! This is pipelining.

In real life, another problem was that one person had to know the whole process in the sequence. Instead, you could have specialists for each stage and increase efficiency.

**Cycles**
- Cycle 1 has load 1 in the washer.
- Cycle 2 has load 1 in the dryer and load 2 in the washer.
- Cycle 3 has load 1 being folded, load 2 in the dryer, and load 3 in the washer.
- Cycle 4 has load 1 completed, load 2 being folded, load 3 in the dryer, and load 4 in the washer.
- Cycle 5 has loads 1 and 2 completed, load 3 being folded, load 4 in the dryer, and nothing in the washer.
- Cycle 6 has loads 1, 2, and 3 completed and load 4 being folded.
Complete.

The throughput for a linear, non-pipelined sequence is 360 minutes.
The throughput for a pipelined sequence is 180 minutes.
Speedup is 360 / 180 = 2x.

If you had more laods to wash, speedup would be greater. That's because the "inactive" wash/dry/fold stages in the beginning and end become a smaller percentage of all cycles. So if you had 12 cycles instead of 6, the beginning and end cycles with "empty" stages are a smaller percentage.

