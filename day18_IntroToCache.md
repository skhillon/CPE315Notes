# Day 18 - Introduction to Cache

Cache is just a very small amount of very fast, easily accessible memory. It's faster than your RAM (memory) and wayyyy faster than your hard drive.

## Von Neumann Architecture
There are multiple levels of cache:
- CPU
- Level 1 Cache (128 KB)
- Level 2 Cache (128 MB)
- Memory/RAM (4 - 32 GB, usually)
- Hard drive/HDD/SSD (128 GB - 2 TB, usually)

**Analogy: Cooking** Level 1 cache is stuff next to your hand, Level 2 cache is stuff on the kitchen counter behind you, memory is like stuff in the fridge/cupboard, and hard drive is supplies in the store.

**Locality:** If you're going to access data in memory, relevant things will be put next to each other.
- **Spacial**: Items accessed are close together
- **Temporal**: If you're going to access it once, you might need to access it twice and more times.

## Modified Harvard Architecture
- CPU
- L1 instruction cache and L1 data cache.
- The rest is the same
In a true Harvard architecture, there would be completely separate memory locations for data and instructions. 

## Direct Mapped
Operates like a hash table with key-value pairs.
