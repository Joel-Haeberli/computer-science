tags: #memory #heap #overflow 

# Heap Attacks

links: [[903 ED TOC - Memory Layout|ED TOC - Memory Layout]] - [[themes/000 Index|Index]]

---

## Buffer overflow

**Inter-chunk overflow**

![[inter-chunk-overflow.png]]

**Inter-chunk overflow with management chunk**

- can modify management data of heap allocator $\rightarrow$ can modify behaviour of heap allocator

![[inter-chunk-overflow-2.png]]

**Inter-chunk overflow with chunk metadata**

- can modify management data of heap allocator $\rightarrow$ can modify behaviour of heap allocator
- create fake chunks

![[inter-chunk-overflow-3.png]]

## Use after free (UAF)

Use an object after the memory it has been pointing to has been freed, and now a different object is stored at that location.

---
links: [[903 ED TOC - Memory Layout|ED TOC - Memory Layout]] - [[themes/000 Index|Index]]