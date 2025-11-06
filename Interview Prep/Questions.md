
### Congratulations on completing the evaluator!

Let's delve into your interview readiness compared to top tech companies and how to structure your coding interview preparation. See answer explanations and read the in-depth algorithm guides below!

To learn more about company-specific trends and how to prepare strategically, visit our comprehensive breakdown of [coding interview patterns](https://algo.monster/problems/stats)

and [frequently seen questions for each company](https://algo.monster/interview-guides)

.

Results

Recommended Level For

Review Answers

Question 1 out of 16

What data structure does Breadth-first search typically uses to store intermediate states?

Your Answer:**

  
Queue

**

Correct Answer:**

  
Queue

**

Breadth-first search uses a queue and Depth-first search uses a stack.

✔

Question 2 out of 16

Which algorithm is best for finding the shortest distance between two points in an unweighted graph?

Your Answer:**

  
Breadth-First Search

**

Correct Answer:**

  
Breadth-First Search

**

Technically, either depth-first search or breadth-first search can be used find the shortest distance two points in an unweighted graph.

However, in a large graph, depth-first search may go too far in the wrong direction, whereas breadth-first search will traverse the closest points first, and therefore be more efficient.

✔

Question 3 out of 16

What is the best way of checking if an element exists in a sorted array once in terms of time complexity? Select the best that applies.

Your Answer:**

  
Hash Set

**

Correct Answer:**

  
Binary Search

**

✖

Question 4 out of 16

Given a sorted array of integers and an integer called target, find the element that equals to the target and return its index. Select the correct code that fills the `___` in the given code snippet.

```python
def binary_search(arr, target):
```

```python
    left, right = 0, len(arr) - 1
```

```python
    while left ___ right:
```

```python
        mid = (left + right) // 2
```

```python
        if arr[mid] == target:
```

```python
            return mid
```

```python
        if arr[mid] < target:
```

```python
            ___ = mid + 1
```

```python
        else:
```

```python
            ___ = mid - 1
```

```python
    return -1
```

Your Answer:**

  
<=, left, right

**

Correct Answer:**

  
<=, left, right

**

We need the equality comparison to catch the edge input case of array of only one element.

If `arr[mid]` is already smaller than the target, then we should discard everything on the left by making `left = mid + 1` else we discard everything on the right.

✔

Question 5 out of 16

Which of the following is a good use case for backtracking?

Your Answer:**

  
Combinatorial problems

**

Correct Answer:**

  
Combinatorial problems

**

✔

Question 6 out of 16

Which data structure is used to implement recursion?

Your Answer:**

  
Stack

**

Correct Answer:**

  
Stack

**

✔

Question 7 out of 16

Consider the classic dynamic programming of longest increasing subsequence:

Find the length of the longest subsequence of a given sequence such that all elements of the subsequence are sorted in increasing order.

For example, the length of LIS for `[50, 3, 10, 7, 40, 80]` is `4` and LIS is `[3, 7, 40, 80]`.

What is the recurrence relation?

Your Answer:**

  
I don't know

**

Correct Answer:**

  
dp[i] = max(dp[i], dp[j] + 1) for j in 0 to i

**

✖

Question 8 out of 16

What is an advantages of top-down dynamic programming vs bottom-up dynamic programming?

Your Answer:**

  
It has better space complexity

**

Correct Answer:**

  
Order of computer subproblems does not matter

**

✖

Question 9 out of 16

What's the relationship between a tree and a graph?

Your Answer:**

  
A tree is a special graph

**

Correct Answer:**

  
A tree is a special graph

**

✔

Question 10 out of 16

Problem: Given a list of tasks and a list of requirements, compute a sequence of tasks that can be performed, such that we complete every task once while satisfying all the requirements.

Which of the following method should we use to solve this problem?

Your Answer:**

  
I don't know

**

Correct Answer:**

  
Topological Sort

**

You can read [our article](https://algo.monster/problems/topo_intro) about Topological Sort.

✖

Question 11 out of 16

You are given an array of intervals where `intervals[i] = [start_i, end_i]` represent the start and end of the `ith` interval. You need to merge all overlapping intervals and return an array of the non-overlapping intervals that cover all the intervals in the input.

Your Answer:**

  
Sort the intervals by their start time, then iterate through the sorted intervals, merging any overlapping intervals.

**

Correct Answer:**

  
Sort the intervals by their start time, then iterate through the sorted intervals, merging any overlapping intervals.

**

The correct approach to solve the problem using a greedy algorithm is to first sort the intervals by their start time. Then, iterate through the sorted intervals and merge any overlapping intervals. This ensures that you can easily determine if the current interval overlaps with the previous one and merge them accordingly.

✔

Question 12 out of 16

Which of the following uses divide and conquer strategy?

Your Answer:**

  
Merge Sort

**

Correct Answer:**

  
Merge Sort

**

✔

Question 13 out of 16

What's the output of running the following function using input `[30, 20, 10, 100, 33, 12]`?

```python
def fun(arr: List[int]) -> List[int]:
```

```python
    import heapq
```

```python
    heapq.heapify(arr)
```

```python
    res = []
```

```python
    for i in range(3):
```

```python
        res.append(heapq.heappop(arr))
```

```python
    return res
```

Your Answer:**

  
[10, 12, 20]

**

Correct Answer:**

  
[10, 12, 20]

**

The function returns the top 3 smallest element using a heap.

✔

Question 14 out of 16

A heap is a ...?

Your Answer:**

  
Tree

**

Correct Answer:**

  
Tree

**

A heap is a tree with special "heap properties" - almost complete and each node's value is smaller/larger than its parent's value (min/max heap).

✔

Question 15 out of 16

Which two pointer techniques do you use to check if a string is a palindrome?

Your Answer:**

  
Two pointers moving in opposite direction

**

Correct Answer:**

  
Two pointers moving in opposite direction

**

✔

Question 16 out of 16

What does the following code do?

```python
def f(arr1, arr2):
```

```python
  i, j = 0, 0
```

```python
  new_arr = []
```

```python
  while i < len(arr1) and j < len(arr2):
```

```python
      if arr1[i] < arr2[j]:
```

```python
          new_arr.append(arr1[i])
```

```python
          i += 1
```

```python
      else:
```

```python
          new_arr.append(arr2[j])
```

```python
          j += 1
```

```python
  new_arr.extend(arr1[i:])
```

```python
  new_arr.extend(arr2[j:])
```

```python
  return new_arr
```

Your Answer:**

  
Find the intersection of two arrays.

**

Correct Answer:**

  
Merge two sorted arrays.

**

✖