tags: #mitigation #shadow #stack
 
# Shadow Stack

links: [[915 ED TOC - Further Topics|Further Topics]] - [[themes/000 Index|Index]]

---

## Shadow Stack

Shadow Stack is a separate stack which stores all return addresses. On every CALL instruction, return addresses are pushed onto both the call stack and shadow stack, and on RET instructions, a comparison is made to ensure integrity is not compromised.

![[shadow-stack.png]]



---
links: [[915 ED TOC - Further Topics|Further Topics]] - [[themes/000 Index|Index]]