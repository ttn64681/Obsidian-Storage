
# Bad
## Premature Coder
- seeing a problem and immediately typing 
- `for i in range(len(arr))`
- instead of actually planning and testing (via pseudocode)

## For Loop For Everything
- defaulting to nested loops for any problem
- Ask "What's the fastest search we know of?"

## Ignoring Clues in Prompt
- sorted array problem, yet treat it like a regular, unsorted list, missing huge optimization
- Mantra: "If input arr sorted, immediately think of Binary Search or Two Pointers"


# Good
## Avoid  for i in range(len(arr)): ... arr[i] ...
- instead, do
	for element in arr
	or
	for index, element in enumerate(arr)

## Avoid string concatenation in a loop 
- avoid `new_str += char`
- Strings are immutable in Python
- This creates new string in memory w/ each addition, making it an O(n^2) operation
- instead, do:
	- "".join(list_of_chars)
	- or f-strings
		- `message = f"My name is {name}"`

## Avoid recalculating values
-