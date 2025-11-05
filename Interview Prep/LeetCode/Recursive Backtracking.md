Basic Steps: "Performing DFS on a decision tree"
- **CHOOSE:** 
	- *Make decisions*
- **EXPLORE:** 
	- *Recursion on decision (move on after 1 decision)*
		- recursive function (DFS)
	- *Keep going until Base Case*
		- recursive function keeps exploring decisions based on previous decision
- **UNCHOOSE:** 
	- You then *Undo Decisions* after base case is hit

Intent: 
- Exhaustive Search
- Basically definition of Brute Search

Key words:
- want to consider "all" solutions
	- if you want to see all, you can use backtracking to generate ALL the solutions
- "All" subset (aka power set)

Complexity:
- Time:
	- O( n * recursive func)
	- recursive func -> 
		- "how many possible decisions can i make to get to the next step?"
		- if 2, then it's binary 2^m
			- m - length of each step (e.g. # elements in array, # characters in a word)
		- if 4, then it's 4^m
	- O( n * 2^m)
- Space:
	- maximum depth of recursion call stack + space complexity
		- recursion call stack -> O(n)
		- space complexity -> O(m)
	- O(n + m)

Key Distinction:
- Find All vs Find One
- If Find ALL Solutions (e.g., subsets, permutations, combinations)
	- Keep track of global List of results
		- (backtrack/recursive func returns nothing)
	- add copy of currentPath to results list
- If Find ONE Solution (word search, sudoku solver)
	- Return true once base case is hit (found valid solution)
	- Check if backtrack/recursive func returns true, if so, return true up the call stack

Tips:
- 

Example : Subsets 
- Find ALL
- binary decision tree O(2^n)
- indices 0-(n-1) to represent numbers 1-n
- 2 global lists
	- Result: list of final full answer
	- Solution: 
- Time complexity, for each step you make 2 decisions, so 2^n where n is amount of elements in array.
Answer:
```

```

Example : Word Search
- Find ONE
- 4-way decision tree O(4^L)
- since you can't revisit a previously tracked letter, it's basically a 3-way decision tree O(3^L)
Answer:
```
class Solution:

def exist(self, board: List[List[str]], word: str) -> bool:

ROW, COL = len(board), len(board[0])

w = len(word) # Space O(1)

  

def isInBounds(r,c):

if (r<0 or r>=ROW or c<0 or c>=COL):

return False

  

def dfs(r, c, i): # O(3^w) (w - word length)

if (i == w): # finished finding all chars in word

print("Complete (i==n)!")

return True

  

# If char not found, return False

if (isInBounds(r,c) == False or

board[r][c] == "#"): # if letter already read

print("Not Found... indexOutOfBounds")

return False

elif (board[r][c] != word[i]):

print("Not Found... ", board[r][c])

return False

# Else if char is found, mark it and continue

temp = board[r][c] # Space O(1)

board[r][c] = "#" # mark as read ("#")

print("Found! ", temp)

  

paths = dfs(r+1,c,i+1) or\

dfs(r-1,c,i+1) or\

dfs(r,c+1,i+1) or\

dfs(r,c-1,i+1)

board[r][c] = temp # unmark to original letter

return paths

  

for r in range(ROW): # Time O(m * n)

for c in range(COL):

# whenever first letter of word found, do dfs

if board[r][c] == word[0]:

res = dfs(r,c,0) # Time O(3^w)

if res:

print(board)

return True # if found, return True

return False

  

# Overall Time O(m * n * 3^w)

# Overall Space O()
```

Example : Binary Paths 
- 
Answer:
```

```



