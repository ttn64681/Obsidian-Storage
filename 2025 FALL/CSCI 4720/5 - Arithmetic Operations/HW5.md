## Question 1 (10 points)

Assume 35 and 122 are signed 8-bit decimal integers.

a. Calculate 35 + 122. (Please write your answer in answer box 1. The result is in Decimal! )

b. Is there overflow? (Please write your answer in answer box 2, Your answer should either be Yes/No)


- **35** in 8-bit binary is: `00100011` (Positive, sign bit is 0)
    
- **122** in 8-bit binary is: `01111010` (Positive, sign bit is 0)
    
- **The Addition:**
    
    ```
      00100011   (35)
    + 01111010   (122)
    -----------------
      10011101
    ```

<hr>

## **Question 2** (10 points)

Write down the binary representation of the decimal number 13.5 assuming the IEEE 754 single precision format.

**Note:** Do not directly write your answer. Please show steps how you got binary representation for the above decimal number. 

**`M5.3.pdf`, Page 5**.

1. **Sign (S):** The number is positive.
    
    - **S = 0**
        
2. **Binary Conversion:**
    
    - Integer part: `13` = 8 + 4 + 1 = `1101`
        
    - Fractional part: `0.5` = 1 * 2⁻¹ = `0.1`
        
    - Combined binary: `1101.1`
        
3. **Normalization:** - "We first normalize significand: `1.0 <= |significand| < 2.0`".
    
	- This means we _must_ move the decimal point until there is only one `1` to its left (the "hidden bit").
	    
	- Our binary number is: `1101.1`
	    
	- We need to move the decimal point **3 places to the left** to get: `1.1011`
	    
	- Because we moved the decimal 3 places _left_, the exponent is **3**.
	    
	- Our normalized number is: **`1.1011 x 2^3`**
        
4. **Biased Exponent:** The bias for single precision is **127** (from `M5.3.pdf`, Page 4).
    
    - `Biased Exponent = Actual Exponent + Bias`
        
    - `Biased Exponent = 3 + 127 = 130`
        
    - In 8-bit binary, `130` = 128 + 2 = **`10000010`**
        
5. **Assemble the 32-bit Number:**
    
    - **S:** `0`
        
    - **Exponent (8 bits):** `10000010`
        
    - **Fraction (23 bits):** `1011` (We pad with 19 zeros) -> `10110000000000000000000`
        

**Final Answer:** `0` `10000010` `10110000000000000000000`


<hr>

## **Question 3** (10 points)

 

Write down the binary representation of the decimal number 270.625 assuming the IEEE 754 single precision format.

**Note:** Do not directly write the answer. Please show steps how you got binary representation for the above decimal number. 

You can add image or write your answer in the box below.


- Decimal to IEEE (add bias) - S(0 or 1) 8-bit-biased-exponent 23-bit-fraction

- _**S = 0**_  
- Integer: 270 = 256 + 8 + 4 + 2 = 100001110  
- Fraction: 0.625 = 0.5 + 0.125  
- = 1*2⁻¹ + 0*2⁻² + 1*2⁻³ = 0.101  
- -> 100001110.101   

- Normalization -  
- normalize significand: 1.0 <= |significand| < 2.0  
- 100001110.101 -> move decimal to left (8 times) -> 1.00001110101 normalized number: 1.00001110101 x 2^8  
- _**Fraction = 00001110101**_  
- _**Actual Exponent = 8**_  

- Biased Exponent = actual exponent + Bias (127 for single precision)  
- Biased Exponent = 8 + 127 = 135  
- Biased Exponent = 135 -> 8-bit binary -> _**10000111**_  

- **Final IEEE:  
- **0 10000111 **00001110101**000000000000


<hr>
## **Question 4** (10 points)

 

What number is represented by the single-precision float for the given binary representation:

 1 01111100 11000000000000000000000

**Note:** Do not directly write your answer. Please show steps how you got decimal representation for the above binary number. 
### **IEEE to Decimal (subtract bias)**

1. **Deconstruct the 32-bit Number:**
    
    - **S = 1** (This means the number is negative)
        
    - **Exponent = 01111100**
        
    - **Fraction = 11000000000000000000000**
        
2. **Find the Actual Exponent (reverse biasing):**
    
    - First, convert the 8-bit Exponent from binary to decimal:
        
        01111100 = 64 + 32 + 16 + 8 + 4 = 124
        
    - Next, subtract the Bias (which is 127 for single precision):
        
        Actual Exponent = 124 - 127 = -3
        
3. **Find the Significand (1 + Fraction):**
    
    - The `Fraction` bits are `1100...`.
        
    - This represents the binary number `0.11`
        
    - Convert the binary fraction to a decimal:
        
        0.11 (binary) = (1 * 2⁻¹) + (1 * 2⁻²) = 0.5 + 0.25 = 0.75
        
    - `Significand = 1 + Fraction = 1 + 0.75 =` **1.75**
        
4. **Calculate the Final Number:**
    
    - `x = (-1)^S * (Significand) * 2^(Actual Exponent)`
        
    - `x = (-1)^1 * (1.75) * 2^(-3)`
        
    - `x = -1 * 1.75 * (1/8)`
        
    - `x = -1.75 / 8`
        
    - **x = -0.21875**


<hr>
## **Question 5** (10 points)

 

How is subtraction implemented using addition in the ALU?

**Note: Just write steps/procedure.**




<hr>

Use the unsigned multiplication algorithm to multiply the unsigned binary numbers 1010 by 0011.

**Note :** For each step show the contents of the registers and the operation performed. Your answer should be written in this tabular format. **(You can draw the table in the given answer box OR can upload image of your answer. You can add multiple images).**

|   |   |   |   |   |
|---|---|---|---|---|
|Iteration|Step|Multiplier|Multiplicand|Production|
||||||
||||||
||||||

- **"Contents of the registers"**: These are the `Multiplier`, `Multiplicand`, and `Product` columns. You are showing the 4-bit or 8-bit value inside each register at each step.
    
- **"Operation performed"**: This is the `Step` column (e.g., "1a: Add Mcand to Prod", "2: Shift left Multiplicand", etc.).

You get the answer by following a **fixed 3-step algorithm** for each iteration. This algorithm is _directly_ from your lecture slides: **`M5.2 Arithmetic for Computers.pdf`** on **Page 8 (the flowchart)** and **Page 9 (the table)**.

just repeat the same 3 steps, once for each bit of the multiplier.

### 3 Steps (The Algorithm)

You will repeat these 3 steps 4 times (because your multiplier `0011` is 4 bits long).

- **Step 1: Test the Multiplier's LSB.**
    
    - Look at the _very last bit_ (the LSB, or `Multiplier0`) of the `Multiplier` register.
        
- **Step 2: Add or Do Nothing.**
    
    - If the LSB from Step 1 is **`1`**: Add the _entire_ `Multiplicand` register to the `Product` register.
        
    - If the LSB from Step 1 is **`0`**: Do nothing ("No operation").
        
- **Step 3: Shift.**
    
    - Shift the _entire_ `Multiplicand` register **LEFT** by 1 bit (padding with 0 on the right).
        
    - Shift the _entire_ `Multiplier` register **RIGHT** by 1 bit (padding with 0 on the left).
        

### Re-Trace the Table With These Steps:

**Multiplicand = `1010` (10) | Multiplier = `0011` (3)**

**Iteration 0:**

- **Step:** Initial values.
    
- **Multiplier:** `0011`
    
- **Multiplicand:** `0000 1010` (Must be 8 bits, as `n+m` = 4+4=8)
    
- **Product:** `0000 0000` (Starts at 0)
    

**Iteration 1:**

- **Step 1 (Test):** Multiplier is `001**1**`. The LSB is **1**.
    
- **Step 2 (Add):** LSB is 1, so we add.
    
    - `Product` = `Product` + `Multiplicand`
        
    - `Product` = `0000 0000` + `0000 1010` = **`0000 1010`**
        
- **Step 3 (Shift):**
    
    - Shift `Multiplicand` left: `0000 1010` -> `0001 0100`
        
    - Shift `Multiplier` right: `0011` -> `0001`
        
- **End of Iteration 1:**
    
    - **Multiplier:** `0001`
        
    - **Multiplicand:** `0001 0100`
        
    - **Product:** `0000 1010`
        

**Iteration 2:**

- **Step 1 (Test):** Multiplier is `000**1**`. The LSB is **1**.
    
- **Step 2 (Add):** LSB is 1, so we add.
    
    - `Product` = `Product` + `Multiplicand`
        
    - `Product` = `0000 1010` + `0001 0100` = **`0001 1110`**
        
- **Step 3 (Shift):**
    
    - Shift `Multiplicand` left: `0001 0100` -> `0010 1000`
        
    - Shift `Multiplier` right: `0001` -> `0000`
        
- **End of Iteration 2:**
    
    - **Multiplier:** `0000`
        
    - **Multiplicand:** `0010 1000`
        
    - **Product:** `0001 1110`
        

**Iteration 3:**

- **Step 1 (Test):** Multiplier is `000**0**`. The LSB is **0**.
    
- **Step 2 (No-Op):** LSB is 0, so we do nothing. Product stays `0001 1110`.
    
- **Step 3 (Shift):**
    
    - Shift `Multiplicand` left: `0010 1000` -> `0101 0000`
        
    - Shift `Multiplier` right: `0000` -> `0000`
        

**Iteration 4:**

- **Step 1 (Test):** Multiplier is `000**0**`. The LSB is **0**.
    
- **Step 2 (No-Op):** LSB is 0, so we do nothing. Product stays `0001 1110`.
    
- **Step 3 (Shift):**
    
    - Shift `Multiplicand` left: `0101 0000` -> `1010 0000`
        
    - Shift `Multiplier` right: `0000` -> `0000`
        

**Final Answer:** After 4 iterations, the `Product` register contains **`0001 1110`**, which is `16 + 8 + 4 + 2 = 30`.

<hr>

# Question 7 (30 points)
 
Write a program that compare two single precision floating point numbers numA and numB. If numA is greater than numB, Swap the numbers.

NOTE: Type your MIPS Instructions line-by-line. You are not allowed to upload image for this.


```
# --- Assumptions---
# $s0 - holds memory addr of 'numA'
# $s1 - holds memory addr of 'numB'



main:
# 1. load the two single-precision floats from memory
# lwc1 = Load Word Coprocessor 1
lwc1 $f0, 0($s0) # load numA into float reg $f0
lwc1 $f2, 0($s1) # load numB into float reg $f2

# 2. compare if numA &gt; numB (same as !(numA &lt;= numB))
# c.le.s = Compare Less Than or Equal, Single-Precision&nbsp;
c.le.s $f0, $f2 # set FP condition flag if numA NOT greater than numB

# 3. if numA NOT greater than numB, skip swap)
# bc1t = Branch on Coprocessor 1 True&nbsp;
bc1t skip_swap&nbsp;

# 4. swap the numbers (this code only runs if A &gt; B)
# swc1 = Store Word Coprocessor 1&nbsp;
swc1 $f0, 0($s1) # store numA ($f0) at numB's address ($s1)
swc1 $f2, 0($s0) # store numB ($f2) at numA's address ($s0)



skip_swap:
# 5. exit program
li $v0, 10 # exit
syscall
```