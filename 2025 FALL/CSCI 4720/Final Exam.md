

# 2

Draw FSM (Finite State Machine) for 3 bits counter that can count **0, 2, 3, 5** only and implement it using D flip flop.

Your answer should include Truthable, Boolean expression and Circuit diagram.


|| Q2​\Q1​Q0​ | 00 | 01 | 11 | 10 | | :--- | :--- | :--- | :--- | :--- | | **0** | 0 | X | **1** | 0 | | **1** | X | 0 | **X** | X ||

# 3
### **Checklist: What to look for in the "beq" Datapath**

To find the correct choice, look for the image that highlights **only** these specific paths:

1. **ALU Input Mux (ALUSrc):**
    
    - **Requirement:** The multiplexer before the ALU must select the path coming from **Register Read Data 2**, _not_ the sign-extended immediate.
        
    - **Why?** `beq` compares two registers (r1−r2). If the path highlights the sign-extend block going into the ALU, that is wrong (that would be for `addi`, `lw`, or `sw`).
        
2. **Branch Target Calculation (The "Top" Adder):**
    
    - **Requirement:** You should see a highlighted path going from **Sign-Extend → Shift-Left-2 → Add** (usually the adder at the top right).
        
    - **Why?** The processor calculates the address to jump to (PC + 4 + offset) in parallel with the comparison.
        
3. **The "Zero" Line:**
    
    - **Requirement:** The line coming out of the ALU labeled **"Zero"** must be highlighted and leading to the AND gate (or the control logic for the PC Mux).
        
    - **Why?** This signal tells the PC whether to branch or not.
        
4. **Register File (No Write Back):**
    
    - **Requirement:** The path for **"Write Data"** going back into the Register File should **NOT** be highlighted.
        
    - **Why?** `beq` does not save any result. If you see the path looping back from the Data Memory or ALU to the Register File highlighted, that choice is **wrong**.
        
5. **Data Memory (Ignored):**
    
    - **Requirement:** The Data Memory block should generally be ignored (no read or write lines highlighted active).
        

### **Summary for Selection**

- **Look for:** Two registers going to ALU + "Zero" output + Top Adder calculating address.
    
- **Avoid:** Any path writing back to the register file or any path sending the immediate (Sign-extend) directly into the ALU.

# 4 <span style="background:#fff88f">why 0 and why X?</span>

**What are the values of following control signals for the above instruction?**

RegDest = ____ (Box 1)

RegWrite = ____ (Box 2)

ALUSrc= ____ (Box 3)

MemWrite = ____ (Box 4)

MemRead = ____ (Box 5)

MemToReg = ____ (Box 6)

PCsrc = ____ (Box 7)

X
0
0
0
0
X
1

- **RegDest:** **X** (Don't Care) - No write happens.
    
- **RegWrite:** **0** - **Crucial:** We are NOT writing to the register file (matches Choice 2).
    
- **ALUSrc:** **0** - The ALU compares `rt` (Reg Data 2) vs `rs`.
    
- **MemWrite:** **0** - No memory write.
    
- **MemRead:** **0** - No memory read.
    
- **MemToReg:** **X** (Don't Care) - No write happens.
    
- **PCsrc:** **1** (or labeled "Branch") - The branch decision logic is active.

# 5
Problem in this part assume that logic blocks needed to implement a processor's datapath have the following latencies:

| **I-Mem** | **Add** | **Mux** | **Alu** | **Regs** | **D-Mem** | **Sign-Extend** | **Shift-Left-2** |
| --------- | ------- | ------- | ------- | -------- | --------- | --------------- | ---------------- |
| 230ps     | 60ps    | 20ps    | 80ps    | 100ps    | 250 ps    | 10ps            | 15ps             |
![[q5 diagram figure.png]]

Consider a datapath similar to the above figure(same as previous question), but for a processor that only has one type of instruction: **beq r1, r2, offset**.

What would be the cycle time for this datapath for **branch on equal** instruction?(Box 1)

**Note: Answer is cycle time that means it has the unit in milliseconds/nanoseconds/picoseconds. Please specify the unit of your answer at the end with a space.**  
**For eg. If your answer is 782 nanoseconds, you would type "782 ns" in the answer box below. If your answer is 120 picoseconds, you would type "120 ps" in the answer box below.**

For the `beq` instruction, the processor performs two major tasks in parallel after fetching the instruction. The **Cycle Time** is determined by whichever path takes the longest time to complete.

**Latencies:**

- **I-Mem:** 230 ps
    
- **Regs:** 100 ps
    
- **Mux:** 20 ps
    
- **ALU:** 80 ps
    
- **Add:** 60 ps
    
- **Sign-Extend:** 10 ps
    
- **Shift-Left-2:** 15 ps
    

---

**Path 1: Branch Decision (The Comparison Path)** This path determines _if_ the branch should be taken.

1. **Instruction Fetch:** Retrieve instruction from I-Mem. (**230 ps**)
    
2. **Register Read:** Read `r1` and `r2`. (**+ 100 ps**)
    
3. **ALU Mux:** Select register input (not immediate). (**+ 20 ps**)
    
4. **ALU Operation:** Compare registers (subtract). (**+ 80 ps**)
    
5. **PC Mux:** The Zero flag controls the Mux to update PC. (**+ 20 ps**)
    

**Total:** 230+100+20+80+20=450 ps

**Path 2: Branch Target Address Calculation** This path calculates _where_ the branch goes.

1. **Instruction Fetch:** (**230 ps**)
    
2. **Address Logic:**
    
    - Sign-Extend (**+ 10 ps**)
        
    - Shift-Left-2 (**+ 15 ps**)
        
    - Add (PC + Offset) (**+ 60 ps**)
        
3. **PC Mux:** (**+ 20 ps**)
    

**Total:** 230+10+15+60+20=335 ps

---

**Conclusion:** The **Branch Decision Path (450 ps)** is slower than the Address Calculation Path (335 ps). Therefore, the cycle time must be set to the slower path.

**Answer:** `450 ps`
# 6
*i have done a similar question in module 5 quiz question 3*

Use the unsigned multiplication algorithm to multiply the unsigned binary numbers 0110 by 0111.

**Note :** For each step show the contents of the registers and the operation performed. Your answer should be written in this tabular format. **(You can draw the table in the given answer box OR can upload image of your answer)**

| Iteration | Step | Multiplier | Multiplicand | Production |
| --------- | ---- | ---------- | ------------ | ---------- |
|           |      |            |              |            |
|           |      |            |              |            |
|           |      |            |              |            |

**Instead of uploading images, please try to use the insert table option of the above given options and then type your information in the inserted in the table. If you are not comfortable with that you may upload image.**

| **Iteration** | **Step**                                   | **Multiplier** | **Multiplicand** | **Product**   |
| ------------- | ------------------------------------------ | -------------- | ---------------- | ------------- |
| **0**         | **Initial values**                         | **0111**       | **0000 0110**    | **0000 0000** |
| **1**         | 1: LSB=1 $\rightarrow$ Prod = Prod + Mcand | 0111           | 0000 0110        | 0000 0110     |
|               | 2: Shift left Multiplicand                 | 0111           | 0000 1100        | 0000 0110     |
|               | 3: Shift right Multiplier                  | **0011**       | 0000 1100        | 0000 0110     |
| **2**         | 1: LSB=1 $\rightarrow$ Prod = Prod + Mcand | 0011           | 0000 1100        | 0001 0010     |
|               | 2: Shift left Multiplicand                 | 0011           | 0001 1000        | 0001 0010     |
|               | 3: Shift right Multiplier                  | **0001**       | 0001 1000        | 0001 0010     |
| **3**         | 1: LSB=1 $\rightarrow$ Prod = Prod + Mcand | 0001           | 0001 1000        | 0010 1010     |
|               | 2: Shift left Multiplicand                 | 0001           | 0011 0000        | 0010 1010     |
|               | 3: Shift right Multiplier                  | **0000**       | 0011 0000        | 0010 1010     |
| **4**         | 1: LSB=0 $\rightarrow$ No operation        | 0000           | 0011 0000        | 0010 1010     |
|               | 2: Shift left Multiplicand                 | 0000           | 0110 0000        | 0010 1010     |
|               | 3: Shift right Multiplier                  | **0000**       | 0110 0000        | **0010 1010** |

# 7
Select the equivalent number (in decimal) that is represented by the single-precision floating-point for the given IEEE 754

1 10000100 1010000000000000000001

Binary: 1 10000100 1010000000000000000001

We break this down into the IEEE 754 components:
    Sign Bit (S): 1
    Exponent (E): 10000100
    Fraction (Mantissa): 1010000000000000000001 (Note: The provided fraction has 22 bits. Assuming the missing 23rd bit is a 0 or the string represents the significant bits).

- **Break Down Components:**
    - **Sign (S):** `1` → **Negative (-)**
    - **Exponent (E):** `10000100`
        - Decimal value: 128+4=132.
        - *Subtract Bias (127): 132−127=5.*
    - **Mantissa (Fraction):** `10100...`
        - Add implicit leading 1: 1.1010..
        - Convert to decimal: 1+0.5+0.125=1.625.
- **Calculate Value:**
    - Value=−1×1.625×25
    - Value=−1.625×32
    - Value=−52

# 8
There are two single precision floating point numbers that are saved in registers $f6 and $f8. Write a piece of code in MIPS assembly language  that compares these two numbers and if $f6 is less than $f8 then save 1 in register $s1 and if condition is not true, save 0 in register $s1.

**NOTE**: Type your MIPS Instructions line-by-line. You are not allowed to upload image for this.


# 9
In this question, we examine how data dependences affect execution in the basic 5-stage pipeline for code below.

lw $s3,4($ s5)  
sw $s3,0($s4)  
or $s5,$s3,$s4  
and $s7,$s4,$s5

Assume the following cycle times for each of the without forwarding and full forwarding.
( Without Forwarding: 250ps, With Full Forwarding: 300ps )

a. Assume there is no forwarding in this pipelined processor. Indicate hazards and add NOP instructions to eliminate them and rewrite these instructions with the NOP instructions in your answer.

b. Assume there is full forwarding. Indicate hazards and add NOP instructions to eliminate them and rewrite these instructions with the NOP instructions in your answer. 

c. What is the total execution time of this instruction sequence without forwarding and with full forwarding? What is the speedup achieved by adding full forwarding to a pipeline that had no forwarding?

**Note:** Type your answer in the below box. Uploading image is not allowed. The last numerical questions asks for speedup. Please use the following guideline to solve for speedup.

**Speedup is not the difference in two timings.** Consider two execution times t1 = 200 ns and t2 = 150 ns. 

The speed up is ratio of Higher Time(Slower Execution) / Lower Time(Faster Execution). Thus, speedup = 200/150(**Unit needs to be same** - in this case nanoseconds) = 1.33

# 10
*i believe i've answered a question like this before and got it right*
For the given SR-LAtch using NAND Gate. Please select the appropriate output for the given input

Inputs:
1. When S=0 R=0
2. When S=1 R=0

Outputs:
a. Q'=1 Q=0
b. Q'=Not Applicable Q=Not Applicable
c. Q'=Memory State Q=Memory State
d. Q'=0 Q=1

(Each input corresponds to 1 output answer)