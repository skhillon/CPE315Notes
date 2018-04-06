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

```ARM
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




