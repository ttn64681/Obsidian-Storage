- [x] August 27, 11:59 - CSCI 4720 HW1
- [x] Sept 3, 11:59 - CSCI 4720 M1 Quiz (w/ Cheatsheet)

# Outline:
```table-of-contents
```
# 1. HW 1
- if number rounding is followed by 5,6,7,8,9, round up.
- 2e+09 = 2 x (10^9) = 2,000,000,000
- 4e-03 = 4 x (10^-3) = 0.004

## 1. Select all true:
- [ ] Computer buses are for connecting computers
	- wrong, they are used for connecting different parts of a computer
- [x] Address Bus: carry CPU generated address out to memory & I/O devices
- [x] Control bus carries signals from CPU to external devices and vice versa. e.g. READ WRITE
- [x] Number of wires in databus depends on word size that micro-processor (CPU) operates with
- [x] Databus signals are bi-directional

## 2. Match:
1. Address Bus
2. Data Bus
3. Control Bus
a. Is bi-directional; signals travel out of and into the micro-processor.
b. Carries the CPU generated address out to memory & I/O devices.
c. External devices and vice versa. e.g. READ and WRITE signals.

Answer: 1b, 2a. 3c

## 3. Match:
1. RAM - big
2. Cache -
a. Closer to the processor core.
b. Faster!
c. Cheaper
d. Way larger
e. Reduces the memory access latency b/c of its size

Answer: 2a, 2b, 1c, 1d, 2e
## 4. Match:
1. Microprocessor
2. Microcontroller
a. Designed to govern a specific operation in an embedded system
b. (Image of intel core i7 chip)
c. Created by packaging CPU, Memory and I/O parts and buses in a single VLSI chip.
d. CPU unit packaged in a single chip

Answer: 2a, 1b, 2c, 1a

## 5. Match
1. Primary storage
2. Secondary storage
a. RAM
b. Cheaper and slower
c. Hard disk drive (HDD)
d. Registers
e. Nonvolatile
f. Cache memory

Answers: 1a, 2b, 2c, 1d, 2e, 1f

## 6. Calculate: CPU_time, fastest?, IC, clock_rate
Consider three different processors P1, P2, and P3 executing the same instruction set.
P1 has a 3.00 GHz clock rate and a CPI of 1.5.
P2 has a 2.50 GHz clock rate and a CPI of 1.0.
P3 has a 4.00 GHz clock rate and has a CPI of 2.2.
1. Find execution time for each processor {The first three answer boxes in order of processor number, only write the rounded (up) time in seconds in format of d.d; e.g. 0.7} for a program with 2.00e+9 (2e+09 is a notation for 2x(10^9) = 2,000,000,000) instructions. Which one is the fastest {The fourth answer box just the number of fastest processor, 1, 2, or 3}?
2. If the processors each execute a program in 10 seconds, find the number of instructions that they are running {The answer boxes 5, 6, and 7 for processor 1 , 2, and 3 respectively, in the format of d.dde+dd; e.g. 1.79e+10}? We are trying to reduce the execution time by 20% but this leads to an increase of 10% in the CPI. What clock rate in GHz should we have to get for this time reduction for each processor {The last three answer boxes in order of processor numbers in format of d.d; e.g. 3.1}?

**Answers:**
Execution time for processors 1-3 -
1. 1.0
2. 0.8
3. 1.1
Fastest processor? -
4. 2
IC for each processor at 10s CPU time -
5. 2.00e+10
6. 2.50e+10
7. 1.82e+10
20% reduced CPU time, 10% increase CPI, what is Clock rate?
8. 4.1
9. 3.4
10. 5.5
## 7. Calculate: Capacitive loads
The Pentium 4 Prescott processor, released in 2004, had a
clock rate of 3.60 GHz and voltage of 1.25 V. Assume that, on average, it consumed 90 W of power.
The Core i5 Ivy Bridge, released in 2012, had a
clock rate of 3.40 GHz and voltage of 0.90 V. Assume that, on average, it consumed 40 W of power.

1. For each processor find the capacitive loads
   {The first answer box is for Pentium 4 and second answer box is for Core i5; values should be rounded in the format of d.dde-dd; e.g. 2.46e-09 - - do **NOT** write the unit ahead of your answer}.

Answers:
1. 1.60e-08
2. 1.45e-08

## 8. Calculate: CPI for Clock Cycle time, SPEC ratio
The results of the SPEC CPU2006 bzip2 benchmark running on an AMD Barcelona has an instruction count of 2.389e+12, an execution time of 750 s, and a reference time of 9650 s.

1. Find the CPI if the clock cycle time is 0.333 ns {The first answer box with round value in format of d.dd; e.g. 0.86}.
2. Find the SPEC ratio {The second answer box with round value format of d.dd; e.g. 16.56}.

Answers: 0.94, 12.87

## 9. Calculate: avg CPI for Clock cycle time, ratio of Freq rate, CPU ratio old-new
Assume that for a program, compiler A results in a dynamic instruction count of 1.00e+9 and has an execution time of 1.1 s, while compiler B results in a dynamic instruction count of 1.20e+9 and an execution time of 1.5 s.

1. Find the average CPI for each program given that the processor has a clock cycle time of 1 ns {The first two answer box for compiler A and B, respectively. The answers should be rounded up in format of d.dd; e.g. 2.30}.
  
2. Assume the compiled programs run on two different processors. If the execution times on the two processors are the same, what is the ratio of frequency rate  for processor running compiler B's code to that of processor running compiler A's code? {The third answer box, rounded value in format of d.dd; e.g. 1.45}?

3. A new compiler is developed that uses only 6.00e+8 instructions and has an average CPI of 1.1.

4. What is the ratio of CPU time of compiler A to the CPU time of the new compiler? {Write your answer in the forth answer box in the format d.dd e.g 2.10}

5. What is the ratio of CPU time of compiler B to the CPU time of the new compiler? {Write your answer in the fifth answer box in the format d.dd e.g 0.70}

**Answers:**
1. 1.10
2. 1.25
3. 1.37
4. 1.67
5. 2.27

## 10. Calculate:
Assume a program requires the
execution of 50e+6 FP instructions, 110e+6 INT instructions, 80e+6 L/S instructions, and 16e+6 branch instructions.
The CPI for each type of instruction is 1, 1, 4, and 2, respectively.
Assume that the processor has a 2.00 GHz clock rate.

1. Find the execution time {The first answer box in the format of d.ddd; e.g. 5.857 - do NOT put the unit(s or seconds) ahead of your answer }?

2. What is the new CPI value of FP instructions if we want the program to run two times faster? {The second answer box, if impossible write "IMP", if possible write new CPI value in format of d.dd; e.g. 0.70}?

3. What is the new CPI value of L/S instructions if we want the program to run two times faster? {The third answer box, if impossible write "IMP", if possible write new CPI value in format of d.dd; e.g. 0.50} ?
  
4. What is the new(improved) execution time of CPU if the CPI of INT and FP instructions is reduced by 40% and the CPI of L/S and Branch is reduced by 30 {The fourth answer box in format of rounded d.ddd; e.g. 0.350 - do NOT put the unit(s or seconds) ahead of your answer}?

Answers:
1. 0.256
2. IMP
3. 0.80
4. 0.171

<hr>

# 2. MQ1

## 1. What is used in the Embedded System?
- Microcontroller
- Microprocessor

Answer: Microcontroller

## 2. Calculate:
The design team for a simple, single-issue processor is choosing between a pipelined or non-pipelined implementation.  Here are some design parameters for the two possibilities:  

| Parameter:                      | Pipelined Version: | Non Pipelined Version: |
| ------------------------------- | ------------------ | ---------------------- |
| Clock Rate ->                   | 3 GHz              | 2 GHz                  |
| CPI for ALU instructions ->     | 1.5                | 1                      |
| CPI for Control instructions -> | 1                  | 3                      |
| CPI for Memory instructions ->  | 2                  | 2                      |

1. For a program with 20% ALU instructions, 10% control instructions and 70% memory instructions, which design will be faster? {Write either "Pipelined" or "Non Pipelined " in answer box 1}
	Give a quantitative CPI average for each case. {The answer box 2 is for CPI of Pipelined version and answer box 3 is for CPI of Non Pipelined version in format of d.d; e.g. 2.1}?

2. Find execution time in millisecond (ms) for each version when running a program with 1.00e+6(1 X 106) instructions. {The answer box 4 is for execution time of Pipelined version and answer box 5 is for execution time of Non Pipelined version  in the format of d.dd; e.g 5.45}

Answers:
- Pipelined
- 1.8
- 1.9
- 0.60
- 0.95

## 3. Calculate: What is ALU?
- Answer:
	- The ALU is a unit inside the CPI that handles any logical/arithmetic operations within an instruction that the CPU is supposed to execute
	- Let's say the PC, which is a special register that holds instructions inside a CPU, loads instructions that contains an arithmetic operation (x + y). The ALU will then carry out the binary/bit-wise operations to perform x+y, and outputs a bitwise/binary result that gets sent via data signal to some output.

## 4. Calculate: What is the advantage of Secondary Storage?
- Answer:
	- The advantage of secondary storage is that it can hold more storage than primary registers, and that it is usually cheaper than primary registers, which are smaller and more expensive.

## 5. Calculate: Avg Capacitive load (C), Percent of Power saving if C reduced 20% and freq reduced 15%
A processor has a clock rate of 2.0 GHz and voltage of 1.0 V. Assume that, on average, it consumes 70 W of power.

1. Find the average capacitive load?{Write in answer box 1 below in the format of d.dde+dd; e.g. 1.79e+10 - do **NOT** write the unit ahead of your answer}?
2. If we decrease load 20%, and reduce the frequency 15% what would be the percentage of power saving?{Write in answer box 2 below in format of rounded dd.dd; e.g. 78.59 - do **NOT** put the percent sign at the end of your answer}?

Answers:
1. 3.50e-80
2. **.32 power saved from old to new** or .68 power saved comparing new to old

## 6. Calculate: IC for 2 computers have eq CPU time
Computer A has an overall CPI of 1.3 and can  run at a clock rate of 2 GHz. Computer B has a CPI of 2.5 and can  run at a clock rate of 3 GHz. We have a particular program we wish to run. When compiled for computer A, this program has exactly  1 x 10 9 instructions. How many instructions would the program need to have when compiled for Computer B, in order for the two computers to have exactly the same execution time for this program?{Write in answer box below in the format of d.dde+dd; e.g. 1.79e+10}?

Answer: **7.80e+8**

## 7. In a 32-bit Processor, which type of bus consists of 32 wires?
Answer: Data Bus

























## … Some scratch work (unfinished and sloppy don't mind too much)

1. 3 Processors w/ same instruction set

- Execution time or CPU time = (Instructions * CPI) / clock_rate
- always convert to Hz

p1 - 3 GHZ rate, CPI 1.5
p2 - 2.5 GHz rate, CPI

2.00e+9 insturctions

CPU execution time:
1. (2 x 10^9) x 1.5 / (3 x 10^9) = 1
2. (2 x 10^9) x 1.5 / (2.5 x 10^9) = .8
3. (2 x 10^9) x 1.5 / (4.0 x 10^9) = 1.1

- Execution time or CPU time = Instructions * CPI / clock_rate

10 seconds CPU time constant - find IC
IC = CPUtime (10s) * rate /  CPI

1. IC = 10s * (3 x 10^9 Hz) = 2e10
2. IC = 10 s * (2.50 x 10^9 Hz) = 2.5e10
3. IC = 10 s * (4.00 x 10^9 Hz) = 1.82e10

new time = 10s x .2 (20 % decrease) = 8s
1  new cpi = 1.5 x 1.1 = 1.65
	  new rate = Instructions * new cpi / new time
	  new rate = 2e10 x (1.65) /  8 = 4.125 x 10^9 Hz = 4.1 GHz

<hr>

Consider three different processors P1, P2, and P3 executing the same instruction set. P1 has a 3.00 GHz clock rate and a CPI of 1.5. P2 has a 2.50 GHz clock rate and a CPI of 1.0. P3 has a 4.00 GHz clock rate and has a CPI of 2.2.

a. Find execution time for each processor {The first three answer boxes in order of processor number, only write the rounded (up) time in seconds in format of d.d; e.g. 0.7} for a program with 2.00e+9 (2e+09 is a notation for 2x(10^9) = 2,000,000,000) instructions. Which one is the fastest {The fourth answer box just the number of fastest processor, 1, 2, or 3}?

b. If the processors each execute a program in 10 seconds, find the number of instructions that they are running {The answer boxes 5, 6, and 7 for processor 1 , 2, and 3 respectively, in the format of d.dde+dd; e.g. 1.79e+10}? We are trying to reduce the execution time by 20% but this leads to an increase of 10% in the CPI. What clock rate in GHz should we have to get for this time reduction for each processor {The last three answer boxes in order of processor numbers in format of d.d; e.g. 3.1}?





<hr>


"The Pentium 4 Prescott processor, released in 2004, had a clock rate of 3.60 GHz and voltage of 1.25 V. Assume that, on average, it consumed 90 W of power.
The Core i5 Ivy Bridge, released in 2012, had a clock rate of 3.40 GHz and voltage of 0.90 V. Assume that, on average, it consumed 40 W of power.

For each processor find the capacitive loads {The first answer box is for Pentium 4 and second answer box is for Core i5; values should be rounded in the format of d.dde-dd; e.g. 2.46e-09 - - do NOT write the unit ahead of your answer}."



<hr>

"The results of the SPEC CPU2006 bzip2 benchmark running on an AMD Barcelona has an instruction count of 2.389e+12, an execution time of 750 s, and a reference time of 9650 s.


a. Find the CPI if the clock cycle time is 0.333 ns {The first answer box with round value in format of d.dd; e.g. 0.86}.


b. Find the SPEC ratio {The second answer box with round value format of d.dd; e.g. 16.56}."

<hr>

do the following:
"Assume that for a program, compiler A results in a dynamic instruction count of 1.00e+9 and has an execution time of 1.1 s, while compiler B results in a dynamic instruction count of 1.20e+9 and an execution time of 1.5 s.


a. Find the average CPI for each program given that the processor has a clock cycle time of 1 ns {The first two answer box for compiler A and B, respectively. The answers should be rounded up in format of d.dd; e.g. 2.30}.


b. Assume the compiled programs run on two different processors. If the execution times on the two processors are the same, what is the ratio of frequency rate  for processor running compiler B's code to that of processor running compiler A's code? {The third answer box, rounded value in format of d.dd; e.g. 1.45}?



c. A new compiler is developed that uses only 6.00e+8 instructions and has an average CPI of 1.1.



d. What is the ratio of CPU time of compiler A to the CPU time of the new compiler? {Write your answer in the forth answer box in the format d.dd e.g 2.10}



e. What is the ratio of CPU time of compiler B to the CPU time of the new compiler? {Write your answer in the fifth answer box in the format d.dd e.g 0.70}"


<hr>


"Assume a program requires the execution of 50e+6 FP instructions, 110e+6 INT instructions, 80e+6 L/S instructions, and 16e+6 branch instructions. The CPI for each type of instruction is 1, 1, 4, and 2, respectively. Assume that the processor has a 2.00 GHz clock rate.


a. Find the execution time {The first answer box in the format of d.ddd; e.g. 5.857 - do NOT put the unit(s or seconds) ahead of your answer }?


b. What is the new CPI value of FP instructions if we want the program to run two times faster? {The second answer box, if impossible write "IMP", if possible write new CPI value in format of d.dd; e.g. 0.70}?


c. What is the new CPI value of L/S instructions if we want the program to run two times faster? {The third answer box, if impossible write "IMP", if possible write new CPI value in format of d.dd; e.g. 0.50} ?


d. What is the new(improved) execution time of CPU if the CPI of INT and FP instructions is reduced by 40% and the CPI of L/S and Branch is reduced by 30 {The fourth answer box in format of rounded d.ddd; e.g. 0.350 - do NOT put the unit(s or seconds) ahead of your answer}?"

<hr>



2. find C for each processor based on each GHz and V and avg P
P = C * V^2 * f
C = P / (V^2 * f)
- convert GHz to Hz, in order to yield Farads (F) units for C.

1 -
P = 90W
V = 1.25 V
f = 3.6 GHz = 3.6 x 10^9 Hz

C = 90 / (1.25^2) x (3.6 x 10^9) =
1.60e-08

- P = 40 W
- V = 0.90 V
- f = 3.40 GHz = 3.40 x 10^9 Hz

`C = 40 W / ( (0.90 V)^2 * (3.40 x 10^9 Hz) )`
`C = 40 / ( 0.81 * 3.40 x 10^9 )`
`C = 40 / ( 2.754 x 10^9 )`
`C = 1.45e-08`

3. IC = 2.389e+12, CPUtime = 750s, reference time = 9650

find CPI is clock cycle time - .333ns

**CPI = (Execution Time (T) * Clock Rate (f)) / Instruction Count (IC)**
- Instruction Count (IC) = 2.389e+12
- Execution Time (T) = 750 s
- Clock Cycle Time = 0.333 ns = 0.333 x 10^-9 s
- Rate = 1 / freq  = 3.003003… x 10^9 Hz
must be in seconds, b/c freq yields cycle per second

1. **Calculate CPI:**
	`CPI = (750 s * 3.003003… x 10^9 Hz) / (2.389 x 10^12 instructions)`
	`CPI = (2.25225225 x 10^12) / (2.389 x 10^12)`
	`CPI = 0.9427…`

find SPEC ratio
SPEC Ratio = Reference Time / Execution Time

**Given:**

- Execution Time = 750 s
- Reference Time = 9650 s

**Calculations:**
`SPEC Ratio = 9650 s / 750 s`
`SPEC Ratio = 12.8666…`

**Answer:**
SPEC Ratio = 12.87
