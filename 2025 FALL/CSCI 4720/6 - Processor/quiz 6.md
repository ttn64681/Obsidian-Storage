
`LWI rt, rd(rs)` — semantics: `R[rt] ← MEM[ R[rs] + R[rd] ]`.

### What the datapath _must_ do (control signals)

- **Read register file**: read `R[rs]` and `R[rd]` → both register-file read ports used.
    
- **ALU input selection**: second ALU operand must come from the register file (not an immediate). So **ALUSrc = 0**.
    
- **ALU operation**: add the two register values → ALU performs `ADD`.
    
- **Memory**: use ALU result as address to **MemRead = 1** (and **MemWrite = 0**).
    
- **Writeback**: memory read data must be written into register `rt` → **MemtoReg = 1** and **RegWrite = 1**.
    
- **Destination register**: since this is a load-style write, the destination is `rt` (instruction bits [20:16]) — so the RegDst MUX must select the `rt` field (RegDst = 0 in the classic single-cycle datapath where RegDst = 1 selects rd).
    

Any correct highlighted path must reflect **all** of the above.
- Both register read outputs → ALU inputs. (ALUSrc = 0)
    
- ALU result → Data memory address input.
    
- MemRead asserted and memory read data → MemtoReg → register write data.
    
- RegWrite true and destination field = `rt` (RegDst selects the `rt` bits).


<hr>




<hr>


## **Question 3** (21 points)

 

Problems in this question assume that logic blocks needed to implement a processor's datapath have the following latencies:

| **I-Mem** | **Add** | **Mux** | **Alu** | **Regs** | **D-Mem** | **Sign-Extend** | **Shift-Left-2** |
| --------- | ------- | ------- | ------- | -------- | --------- | --------------- | ---------------- |
| 250ps     | 50ps    | 20ps    | 70ps    | 90ps     | 300 ps    | 10ps            | 10ps             |


a. Consider a datapath similar to **question 1,** but for a processor that only has one type of instruction: **sw rt, offset(rs)**. What would the cycle time be for this datapath?

b. Consider a datapath similar to **question 1,** but for a processor that only has one type of instruction: **add rd, rs, rt**. What would the cycle time be for this datapath?

c. Consider a datapath similar to **question 1,** but for a processor that only has one type of instruction: **beq rs, rt, offset**. What would the cycle time be for this datapath?

**Note: Answers are cycle time that means they have the unit in milliseconds/nanoseconds/picoseconds. Please specify the unit of your answer at the end with a space.  
For eg. If your answer is 782 nanoseconds, you would type "782 ns" in the answer box below. If your answer is 120 picoseconds, you would type "120 ps" in the answer box below.**


<hr>




<hr>


## **Question 5** (20 points)

 

For the problems in this question, assume that there are no pipeline stalls and that the breakdown of executed instructions is as follows:

add: 20%
addi: 20%
not: 0%
beq: 25%
lw: 25%
sw: 10%

a. In what fraction of all cycles is the register file used?**(Box 1)**  
b. In what fraction of all cycles is the input of the sign-extend circuit needed? **(Box 2)**  
c. In what fraction of all cycles is the shift left 2 circuit needed?**(Box 3)**  
d. In what fraction of all cycles is the instruction memory used? **(Box 4)**

Note: For all the answers - **DO NOT** include the percentage sign. Just type the numeric value in the box.