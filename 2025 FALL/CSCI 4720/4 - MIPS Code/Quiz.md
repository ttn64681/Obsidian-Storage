
Q1:
Provide the the type and hexadecimal representation of following instruction (Machine code):    **sw $t1, 32($t2)**

i) Type (first answer box, only the char(s), e.g. R )

- sw uses immediate value -> I type (eye type)
- format:
	- `opcode (6 bits) | rs (5 bits) | rt (5 bits) | immediate (16 bits)`
- Field breakdown:
	- `The instruction ` sw $t1, 32($ t2) ` maps to the format ` sw rt, offset(rs) `.`
		- `opcode`: The operation code for `sw` -> *43 (in decimal) -> 101011 (6bit binary)*
		- `rt` (source register): `$t1`
		- `rs` (base address register): `$t2`
		- `immediate` (offset): `32`

ii) Hexadecimal representation (second answer box, put only the hexadecimal value without any space and in the exact bit size of the instruction type, e.g. 01A54321 - do **NOT** put the **0x** before your **HEX** answer & make sure that all alphabets(A,B,C,D,E) in your **HEX** answer(if any) should be **CAPITAL/UPPERCASE**)