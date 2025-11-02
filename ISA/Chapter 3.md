# 3. Data Processing Instructions

Data processing instructions are the core of the ARM ISA, enabling arithmetic, logical, and comparison operations on registers. Understanding these instructions is essential for both assembly programming and low-level optimization.

## 3.1 Arithmetic Operations

Arithmetic instructions perform addition, subtraction, multiplication, and combined operations:

| Instruction | Description                                 | Example                         |
| ----------- | ------------------------------------------- | ------------------------------- |
| **ADD**     | Adds two operands and stores the result     | `ADD R0, R1, R2` ; R0 = R1 + R2 |
| **SUB**     | Subtracts the second operand from the first | `SUB R0, R1, R2` ; R0 = R1 - R2 |
| **MUL**     | Multiplies two registers                    | `MUL R0, R1, R2` ; R0 = R1 * R2 |
| **MLA**     | Multiply and accumulate: R0 = R1 * R2 + R3  | `MLA R0, R1, R2, R3`            |

**Notes:**

* Arithmetic instructions can optionally update the condition flags (N, Z, C, V) using the `S` suffix, e.g., `ADDS`.

## 3.2 Logical Operations

Logical instructions manipulate individual bits and perform bitwise operations:

| Instruction | Description     | Example                            |
| ----------- | --------------- | ---------------------------------- |
| **AND**     | Bitwise AND     | `AND R0, R1, R2`                   |
| **ORR**     | Bitwise OR      | `ORR R0, R1, R2`                   |
| **EOR**     | Bitwise XOR     | `EOR R0, R1, R2`                   |
| **BIC**     | Bitwise AND NOT | `BIC R0, R1, R2` ; R0 = R1 & (~R2) |

**Use Cases:**

* Masking bits, clearing flags, combining multiple values, or testing bits before branching.

## 3.3 Comparison and Test Instructions

Comparison and test instructions do not write results to a destination register but update condition flags:

| Instruction | Description                                                      | Example         |
| ----------- | ---------------------------------------------------------------- | --------------- |
| **CMP**     | Compares two values (subtracts second from first, updates flags) | `CMP R0, #10`   |
| **TST**     | Performs bitwise AND, updates flags without storing result       | `TST R0, #0xFF` |

**Summary of Flags Updated:**

* **N**: Negative
* **Z**: Zero
* **C**: Carry
* **V**: Overflow

## 3.4 Immediate vs Register Operands

* **Immediate Operand**: Constant value encoded directly in the instruction.
  Example: `ADD R0, R1, #5` ; R0 = R1 + 5
* **Register Operand**: Value held in a register.
  Example: `ADD R0, R1, R2` ; R0 = R1 + R2

**Notes:**

* Many instructions allow shifting of register operands (LSL, LSR, ASR, ROR) before computation.
* Immediate operands may have restrictions (like rotation) in ARMv7.

### Summary

ARM’s data processing instructions provide arithmetic, logical, and comparison capabilities essential for algorithm implementation, bit manipulation, and decision-making. Familiarity with immediate and register operands, along with flag effects, is critical for efficient ARM assembly programming.
