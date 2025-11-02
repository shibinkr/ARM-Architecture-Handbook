# 1. Introduction to ARM ISA

The ARM Instruction Set Architecture (ISA) is a fundamental component of ARM processors, defining the set of instructions and execution behaviors for software development. It is designed for high performance, low power consumption, and scalability across embedded, mobile, and server-class devices.

## 1.1 Overview of ARM Architecture Versions

* **ARMv7**: 32-bit architecture widely used in Cortex-A/R/M series. Supports Thumb, Thumb-2, and NEON SIMD instructions.
* **ARMv8**: Introduces AArch64 for 64-bit execution while maintaining backward compatibility with AArch32. Adds cryptography and virtualization extensions.
* **ARMv9**: Builds on ARMv8-A with enhanced security (Confidential Compute), AI/ML extensions, and improved vector processing (SVE2).

## 1.2 AArch32 vs AArch64 Execution States

* **AArch32**: Legacy 32-bit mode. Uses 32-bit general-purpose registers (R0–R15) and supports existing 32-bit instructions.
* **AArch64**: Modern 64-bit mode. Uses 31 general-purpose 64-bit registers (X0–X30), SP (Stack Pointer), and PC. Enables larger address space and improved performance for modern workloads.

| Feature           | AArch32           | AArch64 |
| ----------------- | ----------------- | ------- |
| Register Width    | 32-bit            | 64-bit  |
| General Registers | R0–R15            | X0–X30  |
| Stack Pointer     | SP (R13)          | SP      |
| Instruction Set   | ARM/Thumb/Thumb-2 | A64     |
| Address Space     | 4 GB              | 16 EB   |

## 1.3 ARM Execution Model

The ARM processor executes instructions through a structured execution model:

* **Registers**: CPU cores provide general-purpose, special-purpose, and system registers.
* **Processor Modes**: Privilege levels or exception levels (EL0–EL3 in ARMv8) determine accessible instructions and memory.
* **Exception Levels**:

  * **EL0**: User applications (least privileged)
  * **EL1**: Operating system kernel
  * **EL2**: Hypervisor for virtualization
  * **EL3**: Secure monitor (highest privilege, TrustZone support)

This model allows secure separation between user applications, OS, hypervisors, and trusted firmware.

### Summary

Chapter 1 provides a foundational understanding of ARM ISA, highlighting architecture versions, 32-bit vs 64-bit execution states, and the processor execution model including registers, modes, and privilege levels. This knowledge is essential for developers targeting ARM-based systems.
