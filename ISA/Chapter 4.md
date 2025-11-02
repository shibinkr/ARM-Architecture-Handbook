# 4. Load/Store Instructions

Load and store instructions are used to transfer data between registers and memory. In ARM, memory access is separated from arithmetic/logical operations, following the load/store architecture.

## 4.1 Single-Register Loads/Stores

Single-register instructions move one word or byte between memory and a register.

| Instruction | Description                                   | Example                       |
| ----------- | --------------------------------------------- | ----------------------------- |
| **LDR**     | Load a word/byte from memory into a register  | `LDR R0, [R1]` ; R0 = Mem[R1] |
| **STR**     | Store a word/byte from a register into memory | `STR R0, [R1]` ; Mem[R1] = R0 |

**Notes:**

* LDR and STR support immediate and register offsets.
* Byte variants: `LDRB` and `STRB`.

## 4.2 Multiple-Register Instructions

ARM supports loading or storing multiple registers in a single instruction.

| Instruction | Description                         | Example                                                    |
| ----------- | ----------------------------------- | ---------------------------------------------------------- |
| **LDM**     | Load multiple registers from memory | `LDM R0!, {R1-R3}` ; load R1-R3 starting at R0, update R0  |
| **STM**     | Store multiple registers to memory  | `STM R0!, {R1-R3}` ; store R1-R3 starting at R0, update R0 |

**Notes:**

* Useful for context save/restore in function calls or interrupt handling.
* Address update modes: increment after (IA), decrement before (DB), etc.

## 4.3 Load/Store Addressing Modes

ARM provides flexible memory addressing modes:

| Mode             | Description                         | Example                                           |
| ---------------- | ----------------------------------- | ------------------------------------------------- |
| **Offset**       | Base + immediate or register offset | `LDR R0, [R1, #4]` ; R0 = Mem[R1 + 4]             |
| **Pre-indexed**  | Base modified before access         | `LDR R0, [R1, #4]!` ; R1 = R1+4, R0 = Mem[R1]     |
| **Post-indexed** | Base modified after access          | `LDR R0, [R1], #4` ; R0 = Mem[R1], then R1 = R1+4 |

**Notes:**

* Pre/post-indexing is useful for stack operations and pointer arithmetic.

## 4.4 Unaligned Access and Memory Barriers

* ARM supports unaligned memory access in later architectures, but older cores require aligned accesses.
* Memory barriers (`DMB`, `DSB`, `ISB`) ensure ordering of memory operations across cores or peripherals.

**Summary:**

* Single and multiple register instructions allow efficient memory transfers.
* Flexible addressing modes support pointer arithmetic and structured data access.
* Awareness of alignment and memory barriers is crucial for performance and correctness in multi-core systems.
