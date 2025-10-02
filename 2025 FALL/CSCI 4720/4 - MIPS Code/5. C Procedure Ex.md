# C Sort Example - Bubble Sort
## Swap
- Illustrates bubble sort in C
- Swap procedure (leaf)
```
void swap(int v[], int k)
{
	int temp;
	temp = v[k];
	v[k] = v[k+1];
	v[k+1] = temp;
}
```
- **v in $a0, k in \$a1, temp in $t0**

## Function calling Swap
- Non-leaf (calls swap)
```
void sort (int v[], int n)
{
int i, j;
for (i = 0; i < n; i += 1) {
	for (j = i-1; j > 0 && v[j] > v[j+1]; j-=1) {
		swap(v,j)
	}
}
}
```
- v in $a0, n in \$a1, i in \$s0, j in \$s1

# MIPS Code for Bubble Sort
## Swap
- \$a0 + $a1\*4 (4 bytes)
```

```
- calc address of k
	- left shift 2 bits to get k\*4
	- then add a0 to it

- load vk + 1
	- t2 = v[k+1]
- store t2 to v[k]
- store t0 to v[k+1] 
- jr $ra return to calling routine

## Non-leaf Procedure calling Swap
```

```
- move params
	- save a0 into s2
	- save a1 into s3
	- we do this since we need a0 and a1 to pass as args to swap function
		- if we don't move, then it'll be overridden
- outer loops: slt $t0, \$s0, $s3
	- if s0 < s3 keep going
		- addi $s1
	- if so ≥ s3, t0 = 0

### Why we prefer s0 s1 s3
**saved register vs temp register**
- yes we can use t0, t1, t3
- you'd have to set t0 t1 and t3 by yourself before the call the swap
- callee saves the register
	- s0 s1 s3

## Full Procedure
sort:
- addi $sp, \$sp, -20
	- make room on stack for 5 registers
- sw ra, 16{sp}
	- save on stack
- sw s3, 12{sp}
- sw s2, 8{sp}
- sw s1, 4{sp}
- sw 0, 0{sp}
... # procedure body

exit1:
- lw s0, 0(sp)
	- restore s0 from stack
- lw s0, 4(sp)
	- restore s1
- lw s0, 8(sp)
- lw s0, 12(sp)
- lw s0, 16(sp)


# Effort of Compiler Optimization
- **Compiled w/ gcc for Pentium 4 under Linux**

- Relative Performance

- Instruction Count
	- more instructions mean slightly better performance
- Clock Cycles
	- 
- CPI: 01, 02,0 3
	- slower typically

- A java interpreter has relative performance of .12 while java JIT compiler has 3 times more .36

## Lessons Learned
- Instruction count and CPI are not good performance indicators in isolation
- Compiler optimizations are sensitive to algorithm
- Java/JIT compiled code is significantly faster than JCM interpreted
	- JIT can optimize runtime compilation, but has some costs
	- Comparable to optimized C in some cases
- Nothing can fix a dumb algorithm!
	- if you can develop efficient algorithm, then performance significantly improves
- Thats why in Machine Learning there are diff algorithms

## Arrays vs Pointers
- Array indexing involves
	- Multiplying index by element size
	- Adding to array base address
- Pointers correspond directly to memory addresses
	- Can avoid indexing complexity

## Example: Clearing and Array
## clear an array w/ pointer is more efficient
### no pointers
```
clear1(int array[], int size) {
	int il
	for (i=0; i<size; i+=1)
		array[i] = 0
}
```

### with pointers
```
clear2(int *array, int size) {
	int *p;
	for ()&array[o]; p < &array[size];
		p = p+1)
		*p = 0;
}
```
- MIPS:
- left shift a1 by 2 # t1 = size x 4
- add a0 t1 = t2 # t2 = &array[size]

## Example: Clearing and Array

## Comparison of Array vs. Pointer
- The array must have the "multiply" and add inside the loop b/c i is incremented...

# ARM & MIPS Similarities
- ARM: the most popular embedded core
- Similar basic set of instructions to MIPS

|                       | ARM         | MIPS        |
| --------------------- | ----------- | ----------- |
| Date announced        | 1985        | 1985        |
| instruction size      | 32 bit      | 32 bits     |
| addr space            | 32-bit flat | 32-bit flat |
| data alignment        | aligned     | aligned     |
| data addressing modes | 9           | 3           |
| registers             |             |             |
| input/output          |             |             |
- **Both RISC instruction sets**
## The Intel x86 ISA
- Evolution w/ backwards compatibility
	- 8080: 8-bit microprocessor
		- Accumulator, plus 3 index-register pairs
	- 8086: 16-bit extension to 8080
		- Complex instruction set (CISC)
	- ...

- Further evolution...
	- i486: pipelined, on-chip caches and FPU
	- Pentium: superscalar, 64-bit datapath
	- Pentium Pro, Pentium II
		- New microarchitecture
	- Pentium III
		- Added SSE (Streaming SIMD Extensions) and associated registers
	- Pentium 4 (2001)
		- new microarchitecture
		- Added SSE2 instructions

## Basic x86 Registers

## x86 Instruction Encoding
- Variable length encoding

## Fallacies
- Powerful instruction => higher performance
	- Fewer instructions required
	- But complex instructions are hard to implement
		- May slow down all instructions, including simple ones
	- Compilers are good at making fast code from simple instructions
- Use assembly code for high performance
	- But modern compilers are better at dealing w/ modern prcoessors
	- Can reduce portability of code
		- Assembly MIPS cannot run x86 CPU or ARMS CPU
	- More lines of code => more errors and less productivity
- JIT can do many optimizations
	- can almost reach same performance level as highly-tuned assembly code
	- so we write high-level and write assembly for...

- Backward compatibility instruction set doesn't change
	- But they do accrete more instructions
CHART: x86 instruction set - number of instructions increase greatly from 1078-2008


# Concluding Remarks
- Design principles
	1. Simplicity favors regularity
	2. Smaller is faster
	3. Make the common case fast
	4. Good design demands  compromises
2. Layers of software/hardware
	1. Compiler, assembler, hardware
3. MIPS: typical of RISC ISAs
	1. c.f. x86

## The 20 MiniMIPS instructions covered so far
Copy
Arithmetic
Logic
Memory access
Control transfer