# 14. Troubleshooting & FAQs

Troubleshooting ARM-based systems can be challenging due to the complexity of SoCs, multiple cores, caches, and peripheral interactions. This chapter covers common issues, diagnostics, and practical solutions.

---

## 14.1 Boot Fails / No UART Output

**Symptoms:** Board does not boot, no UART messages.
**Common Causes:**

* Incorrect bootloader configuration.
* Wrong memory map or device tree settings.
* Power supply issues or hardware resets.

**Diagnostics:**

1. Check UART wiring and baud rate.
2. Verify bootloader logs (if available via JTAG/SWD).
3. Inspect device tree for correct CPU and peripheral addresses.
4. Use a logic analyzer to confirm UART TX activity.

**Example Check:**

```c
// Minimal UART init check
UART_CR1 |= (1 << UE); // Enable UART
while(!(UART_SR & (1 << TXE))); // Wait for transmit ready
UART_DR = 'H'; // Send character
```

---

## 14.2 MMU & Page Faults

**Symptoms:** Unexpected faults, memory access errors.
**Common Causes:**

* Misconfigured page tables.
* Incorrect section/block attributes.
* Accessing unmapped memory.

**Diagnostics:**

* Enable ARM fault exception handlers.
* Inspect Translation Table Base Register (TTBR) values.
* Use `dmesg` in Linux or `fault status registers` in bare-metal.

**Example Fix:**

```c
// Map 1MB section with read/write access
TTBR0[section_index] = SECTION_BASE | AP_RW | TEX_DEFAULT;
```

---

## 14.3 Cache Coherency Bugs

**Symptoms:** Data inconsistency between cores or peripherals.
**Common Causes:**

* DMA writing to memory not flushed from CPU cache.
* Shared buffers without proper memory barriers.
* Incorrectly configured cache policies.

**Diagnostics:**

* Use cache maintenance instructions (clean/invalidate).
* Enable performance counters to detect cache misses or conflicts.

**Example:**

```c
// Ensure data written by CPU is visible to DMA
SCB_CleanDCache_by_Addr((uint32_t*)buffer, size);
```

---

## 14.4 Cross-Toolchain Link Errors

**Symptoms:** Undefined symbols, ABI mismatches.
**Common Causes:**

* Mixing ARM and Thumb code incorrectly.
* Different compilers for kernel and application.
* Wrong library or startup files.

**Diagnostics:**

* Check symbol mangling using `nm` or `objdump`.
* Ensure consistent compiler flags: ` -mcpu`, ` -march`, ` -mthumb`.
* Verify ABI compatibility.

**Example:**

```bash
# Check symbols in object files
arm-none-eabi-nm main.o | grep my_function
```

---

### Summary

Troubleshooting ARM systems involves:

1. **Hardware verification:** UART, power, reset lines.
2. **Memory configuration checks:** MMU, page tables.
3. **Cache and coherency validation:** DMA, multi-core data sharing.
4. **Toolchain consistency:** Flags, ABIs, compiler versions.

Applying these systematically helps developers identify and resolve issues faster, whether in bare-metal or OS-based environments.
