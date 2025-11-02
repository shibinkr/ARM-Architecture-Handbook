# ARM Handbook Index — Instruction Set Architecture (ISA) Focus

## 1. Introduction to ARM ISA

* Overview of ARM architecture versions (ARMv7, ARMv8, ARMv9)
* AArch32 vs AArch64 execution states
* ARM execution model: Registers, modes, exception levels

## 2. ARM Register Architecture

* General-purpose registers (GPRs)
* Special-purpose registers (SP, PC, LR)
* System registers and control registers (SPSR, CPSR, ELx registers)

## 3. Data Processing Instructions

* Arithmetic operations: ADD, SUB, MUL, MLA
* Logical operations: AND, ORR, EOR, BIC
* Comparison and test instructions: CMP, TST
* Immediate vs register operands

## 4. Load/Store Instructions

* Single-register loads/stores: LDR, STR
* Multiple-register instructions: LDM, STM
* Load/store addressing modes: offset, pre/post-indexing
* Unaligned access and memory barriers

## 5. Branch and Control Instructions

* Branch instructions: B, BL, BLX, BX
* Conditional execution: IT blocks (Thumb)
* Exception handling: SVC, HVC, SMCC
* Return and subroutine call conventions

## 6. SIMD & Advanced Instructions

* NEON instructions: Vector operations, load/store
* SVE/SVE2: Scalable Vector Extension concepts
* Cryptography extensions (AES, SHA, PMULL)

## 7. Memory Model and Barriers

* Memory ordering rules: Strong vs weak ordering
* Data and instruction synchronization barriers (DSB, DMB, ISB)
* Cache maintenance instructions

## 8. Exception Levels & Privilege

* EL0–EL3: Privilege levels in ARMv8-A
* Secure vs non-secure states (TrustZone)
* Interrupt handling and vector tables

## 9. Floating Point & Advanced Math

* Floating-point instructions (VFP/NEON FP)
* Conversion, rounding, and saturation operations
* Single vs double precision

## 10. Instruction Encodings

* Thumb-1, Thumb-2, and A64 encodings
* Immediate fields, registers, and opcode mapping
* ARM assembler directives

## 11. System Programming

* CP15 / System registers access
* Performance counters and PMU
* Low-level debugging instructions (BRK, HVC, WFI/WFE)

## 12. Optimization Guidelines

* Pipeline considerations
* Branch prediction and loop unrolling
* Load/store and memory alignment

## 13. Sample Assembly Programs

* Hello World (bare-metal)
* Blink LED with GPIO
* NEON vector addition example
* Using SVE for matrix operations

## 14. Reference Tables

* Instruction set quick reference
* Condition codes and flags
* ARM exception vectors
* Register summary for AArch32 and AArch64

## 15. FAQs and Troubleshooting

* Common ISA pitfalls
* Debugging unaligned accesses
* Cache coherency and memory ordering issues

This index can serve as the backbone for a comprehensive ARM ISA handbook for developers, covering from fundamentals to advanced programming and optimization.
