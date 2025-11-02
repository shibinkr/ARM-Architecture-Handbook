# 14. Reference Tables

This chapter provides **quick-access reference tables** for ARM developers, covering instructions, flags, exception vectors, and register summaries. It is designed to be a handy reference for both AArch32 and AArch64 development.

---

## 14.1 Instruction Set Quick Reference

| Category               | Instructions                           | Description                                            |
| ---------------------- | -------------------------------------- | ------------------------------------------------------ |
| **Data Processing**    | ADD, SUB, MUL, MLA, AND, ORR, EOR, BIC | Arithmetic and logical operations                      |
| **Load/Store**         | LDR, STR, LDM, STM                     | Memory access and multiple-register operations         |
| **Branch & Control**   | B, BL, BX, BLX, IT                     | Branching, subroutine calls, and conditional execution |
| **Exception Handling** | SVC, HVC, SMCC                         | Software and hypervisor calls                          |
| **SIMD/Vector**        | VADD, VMUL, VLD, VST                   | NEON vector operations                                 |
| **Cryptography**       | AES, SHA, PMULL                        | Hardware-accelerated cryptography instructions         |

---

## 14.2 Condition Codes & Flags (AArch32)

| Condition | Mnemonic               | Meaning               |
| --------- | ---------------------- | --------------------- |
| EQ        | Equal                  | Z (Zero) flag set     |
| NE        | Not Equal              | Z flag clear          |
| CS/HS     | Carry Set/Unsigned >=  | C flag set            |
| CC/LO     | Carry Clear/Unsigned < | C flag clear          |
| MI        | Minus                  | N (Negative) flag set |
| PL        | Plus                   | N flag clear          |
| VS        | Overflow               | V (Overflow) flag set |
| VC        | No Overflow            | V flag clear          |
| HI        | Unsigned >             | C set and Z clear     |
| LS        | Unsigned <=            | C clear or Z set      |
| GE        | Signed >=              | N == V                |
| LT        | Signed <               | N != V                |
| GT        | Signed >               | Z clear and N == V    |
| LE        | Signed <=              | Z set or N != V       |
| AL        | Always                 | Always execute        |

---

## 14.3 ARM Exception Vectors

| Vector Name           | Address (AArch32) | Description                          |
| --------------------- | ----------------- | ------------------------------------ |
| Reset                 | 0x00000000        | CPU reset handler                    |
| Undefined Instruction | 0x00000004        | Handles illegal instructions         |
| SWI/SVC               | 0x00000008        | Software interrupt / supervisor call |
| Prefetch Abort        | 0x0000000C        | Instruction fetch abort              |
| Data Abort            | 0x00000010        | Data access violation                |
| IRQ                   | 0x00000018        | Standard interrupt request           |
| FIQ                   | 0x0000001C        | Fast interrupt request               |

> **Note:** AArch64 uses **ELx exception levels** with separate vector tables, e.g., EL1/EL2/EL3.

---

## 14.4 Register Summary

### 14.4.1 AArch32 Registers

| Register | Purpose                                 |
| -------- | --------------------------------------- |
| R0–R12   | General-purpose                         |
| SP (R13) | Stack pointer                           |
| LR (R14) | Link register                           |
| PC (R15) | Program counter                         |
| CPSR     | Current program status register (flags) |
| SPSR     | Saved program status register           |

### 14.4.2 AArch64 Registers

| Register | Purpose                                  |
| -------- | ---------------------------------------- |
| X0–X30   | General-purpose (X30 = LR)               |
| SP       | Stack pointer                            |
| PC       | Program counter                          |
| PSTATE   | Processor state (flags, condition codes) |
| NZCV     | Negative, Zero, Carry, Overflow flags    |
| ELR_ELx  | Exception link register                  |
| SPSR_ELx | Saved PSTATE for exception levels        |

---

### Summary

This chapter provides **quick lookup tables** for instructions, flags, exception vectors, and registers for ARM developers. It is essential for:

* Writing bare-metal assembly code.
* Debugging low-level exceptions.
* Optimizing ARM programs efficiently.
* Cross-referencing AArch32 and AArch64 register usage.

These reference tables reduce the need to constantly look up ARM manuals and provide a **fast-access guide for developers**.
