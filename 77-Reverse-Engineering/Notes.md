# 77 - Reverse Engineering

## Overview
Reverse Engineering (RE) is the process of analyzing compiled software to understand its functionality without access to source code. Used in malware analysis, vulnerability research, and CTF challenges.

---

## 1. Disassembly – IDA & Ghidra

### Key Concepts
- **Assembly Language**: Low-level language that maps directly to CPU instructions
- **Disassembly**: Converting machine code (bytes) back to assembly instructions
- **Decompilation**: Converting assembly to pseudo-C code (higher-level, easier to read)

### Common x86/x64 Assembly Instructions
| Instruction | Meaning                            |
|-------------|------------------------------------|
| MOV         | Move data between registers/memory |
| PUSH/POP    | Push to / pop from stack           |
| CALL        | Call a function                    |
| RET         | Return from function               |
| JMP         | Unconditional jump                 |
| JE/JNE      | Jump if equal / not equal          |
| CMP         | Compare two values                 |
| XOR         | Exclusive OR (often used to zero regs) |

### Ghidra Workflow
1. Open Ghidra → New Project → Import File
2. Auto-analyze the binary (accept defaults)
3. Use the **Symbol Tree** to find interesting functions
4. Use **Decompiler** window for pseudo-C view
5. Rename variables and functions to meaningful names
6. Look for: strings, crypto routines, network calls, file I/O

### IDA Free Workflow
1. Open binary in IDA → accept analysis
2. Press `F5` to decompile (Hex-Rays) any function
3. Use `Strings` window (`Shift+F12`) to find interesting strings
4. Use `Imports` tab to see all external API calls
5. Cross-reference (Xref) any suspicious API to trace call chain

---

## 2. Debugging – x64dbg / OllyDbg

### Why Debug?
Dynamic analysis in a debugger lets you:
- Step through code instruction by instruction
- Inspect register values and memory at runtime
- Bypass anti-analysis tricks
- Dump unpacked malware from memory

### x64dbg Key Features
| Feature          | Shortcut / Location       |
|------------------|---------------------------|
| Run              | F9                        |
| Step Into        | F7                        |
| Step Over        | F8                        |
| Breakpoint       | F2 (on selected line)     |
| Memory Dump      | View → Memory Map         |
| Registers        | Right panel               |

### Setting Breakpoints
```
Common breakpoints to set:
- VirtualAlloc     → Detect memory allocation (unpacking)
- CreateProcess    → Detect process spawning
- WriteProcessMemory → Detect process injection
- URLDownloadToFile → Detect download behavior
```

---

## 3. Binary Analysis

### File Format Analysis
- **ELF** (Linux): Header, sections (.text, .data, .rodata)
- **PE** (Windows): DOS header, PE header, sections
- Tools: `readelf`, `objdump`, `pefile` (Python), CFF Explorer

### Anti-Analysis Techniques (What Malware Does to Slow You Down)
| Technique          | Description                                  |
|--------------------|----------------------------------------------|
| Packing            | Compresses/encrypts the binary               |
| Obfuscation        | Renames and scrambles code                   |
| Anti-debugging     | Detects debugger via IsDebuggerPresent()     |
| Timing checks      | Detects slow sandbox execution               |
| VM detection       | Checks registry/hardware for VM artifacts    |

---

## 4. Patch Diffing

### What is Patch Diffing?
Comparing two versions of a binary (before and after a security patch) to identify what changed and reverse-engineer the vulnerability.

### Workflow
1. Download patched and unpatched versions of software
2. Open both in Ghidra or BinDiff
3. Use **BinDiff** plugin to compare functions
4. Identify changed/added/removed code
5. Understand what vulnerability was fixed

### Tools for Patch Diffing
- **BinDiff** (Google, free) – Visual binary comparison
- **Diaphora** (open-source) – IDA/Ghidra plugin for diffing
- **Ghidra Version Tracking** – Built-in diffing feature
