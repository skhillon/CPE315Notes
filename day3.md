# Day 3

## Registers
r0 - r3: Parameters
r4 - r12: Callee save
r0, r1: ???
r13: Stack Pointer
r14: LR
r15: Program Counter

## C to ARM Assembly

```c
void swap(int* x, int* y) {
    int temp;
    temp = *x;
    *x = *y;
    *y = temp;
}
```

```assembler
@ arm assembly

.text
.global swap
    ldr r3, [r0]
    ldr r2, [r1]
    str r2, [r3]
    str r3, [r1]
    bx lr @RET
@end swap
.global sum
```

## Externs
- If you have a variable declared as `extern`, it does not allocate space, though it adds them to the symbol table.
    - This is how you have a global variable in one file but it's actually used in another.

## Another Example
Consider the following. No real need to swap, just for example:
```c
int func(int a, int b) {
    swap(&a, &b);
    return sum(a, b);
}
```

Now to assembly code. Note that a lot of these lines aren't necessary, they're just to show features of arm.
```assembler
.text
.global func

func:
    add sp, sp, #-4     @ Move stack pointer up by 4 bytes (32-bit)
    str lr, [sp]
    sub sp, sp, #12     @ Notice you don't need to say r13, can say sp. 
    str r0, [sp, #4]
    add r3, sp, #8
    str r1, [r3, #-8]!  @ Exclamation is the same thing as `ttx;`, which modifies r3 in place (performs a transformation on an operand) and then stores into r1.
    mov r1, r3
    add r0, sp, #4      @ Move sp down another int width.
    bl swap             @ Branch and (???) to swap.
    ldr r1, [sp]
    ldr r0, [sp, #4]
    bl sum
    add sp, sp #12
    ldr pc, [sp], #4   @ Loading directly into PC, allowed. The `[sp], #4` part is the same as `x++`.
```

- Need to push link register onto stack whenever you call a function.
- Needed to push a and b onto stack, get their addresses, put those into registers so it can perform swap.
- After swap, had to get values off stack, put them into registers to call sum function.
- Then, had to pop off temporary information, pop off saved PC into the PC itself and then return.

