# Risc-V-Learnings-
Notes and my understanding about Risc V 


#What exactly is RISC-V?

# RISC-V Architecture: Fundamentals & System Overview

A concise summary of RISC-V architecture, execution mechanics, modular extensions, and hardware accelerator integration.

---

## 1. What is RISC-V?
* **Open-Source Standard:** RISC-V is an open-standard Instruction Set Architecture (ISA), serving as a royalty-free alternative to proprietary architectures like x86 and ARM[span_0](start_span)[span_0](end_span).
* **Interface Specification:** It defines the software-hardware interface (the instruction ruleset), not a specific physical silicon chip[span_1](start_span)[span_1](end_span).
* **Universal Language:** Compilers translate high-level code into RISC-V assembly instructions, which any compliant hardware processor can execute[span_2](start_span)[span_2](end_span).

---

## 2. Core Philosophy & Design
* **Reduced Instruction Set:** RISC focuses on keeping instructions simple and fixed-length to ensure rapid execution cycles[span_3](start_span)[span_3](end_span).
* **Scalable Hardware:** While the base instruction set is straightforward, hardware implementations can range from simple microcontrollers to high-performance superscalar, out-of-order processors[span_4](start_span)[span_4](end_span).

---

## 3. Base Architectures & Modular Extensions

RISC-V relies on a mandatory base integer set combined with optional modular extensions[span_5](start_span)[span_5](end_span).

### Base Architectures
* **RV32I:** 32-bit address space and 32-bit register width[span_6](start_span)[span_6](end_span).
* **RV64I:** 64-bit address space and 64-bit register width[span_7](start_span)[span_7](end_span).

### Key Extensions
| Extension | Name | Description |
| :---: | :--- | :--- |
| **I** | Integer | Base integer instructions (mandatory for all cores)[span_8](start_span)[span_8](end_span) |
| **M** | Multiplication | Hardware multiplication and division operations[span_9](start_span)[span_9](end_span) |
| **A** | Atomic | Synchronization primitives for multi-core memory locking[span_10](start_span)[span_10](end_span) |
| **F / D** | Float / Double | Single- and double-precision IEEE 754 floating-point units[span_11](start_span)[span_11](end_span) |
| **C** | Compressed | 16-bit instruction encoding to optimize code density[span_12](start_span)[span_12](end_span) |
| **V** | Vector | Parallel array/vector processing for AI and signal workloads[span_13](start_span)[span_13](end_span) |

*Example:* **RV64G** represents `RV64IMAFDC` (Standard General-Purpose Configuration)[span_14](start_span)[span_14](end_span).

---

## 4. Hardware Execution & Memory Model

### Load/Store Architecture
Calculations are restricted to internal CPU registers[span_15](start_span)[span_15](end_span). Memory interaction occurs strictly through dedicated load (`lw`) and store (`sw`) operations[span_16](start_span)[span_16](end_span):
1. **Load:** Move data from memory address into internal register[span_17](start_span)[span_17](end_span).
2. **Compute:** Perform math/logic operations strictly between registers[span_18](start_span)[span_18](end_span).
3. **Store:** Write the modified register content back to memory[span_19](start_span)[span_19](end_span).

### Zero Register (`x0`)
* RISC-V provides 32 general-purpose integer registers (`x0` to `x31`)[span_20](start_span)[span_20](end_span).
* Register `x0` is hardwired to constant `0`[span_21](start_span)[span_21](end_span). Writes to `x0` are ignored, enabling clean implementations for register copies, zeroing out variables, and no-operation (`NOP`) signals[span_22](start_span)[span_22](end_span).

### 4-Stage Execution Cycle
[ 1. Fetch ] ──► [ 2. Decode ] ──► [ 3. Execute ] ──► [ 4. Writeback ]

1. **Fetch:** Program Counter (PC) loads the next instruction from memory[span_23](start_span)[span_23](end_span).
2. **Decode:** Control unit breaks instruction into opcode, source, and destination registers[span_24](start_span)[span_24](end_span).
3. **Execute:** ALU carries out arithmetic logic or memory address resolution[span_25](start_span)[span_25](end_span).
4. **Writeback:** Stores execution results back into target destination registers[span_26](start_span)[span_26](end_span).

---

## 5. Accelerator Offloading & AI Systems
* **Control Core:** Rather than executing heavy tensor arithmetic directly, the RISC-V processor acts as an orchestrator/controller[span_27](start_span)[span_27](end_span).
* **Task Delegation:** High-throughput computations are offloaded to specialized hardware engines such as Vector Units (RVV), GPUs, or AI/NPU accelerators[span_28](start_span)[span_28](end_span).
