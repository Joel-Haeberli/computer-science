tags: #mitigation #cfi
 
# CFI (Control Flow Integrity)

links: [[915 ED TOC - Further Topics|Further Topics]] - [[themes/000 Index|Index]]

---

## Overview

**CFI: Control Flow Integrity**
Also CFG: Control Flow Guard
Or CFE: Control Flow Enforcement

Control Flow Integrity (CFI) is a security technique designed to prevent unauthorized modifications to the intended control flow of a computer program. This technique helps to protect against common security threats like buffer overflows and return-oriented programming (ROP) attacks, which can manipulate the flow to execute malicious code.

CFI works by placing checks throughout the program to ensure that the execution flow at runtime follows only the legitimate paths predicted by the program’s control flow graph, which is typically computed at compile time. Any deviation from these predefined paths triggers a response, often terminating the program, to prevent potential exploitation. By validating the target of each control flow transfer, such as [indirect function calls](https://softwareengineering.stackexchange.com/questions/401110/difference-between-direct-and-indirect-function-calls) and returns, CFI helps in maintaining the integrity of the software’s execution trajectory, thus bolstering its resistance against attacks that attempt to hijack the program’s control flow.

For more specific information: https://clang.llvm.org/docs/ControlFlowIntegrity.html

## Forward Edge Protection

![[forward-edge.png]]

The "forward edge" refers to indirect calls and jumps in a program, where the target of the call or jump is determined at runtime. Forward edge protection ensures that these dynamic dispatches lead only to legitimate function targets, thus preventing an attacker from diverting the control flow to malicious code.

When a function call is made through a function pointer, the control is first passed to a corresponding stub. This stub then safely redirects to the actual function implementation. This indirection via stubs helps to ensure that even if an attacker can overwrite a function pointer, they can only divert the execution to a pre-approved list of stubs, not directly to arbitrary or malicious code.

![[forward-edge-pseudo.png]]

## Backwards Edge Protection

Backward edge protection in Clang is implemented to protect the return addresses on the program stack during function returns. This mechanism prevents attacks that attempt to corrupt the stack to hijack the program’s control flow.

![[backward-edge.png]]

**Unsafe_stack:** Used for storing local variables and function parameters that do not require enhanced security measures. It is more susceptible to overflow attacks

**Safe_stack:** Designed to securely store return addresses separately from other local variables, the safe_stack minimizes the risk of overwriting return addresses through buffer overflows in the unsafe_stack.

![[backward-edge-2.png]]
![[backward-edge-pseudo.png]]

## Granularity

The granularity of CFI enforcement can be influenced by the specific compiler flags set at compile time. These flags determine how detailed and stringent the CFI checks will be. Different compilers offer various CFI-related flags that can control the level of protection, effectively adjusting the granularity between fine-grained and coarse-grained CFI.

- **Fine-Grained CFI Flags**:
    - Flags that enable fine-grained CFI provide more precise control over indirect calls and returns, ensuring that only explicitly defined paths in the control flow graph are followed. These might include flags for protecting specific types of function pointers or virtual calls in C++.
    
- **Coarse-Grained CFI Flags**:
    - Alternatively, some flags may implement a broader, more general form of CFI, where the checks are less detailed. This might involve ensuring that any indirect call targets a legitimate function entry point, without verifying the specific target function against a precise expected set.


## Attacks

- **Infoleaks on Probabilistic CFI**:
    
    - Certain implementations of CFI are probabilistic rather than deterministic, meaning they rely on patterns or probabilities to enforce control flows. Infoleak attacks exploit vulnerabilities where sensitive information (like memory addresses) is unintentionally disclosed. This leaked information can be used to predict or infer the patterns used in probabilistic CFI, allowing attackers to craft inputs that bypass the CFI checks.
    
- **Coarse-Grained CFI Limitations**:
    - Coarse-grained CFI, which checks control flows at a broader level, might only ensure that control transfers (like function calls) land within a permissible set of functions that share similar signatures (e.g., same return type and arguments). This allows more flexibility for attackers to divert execution to any function within this set, even if it’s not the intended specific function. This reduces the security effectiveness because it only prevents jumps to entirely inappropriate or random functions, not unauthorized but signature-matching ones.

- **Data-Only Attacks**:
    - These attacks manipulate the program’s execution flow without changing the code itself; instead, they alter the data used by the program to influence its behavior. Since traditional CFI mechanisms primarily focus on ensuring that the flow between code points (such as functions) is legitimate, they might not protect against attacks that solely modify data values or states to achieve malicious outcomes.

---
links: [[915 ED TOC - Further Topics|Further Topics]] - [[themes/000 Index|Index]]