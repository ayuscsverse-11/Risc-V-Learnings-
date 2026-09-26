# Risc-V Learnings - Quick Notes


My simple study notes on RISC-V architecture, how it works, and its core concepts.

---

## What is RISC-V?
* **Open Source Standard:** RISC-V is a free instruction set architecture (ISA). It's not a physical CPU chip, but a set of rules for processors.
* **Alternative to Proprietary ISAs:** It acts as an open-source alternative to ARM and x86.
* **Role of ISA:** It serves as a bridge/language between software code and hardware circuits.

---

## Core Features & Extensions

RISC-V starts with a simple base system and lets you add features (extensions) as needed:

* **RV32I / RV64I:** Base integer instruction sets (32-bit and 64-bit).
* **M Extension:** Adds hardware multiplication and division.
* **A Extension:** Atomic operations for multi-threaded code.
* **F / D Extensions:** Single and double precision floating-point math.
* **C Extension:** Compressed instructions to save memory space.
* **V Extension:** Vector processing for AI and signal processing workloads.

---

## How Code Executes (4 Pipeline Stages)

Every instruction goes through 4 basic steps inside the processor:

1. **Fetch:** Get the instruction from memory.
2. **Decode:** Figure out what operation needs to be done.
3. **Execute:** Run the calculation on the ALU.
4. **Writeback:** Save the final result back into a register.

---

## Important Rules to Remember

* **Load/Store Architecture:** You cannot do math directly inside RAM. Data must first be loaded into registers (`lw`), processed, and then saved back to memory (`sw`).
* **The Special `x0` Register:** Register `x0` is hardwired to 0. It is useful for copying values and creating zeroed registers easily.
* **AI Offloading:** RISC-V core works as a controller that passes heavy mathematical operations to GPUs or AI vector units.
