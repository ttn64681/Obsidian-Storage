
Q1:
Provide the the type and hexadecimal representation of following instruction (Machine code):    **sw $t1, 32($t2)**

i) Type (first answer box, only the char(s), e.g. R )

- *sw uses immediate value ->* **I type** (eye type)

ii) Hexadecimal representation (second answer box, put only the hexadecimal value without any space and in the exact bit size of the instruction type, e.g. 01A54321 - do **NOT** put the **0x** before your **HEX** answer & make sure that all alphabets(A,B,C,D,E) in your **HEX** answer(if any) should be **CAPITAL/UPPERCASE**)
- instruction maps to format:
	- `opcode (6 bits) | rs (5 bits) | rt (5 bits) | immediate (16 bits)`
- Field breakdown:
	- `The instruction ` sw \$t1, 32(\$t2) ` maps to the format` sw rt, offset(rs)
		- `opcode`: The operation code for `sw` -> *43 (in decimal) -> 101011 (6bit binary)*
		- `rs` (base address register): `$t2` -> *register #10 -> 01010 (5bit binary) *
		- `rt` (source register): `$t1` -> *register #9 -> 01001 (5-bit binary) *
		- `immediate` (offset): `32` -> *0000000000100000 (16bit binary)*

*101011  01010 01001 0000000000100000*
*-> hex:*
*1010 1101 0100 1001 0000 0000 0010 0000*
*->* **AD490020**
<HR>

Assume $t0 = 0xAAAAAAAA, $t1 = 0x12345678. what is the value of $t2 for the following sequence of instructions?  
  
1. sll $t2, $t0, 4  

- *shift left logical by 4 bit positions*
	- *A = 1010 -> AAAAAAAA -> 1010 1010 1010 1010 1010 1010 1010 1010*
	- *sll 4 -> 1010 1010 1010 1010 1010 1010 1010 0000*
	- *->* **AAAAAAA0**

2. or $t2, $t2, $t1  

- *bitwise OR of tI and t2*
	- *t1 = 12345678 ->* 
		- *0001 0010 0011 0100 0101 0110 0111 1000*
	- *t2 = AAAAAAA0 ->*
		- *1010 1010 1010 1010 1010 1010 1010 0000*
	- *OR ->*
		- *1011 1010 1011 1110 1111 1110 1111 1000*
	- *Hex ->* **BABEFEF8**

Fill the first answer box with the 32 bit hexadecimal value of $t2 after the first line of instructions and the second answer box with  value of $t2 after second line of instructions, e.g. 0C765123 (no space and exact 32 bits hexadecimal)

do **NOT** put the **0x** before your **HEX** answer & make sure that all alphabets(A,B,C,D,E) in your **HEX** answer(if any) should be **CAPITAL/UPPERCASE**

<HR>

Assume $t0 = 0xAAAAAAAA . what is the value of $t2 for the following sequence of instructions?

1. srl $t2, $t0, 3  

	- *A = 1010 -> AAAAAAAA -> 1010 1010 1010 1010 1010 1010 1010 1010*
	- *srl 4 -> 0001 0101 0101 0101 0101 0101 0101 0101*
	- $t2 -> **15555555**

2. andi $t2, $t2, 0xFFEF

- *FFEF -> 
	- zero-extended since andi is a logical operation, not arithmetic (extension depends entirely on instruction being used)
	- Logical (like andi, ori, xori,)
		- immediate val treated as 16-bit unsigned bitmask
		- mask with 0's to reach 32-bit register
	- Arithmetic (like addi, addiu)
		- -> 0x0000FFEF
		- sign extend to reach 32-bit register
	- *-> 0000 0000 0000 0000 1111 1111 1110 1111*
- *$t2 ->15555555* *-> 0001 0101 0101 0101 0101 0101 0101 0101*
- *AND -> 0000 0000 0000 0000 0101 0101 0100 0101*
- **Hex -> 00005545**

Fill the first answer box with the 32 bits hexadecimal value of $t2 after the first line of instructions and the second answer box with  value of $t2 after second line of instructions, e.g. 00AC7123 (no space and exact 32 bits hexadecimal)

do **NOT** put the **0x** before your **HEX** answer & make sure that all alphabets(A,B,C,D,E) in your **HEX** answer(if any) should be **CAPITAL/UPPERCASE**

<hr>

Assume $t0 holds the value 0x00101000. What is the value of $t2 after the following instructions?

     slt $t2, $0, $t0  
     bne $t2, $0, ELSE  
     j DONE  
ELSE:  addi $t2, $t2, 2  
DONE:

- *set on less than*
	- *if $0 < \$t0*
		- then $t2 = 1
		- else = 0
	- if 0 < 00101000
		- **yes: $t2 = 1**
- *branch on not equal*
	- *if $t2 = \$0*
		- then DONE
		- else -> jump to ELSE
	- *$t2 ≠ 0, so ELSE:*
		- *add 2 to $t2 (1)* 
		- **2 + 1 = 3**


Fill the answer box with the **FINAL(After the execution of all lines above)** integer value of $t2, e.g. 5.  
The value should be a decimal value(integer).

<hr>
Q6:

Consider the program and the initial values for registers and memory as below. Initial value of **$s5 = 20.** What are the values in registers $s2, $s4, $s5 and memory when program stops?
```
addi $s2, $zero, 4   
sll $s2,$s2,2  
li $s5,4  
sub $s4, $s2, $s5   
lw $s5, 0($s4)
```

Current Memory Structure is given below:

| Memory Address | Values |
| -------------- | ------ |
| 8              | 124    |
| 12             | 152    |
| 16             | 24     |
| 20             | 20     |
| 24             | ....   |
line-by-line
1. *$s2 = 0 + 4 = 4 = 0100*
2. **$s2** *= 10000 =* **16**
3. *$s5 = 0100*
4. **$s4** *= 16 - 4 =* **12**
5. **$s5 = 152**
	1. *lw - load word, rd, offset_val(reg_val)*
	2. *load into s5 reg_val which is 12*

Fill the first three answer boxes with the integer value (e.g. 14) of $s5, $s2, and $s4 respectively. If **any** of the current memory values changed because of the code execution type "Yes" in 4th answer box, otherwise type "No".

- **No current memory address values were changed due to code execution**
	- *only READ (lw, li) and never WRITE (sw)*

<hr>


Find the shortest sequence of MIPS instructions that extracts bits 16 down to 11 from register **$t0** and uses the value of this field to replace bits 31 down to 26 in register $t1 without changing the other 26 bits of register $t1.  
  
NOTE: Type your MIPS Instructions line-by-line. You are not allowed to upload image for this.

**For eg. Answer can be like this:(This is just an example)**  
sll $t2, $t2, 4  
ori $t2, $0, 0x3FF  
and $t1, $t1, $t2  
or $t1, $t1, $t0

```
# Goal: transfer 6 bits from 16-11 to 6 bits at 31-26
## Note 1: Register has 32 bits (bit 0 - bit 31)
## Note 2: We can mutate t0 however we please, as long as we copy the 6 bits from 16-11

# Step 1: Isolate 6 bits from 16-11 by shifting right 11
srl $t0, $t0, 11 # LSB is bit 11
andi $t0, $t0, 0x3F # keep only right 6 bits by AND w/ 111111
sll $t0, $t0, 26 # shift the 6 bits up to target positions at bits 31-26

sll $t1, $t1, 6 # make space for 6 bits to left by shifting left by 6
srl $t1, $t1, 6 # shift back right to create 6 left-most zeros
or $t1, $t1, $t0 # combine via OR

```

<hr>

Translate the following C code to MIPS assembly code. Use a minimum number of instructions. Assume that the values of a, b, i, and j are in registers $s0, $s1, $t0, and $t1, respectively. Also, assume that register $s2 holds the base address of the array D.

for (i=0; i<a; i++)  
     for(j=0; j<b; j++)  
          D[i+j] = 10;

s0 = a
s1 = b
t0 = i
t1 = j
s2 = D[1]

t4 = i + j

t2 stores beq for i \< a
t3 stores beq for j \<b

t5 = 10
```
li   $t5, 10 # load constant value 10 into a temporary register.  
add  $t0, $zero, $zero # initialize i = 0.

# Outer Loop (for i)  
LOOP_I:  
    slt $t2, $t0, $s0 # Set $t2=1 if i < a.  
    beq $t2, $zero, EXIT # If i >= a, exit the loops.

    # Inner Loop (for j)  
    add $t1, $zero, $zero # Initialize j = 0 at the start of each outer loop.  
    
LOOP_J:  
    slt $t3, $t1, $s1 # Set $t3=1 if j < b.  
    beq $t3, $zero, END_J # If j >= b, exit the inner loop.

    # Loop Body  
    add $t4, $t0, $t1 # Calculate the index (i + j).  
    sll $t4, $t4, 2 # Multiply index by 4 to get the byte offset.  
    add $t4, $s2, $t4 # Get the full memory address of D[i+j].  
    sw $t5, 0($t4) # Store the value 10 at that address.

    addi $t1, $t1, 1 # Increment j (j++).  
    j LOOP_J # Jump back to the start of the inner loop.

END_J:  
    addi $t0, $t0, 1        # Increment i (i++).  
    j    LOOP_I             # Jump back to the start of the outer loop.

EXIT:  
    # Program continues here after loops are finished.
```

- initialize 10 (initial value of D[i + j])
- initialize i = 0

LOOP_I:
- if i < a (slt)
- continue:
	- initialize j = 0
- else:
	- EXIT

LOOP_J:
- if j < b (slt)
- continue:
	- calc i+j (t4)
	- calc byte offset (to get next position in array D)
	- add byte offset to D, and store 10 
	- increment j
	- jump back to LOOP_J
- else:
	- EXIT