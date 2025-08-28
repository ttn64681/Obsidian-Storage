# Big O and Data Structures
Big O - notation used to measure an algorithm's efficiency as input size (n) grows.
1. Time Complexity: How long does algo take as input (n) grows bigger?
2. Space Complexity: How much mem does algo use as input (n) grows bigger?

O(n) :
	`for item in my_list:`
O(logn) :
	``

### Data Structures: Your Toolkit 🧰

Choosing the right data structure is the most critical skill. Here are the essentials in Python, when to use them, and their "Big O" costs.

|Data Structure|Python Type|When to Use It (The "Tell")|Common Operations & Average Time Complexity|
|---|---|---|---|
|**Array / List**|`list`|You need to store an ordered collection of items.|**Access by index:** O(1) <br> **Search for value:** O(n) <br> **Insert/Delete (at end):** O(1) <br> **Insert/Delete (at beginning/middle):** O(n)|
|**Hash Map / Dictionary**|`dict`|You need fast lookups, insertions, and deletions. Think "key-value pairs" or caching previously seen values.|**Access/Insert/Delete:** O(1)|
|**Set**|`set`|You need to store unique items and check for existence very quickly.|**Check for existence/Insert/Delete:** O(1)|
|**Stack (LIFO)**|`list` (use `.append()` and `.pop()`)|"Last-In, First-Out". Think of a stack of plates. Useful for matching parentheses, backtracking, or DFS algorithms.|**Push/Pop:** O(1)|
|**Queue (FIFO)**|`collections.deque`|"First-In, First-Out". Think of a line at a store. Essential for Breadth-First Search (BFS) algorithms.|**Enqueue/Dequeue:** O(1)|
|**Linked List**|(Custom Class)|You need efficient insertions/deletions in the middle of a sequence without shifting elements (unlike a list).|**Access/Search:** O(n) <br> **Insert/Delete (at head):** O(1)|
|**Trees / Graphs**|(Custom Class)|Data has hierarchical (tree) or network (graph) relationships. Think social networks, file systems, or network routing.|Varies, but traversal is often O(V+E) where V is vertices and E is edges.|