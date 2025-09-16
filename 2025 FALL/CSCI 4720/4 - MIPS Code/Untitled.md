NEED System Calls to do I/O Operations


| Service      | System call code | Arguments     | Result           |                                                                         |
| ------------ | ---------------- | ------------- | ---------------- | ----------------------------------------------------------------------- |
| print_int    | 1                | $a0 = integer |                  | update register $v0, which stores result, and $a0, which stores int arg |
| print_string | 4                | $a0 = string  |                  | pass address of string to service                                       |
| read_int     | 5                |               | integer (in $v0) | update register $v0, which stores result,                               |
|              |                  |               |                  |                                                                         |
|              |                  |               |                  |                                                                         |
- Library function calls:
	- eventually call system calls
- System calls are provided by os kernel

vi test_io.s:

INCORRECT:
```
.data

message:

.asciiz "Please input an integer:\n"

message_out:

.asciiz "The integer you just"

  

.text

main:

la $a0, message # loads addr of message into register $a0

li $v0, 4 # loads int 4 into register $v0, which is **print_string**

syscall # executes syscall specified by $v0

li $v0, 5 # loads int 5 into register $v5, which is **read_int**

syscall

move $a0, $v0 # we move $v0 (which is )

li $v0, 1 # loads int 1 into register $v0, which is **print_int**

syscall

jr $ra # Jumps to addr in $ra, typically used to exit main func
```

CORRECT:
```
.data

message:

.asciiz "Please input an integer:\n"

message_out:

.asciiz "The integer you just inputted is:\n"

  

.text

main:

la $a0, message

li $v0, 4

syscall

li $v0, 5

syscall

move $a1, $v0

la $a0, message_out

li $v0, 4

syscall

move $a0, $a1

li $v0, 1

syscall

jr $ra
```

- to do a print system call, you need $a0 to store the argument you want to print
- therefore, you must always update $a0 accordingly
- You can create temporary value stored at reg $a1 if wanted/needed


```
.data

message:

.asciiz "Please input an integer:\n"

message_out:

.asciiz "The integer you just inputted is:\n"

message_equal:

.asciiz "Congratulations. You got it!\n"

  

.text

main:

la $a0, message

la $a2, message

li $v0, 4

syscall

move $t0, $v0

la $a0, message_equal

bne $v0, 5, Else

        li $v0, 4

jr $ra
```

```
# REMOVED: move $t0, $v0  <-- This line was incorrect and should be removed

li $v0, 5               # System call code for read_int
syscall                 # Read integer input. Result is in $v0.
move $a1, $v0           # Move user's input from $v0 to $a1 (keeping it safe)

la $a0, message_out     # Load address of output message
li $v0, 4               # System call code for print_string
syscall                 # Print "The integer you just inputted is:"

move $a0, $a1           # Move user's input from $a1 to $a0 for printing
li $v0, 1               # System call code for print_int
syscall                 # Print the user's input

# --- Comparison ---
li $t0, 5               # Load the constant value 5 into $t0 for comparison
bne $a1, $t0, NotEqual  # If user input ($a1) is NOT 5 ($t0), branch to NotEqual
```