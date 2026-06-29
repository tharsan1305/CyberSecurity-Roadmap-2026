# 77 - Reverse Engineering - Labs

## Lab 1: Reverse a Simple CrackMe

### What is a CrackMe?
A CrackMe is a small program designed for RE practice — usually requires finding a serial key or password.

### Where to Get CrackMes
- [crackmes.one](https://crackmes.one/) – Free, rated by difficulty
- [reversing.kr](http://reversing.kr/) – Classic RE challenges
- CTF challenges (picoCTF, pwn.college)

### Steps
1. Download a beginner-level CrackMe from crackmes.one
2. Open in Ghidra → Analyze
3. Find the main function (look in Symbol Tree or search "main")
4. Use the Decompiler to read pseudo-C code
5. Look for string comparison logic (strcmp, strncmp)
6. Find the hardcoded password/serial
7. Verify by running the program with the found answer

---

## Lab 2: Debugging with x64dbg

### Objective
Use x64dbg to trace execution and find a hidden password.

### Steps
1. Download x64dbg from [x64dbg.com](https://x64dbg.com)
2. Load a CrackMe binary into x64dbg
3. Search for strings: Right-click → Search → All Modules → String References
4. Find string like "Wrong password" or "Correct!"
5. Set breakpoint on the comparison instruction before "Wrong password"
6. Run the program (F9), enter a test password, let it hit the breakpoint
7. Inspect register values at the comparison point — the correct password is often in a register

---

## Lab 3: Unpack a Packed Binary

### Objective
Manually unpack a UPX-packed binary.

### Steps
1. Create a test binary and pack it: `upx -9 program.exe`
2. Analyze in PEStudio — notice high entropy, small number of imports
3. Load in x64dbg
4. Set breakpoint on `VirtualAlloc` (common in unpackers)
5. Run until OEP (Original Entry Point) is reached
6. Dump the unpacked binary from memory using x64dbg's Scylla plugin
7. Analyze the dumped binary in Ghidra — now fully readable

---

## Practice Challenges
- [ ] Solve 3 beginner CrackMes from crackmes.one
- [ ] Complete picoCTF Reverse Engineering challenges
- [ ] Use Ghidra to decompile a Windows system DLL and document 3 functions
- [ ] Try pwn.college Reverse Engineering module (free, browser-based)
- [ ] Research and document 5 anti-debugging techniques
