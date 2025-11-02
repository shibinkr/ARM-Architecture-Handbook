# 15. FAQs and Troubleshooting

This chapter covers **frequent questions and common issues** developers face when working with the ARM Instruction Set Architecture (ISA) and embedded systems. It provides guidance on debugging, resolving pitfalls, and understanding tricky behaviors.

---

## 15.1 Common ISA Pitfalls

| Issue                                  | Description                                                                                    | Resolution                                                                                    |
| -------------------------------------- | ---------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| Misaligned memory access               | Accessing data at addresses not aligned to its size (e.g., 32-bit load at non-4-byte boundary) | Enable alignment checks (AArch32), use LDR/STR with correct alignment, or handle via software |
| Incorrect instruction encoding         | Using wrong Thumb/A64 encoding for target CPU                                                  | Verify instruction set mode, check assembler directives, and confirm CPU architecture version |
| Condition code misuse                  | Conditional instructions executing incorrectly                                                 | Ensure correct flags are set and IT blocks are properly structured                            |
| Subtle differences between ARMv7/v8/v9 | Different behavior of certain instructions, e.g., saturation arithmetic                        | Refer to architecture reference manuals and confirm instruction support                       |

**Summary:** Always check alignment, ISA version, and instruction mode to avoid common traps.

---

## 15.2 Debugging Unaligned Accesses

Unaligned accesses can **cause exceptions or performance penalties**. Steps to debug:

1. **Identify faulting instruction:** Use exception vector or debugger to locate.
2. **Check memory alignment:** Verify data structures and stack alignment.
3. **Fix code:** Align structures using compiler attributes (e.g., `__attribute__((aligned(4)))`) or manually adjust addresses.

**Example:**

```c
uint32_t *ptr = (uint32_t *)((uint8_t*)buffer + 1); // misaligned
uint32_t val = *ptr; // may fault on strict ARMv8
```

**Solution:** Align pointer to 4-byte boundary.

---

## 15.3 Cache Coherency and Memory Ordering Issues

**Problem:** Multiple cores or DMA accessing shared memory can see stale data if caches are not coherent.

**Common causes:**

* Lack of cache maintenance instructions (clean/invalidate)
* Weak memory ordering leading to reordering of loads/stores

**Debugging steps:**

1. Use **DMB, DSB, ISB** barriers to enforce ordering.
2. Invalidate or clean caches before sharing data.
3. Verify peripheral and core access patterns.

**Example in AArch64:**

```asm
DSB SY    // Ensure previous stores complete
LDR X0, [X1]  // Load after barrier
```

**Summary:** Always ensure proper barriers and cache maintenance when sharing memory across cores or peripherals.

---

## 15.4 General Troubleshooting Tips

* Enable verbose logging in your debugger (GDB, OpenOCD)
* Test small isolated routines first (bare-metal or single-core)
* Use hardware counters or PMU to check memory access and pipeline stalls
* Validate vector and NEON operations with simple known inputs

---

### Conclusion

This chapter serves as a **practical troubleshooting guide** for ARM developers:

* Prevent common ISA mistakes
* Detect and fix unaligned memory issues
* Maintain cache coherency and memory ordering
* Ensure reliable debugging and testing practices

By following these guidelines, developers can **avoid subtle ARM pitfalls** and maintain system stability.
