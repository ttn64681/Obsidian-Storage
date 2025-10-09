**General Concepts and Constraints**
- MIPS has a 32x32-bit register file.
- There are 32 registers, each 32 bits wide.
- A 32-bit piece of data is called a "word".
- Registers are numbered 0 to 31.
- Memory is byte-addressed, meaning each 8-bit byte has a unique address.
- Word addresses must be a multiple of 4.
- Instructions are encoded in binary as 32-bit words. This is called machine code.
- The Program Counter (PC) is a register that holds the address of the current instruction being executed.

**Register Types and Usage**
- **$zero (r0)**: The constant value 0.
- **$v0 - $v1 (r2-r3)**: Used for storing result values from a procedure.
- **$a0 - $a3 (r4-r7)**: Used for passing arguments to a procedure.
- **$t0 - $t9 (r8-r15, r24-r25)**: Temporary registers that are not preserved across procedure calls.
- **$s0 - $s7 (r16-r23)**: Saved registers that must be preserved across procedure calls.
- **$sp (r29)**: The Stack Pointer, which points to the top of the stack.
- **$ra (r31)**: The Return Address, used to store where a procedure should return to after it finishes.
- **$at (r1)**: Reserved for the assembler to use for pseudo-instructions.

**Instruction Formats**
- **R-Format**: Used for register-to-register operations like `add` and `sub`. It has fields for opcode, three registers (two source `rs`, `rt` and one destination `rd`), a shift amount (`shamt`), and a function code (`funct`).
- **I-Format**: Used for operations with an immediate (constant) value, like `addi`, `lw`, and `sw`. It has fields for opcode, two registers (`rs`, `rt`), and a 16-bit constant or address.

**Operations and Commands**

**Arithmetic Operations**
- **add rd, rs, rt**: Adds the contents of two source registers and stores the result in a destination register.
- **sub rd, rs, rt**: Subtracts the contents of two source registers and stores the result in a destination register.
- **addi rt, rs, constant**: Adds an immediate value to a register. Used with a negative constant to perform subtraction.

**Data Transfer Operations**
- **lw rt, offset(rs)**: "Load Word." Loads a 32-bit word from memory into a register. The memory address is calculated by adding the `offset` to the value in register `rs`.
- **sw rt, offset(rs)**: "Store Word." Stores a 32-bit word from a register into memory.
- **lb rt, offset(rs)**: "Load Byte." Loads an 8-bit byte from memory into the rightmost 8 bits of a register and sign-extends it to 32 bits.
- **lbu rt, offset(rs)**: "Load Byte Unsigned." Loads an 8-bit byte from memory and zero-extends it to 32 bits.
- **sb rt, offset(rs)**: "Store Byte." Stores the rightmost 8 bits of a register into a byte in memory.
- **li reg, imm**: "Load Immediate." A pseudo-instruction that loads an immediate value into a register.    
- **la reg, addr**: "Load Address." A pseudo-instruction that loads a memory address (label) into a register. 
- **lui rt, constant**: "Load Upper Immediate." Loads a 16-bit constant into the upper (leftmost) 16 bits of a register, clearing the lower 16 bits. Used with `ori` to load a full 32-bit constant.   
- **move rd, rs**: "Move." A pseudo-instruction that copies the content of one register to another.

**Logical Operations**
- **and rd, rs, rt**: Performs a bitwise AND operation.
- **or rd, rs, rt**: Performs a bitwise OR operation.
- **nor rd, rs, rt**: Performs a bitwise NOR operation. Can be used to perform a NOT.
- **andi rt, rs, imm**: Bitwise AND with an immediate value.
- **ori rt, rs, imm**: Bitwise OR with an immediate value.
- **sll rd, rt, shamt**: "Shift Left Logical." Shifts the bits of a register left by the specified shift amount.
- **srl rd, rt, shamt**: "Shift Right Logical." Shifts the bits of a register right by the specified shift amount.

**Conditional Branch and Jump Operations**
- **beq rs, rt, Label**: "Branch on Equal." If the values in the two registers are equal, jump to `Label`.
- **bne rs, rt, Label**: "Branch on Not Equal." If the values in the two registers are not equal, jump to `Label`.
- **bge rs, rt, Label**: "Branch on Greater Than or Equal." If the value in rs is ≥ rt,  jump to `Label.`
- **blez rs, rt, Label**: "Branch on Less Than or Equal to Zero." If rs ≤ 0, jump to `Label.`
- **slt rd, rs, rt**: "Set on Less Than." If `rs` < `rt`, set `rd` to 1; otherwise, set `rd` to 0. This is a signed comparison.
- **slti rt, rs, imm**: "Set on Less Than Immediate." Compares a register to an immediate value.
- **sltu**: "Set on Less Than Unsigned." The unsigned version of `slt`.
- **j Label**: "Jump." An unconditional jump to `Label`.
- **jal Label**: "Jump and Link." Used for procedure calls. Jumps to `Label` and stores the return address in the `$ra` register.
- **jr rs**: "Jump Register." Jumps to the address contained in the specified register. `jr $ra` is used to return from a procedure.

**Procedure Calling**
- **Arguments**: The first four arguments are passed in registers `$a0` - `$a3`.
- **Return Values**: Results are returned in registers `$v0` and `$v1`.
- **The Stack**: A last-in, first-out data structure used to save registers. The stack pointer (`$sp`) points to the top of the stack. Pushing is done with `sw`, and popping is done with `lw`.
- **Calling a Procedure**: Use `jal Label`.
- **Returning from a Procedure**: Use `jr $ra`.
- **Non-Leaf Procedures**: Procedures that call other procedures must save their return address (`$ra`) on the stack before making a nested `jal` call.

**Memory Layout**
- **Text**: Contains the program code.
- **Static data**: Contains global variables and constants.
- **Dynamic data (heap)**: Memory that is allocated at runtime.
- **Stack**: Used for automatic storage during procedure calls.