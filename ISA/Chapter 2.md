# 2. ARM Register Architecture

ARM processors provide a rich set of registers that facilitate efficient computation, control, and system management. Understanding these registers is crucial for low-level programming, exception handling, and context switching.

## 2.1 General-Purpose Registers (GPRs)

* **AArch32**: Registers R0–R12 are general-purpose for integer operations, R13 (SP), R14 (LR), and R15 (PC) have special roles.
* **AArch64**: Registers X0–X30 are general-purpose; XZR/WZR acts as zero register.
* **Usage**: Parameters, local variables, intermediate computation, and temporary storage.

| Execution State | Registers | Special Notes   |
| --------------- | --------- | --------------- |
| AArch32         | R0–R12    | General-purpose |
|                 | R13 (SP)  | Stack pointer   |
|                 | R14 (LR)  | Link register   |
|                 | R15 (PC)  | Program counter |
| AArch64         | X0–X30    | General-purpose |
|                 | SP        | Stack pointer   |
|                 | XZR/WZR   | Zero register   |

## 2.2 Special-Purpose Registers

* **SP (Stack Pointer)**: Points to the current top of the stack; used for function calls, local variables, and exception handling.
* **PC (Program Counter)**: Holds the address of the next instruction to execute.
* **LR (Link Register)**: Stores the return address during subroutine calls, eliminating the need to push to the stack.

## 2.3 System and Control Registers

* **CPSR (Current Program Status Register, AArch32)**: Holds condition flags, interrupt masks, and processor mode.
* **SPSR (Saved Program Status Register, AArch32)**: Saves CPSR during exceptions for later restoration.
* **ELx System Registers (AArch64)**: Include general-purpose system control, exception masks, interrupt controls, and security state indicators (EL0–EL3).

| Register | Purpose                                                               |
| -------- | --------------------------------------------------------------------- |
| CPSR     | Current status flags and mode (AArch32)                               |
| SPSR     | Saved CPSR during exceptions (AArch32)                                |
| ELR_ELx  | Stores return address after exceptions (AArch64)                      |
| SP_ELx   | Stack pointer for each exception level (AArch64)                      |
| PSTATE   | Holds condition flags, interrupt masks, and execution state (AArch64) |

### Summary

Chapter 2 introduces ARM’s register architecture, covering general-purpose, special-purpose, and system/control registers. Mastery of these registers is essential for assembly programming, exception handling, and system-level development on ARM platforms.
