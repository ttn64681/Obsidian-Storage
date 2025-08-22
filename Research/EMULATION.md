1. Create simple code in C
2. Cross compile to different computer architecture than current: 
	1. Mac Intel (x64) -> ARM Binary x86
	2. Windows (x64) -> ARM Binary x86
3. Run on Emulator (QEMU - system emulator)

- _ARM64_ - referred as AArch64 or ARM Architecture for 64 bit CPUs. AMD64 - is the x86 architecture

How to do this:
- Need different Toolchain (includes: compiler, assembler, linker, standard libs, and debugger)
	- Toolchain is responsible w/ creating specific ISA version-specific binary code
	- We need a different Toolchain aside from native Toolchain to create ARM64 binary