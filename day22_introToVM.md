# Day 21 -- Wed, May 23

- Every process in an n-bit computer gets to pretend it has the entire virtual memory space; e.g. 2^n bits to use.

The space looks like this:
----
CODE
----
GLOBALS
----
HEAP (goes down)
----
STACK (goes up)
----

## Virtual Pages
- Each virtual address space is divided into blocks called **pages**
- Page size is typically 4-16 KB
- Main memory is also divided into same-size physical pages, but real amount of space available is different than the program thinks it has.
- Memory management in the operating system maps a virtual page to a physical page.
- When you look at the memory addresses and you get a value, that's a virtual memory location. That gets translated to some physical memory location on the actual computer hardware. This is done with **table look-ups**
- Each process may have more than one page mapped to it.

## Address Translation
- Addresses have two parts:
    1) **Page Number**: A mapping assigned by the OS.
    2) **Page Offset**, which is not mapped. Assigned to a particular byte location (how is this different?)

## Page Table Register
- A **page table register** holds the starting address of a process's page table, which is written by the OS when the process is activated.
- It's used as an index into the page table.
- If the index isn't mapped, we get a **page fault** (to be discussed later).
- Page number + value in register = raw address in memory.

## Key things to understand from this intro lecture.
- Each process in VM gets mapped to individual blocks that do not overlap
- Each process thinks it has its own address space, has no knowledge of others that are running.
- How that really happens is through the use of tables, where you have your virrtual address which gets split into a page number, which indicates the page in the page table you're going to access, and then the offset into that individual page of memory to access that data element.
- Number of bits used to identify offset also indicates size of block.
- Page Table Register contains address of wherever the table starts in memory, which gives you the index into the array element. See if it's valid, you get a physical address out of it.
- Each memory access without any mitigating hardware features to make the process easier requires 1 access to memory to get page table entry for physical memory, and then a 2nd to actually go into physical memory and get that data.
