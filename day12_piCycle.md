# Raspberry Pi Cycle
				ALU
F1 	-> 	F2 	->	DECODE/	->	SHIFT, ALU, SAT		-> |	WB	 
				REG READ	->	ADDR, MEM1, MEM2 	-> |
				memory
				_________		__________________
				early regs		late regs

Forward from SHIFT, ALU, SAT, WB
Forward to SHIFT, ALU, ADDR, MEM1

```
ldr	r1[sp]		|	takes 4 cycles
add	r3, r3, r1	|

1.8, 16.1, 16.6
		C1		C2		C3		C4		C5		C6		C7		C8	
ldr	ADDR	MEM1	MEM2	WB___
add			SHIFT	ALU		xSAT |	xWB
								ALU	 |_	ALU		SAT		WB
								__________________________
									4 cycles
``` 

```
ldr	r1, [sp]
add	r3, r3, r1 lsl #1

		C1		C2		C3		C4		C5		C6		C7		C8
ldr	ADDR	MEM1	MEM2	WB
add			SHIFT	xALU	xSAT	xWB			
				SHIFT	SHIFT	SHIFT	SHIFT	ALU		SAT		WB
								_________________________________
										5 cycles
```
