```table-of-contents
```
# Lab 1: Exercises
- slice
	- []
- type cast to int
	- int()
- floor div, exponent, square-root
	- //
	- **
	- \*\*.5
- add to set
	- add()
- add to dict
	- dict[""] = 85

# Lab 2: Matrix Mult, Dot Product, Eigenvalues, Back-Subst 
- Dot product b/w vectors u and v
	- you canNOT do operations on vectors of different dimensions/sizes
	- Ex: <1,2> <3,4>
		- *1x3 + 2x4*
		- **sum(u[i] * v[i])**

- Matrix Addition
	- you canNOT do add/subt on matrices of DIFF dimensions/sizes
	- add each entry in matrix A w/ each entry in matrix B and store in matrix C

- Matrix Transpose
	- switches rows with columns
		- for each entry is t_A (which is opposite dimensions of A):
			- t_A\[i]\[j] = A\[j]\[i]
![[Tranposed Matrix.png]]


- Matrix Multiplication
	- CAN do if 1st matrix's col size == 2nd matrix's row size
		- Ex: 3x2 \* 2x3 --> valid
```python
# matrix multiplication
for i in range(rowsA):
	for j in range(colsB):
		sum = 0
		for k in range(colsA):
			sum += A[i][k] * B[k][j]
```
- the order is **colA++  at rowA**   *times*   **rowB++  at colB**, simultaneously

- Solve Eigenvalues
	- By hand:
		- det(A * lambda I) = 0
```
A = [1 -1]
    [2  4]
det (1-λ -1) = (0)
    (2  4-λ)   (0)
    
    = (1-λ)(4-λ)+(-1)(2) = 0
    = λ^2 + 5λ + 6 = 0
    -> λ1=2, λ2=3
```
- 
	- By code:
		- Theory:
			- Solve lambda^2 - T\*lambda + D = 0
			- Where T (Trace) = A\[0]\[0] + A\[1]\[1]
			- Where D (Determinant) = A\[0]\[0]\*A\[1]\[1] - A\[0]\[1]\*A\[1]\[0]
		- find lambda 1 and 2 via quadratic formula

- Back substitution for linear system
	- solves Ux = b 
		- U is matrix
		- x is vector of variables (x1, ..., xn)
		- b is vector of constants
	- U is square
	- times the x vector on the main diagonal of U
	- = to constants b
		- how to find: constant - (U )
```python
"""
[30 pts] Solve Ux = b where U is upper triangular.
Algorithm:
Start from the bottom row (n-1).
x[i] = (b[i] - sum(U[i][j] * x[j])) / U[i][i]
"""
n = len(b)
x = [0.0] * n # x is same size as b, since U is square (nxn)
for i in range(n-1, -1, -1):
	sum = 0
	for j in range(n-1, -1, -1):
		sum += U[i][j] * x[j]
	x[i] = (b[i] - sum) / U[i][i]
return x
```

U = [[3,2,1],
[0,2,-2],
[0,0,5]]
b = [2,6,-10]

[0.6666666666666666, 1.0, -2.0]

# Lab 3: Distance Matrix, SVD, Cosine Similarity

## Broadcasting + Distance Matrix
### 1. The Starting Point: (2, 2)
Your original matrix X looks like this:
X=[(x0​,y0​)(x1​,y1​)​]

- **Row 0:** Point 0
- **Row 1:** Point 1
### 2. The Transformation: (2, 1, 2) vs (1, 2, 2)
When you add `np.newaxis`, you aren't changing the data, you are changing the **address** of the data.

**`A = X[:, np.newaxis, :]` → Shape (2, 1, 2)** Think of this as **two separate sheets** (Depth=2). Each sheet has **1 row** and **2 columns**.

- Sheet 0: `[(x_0, y_0)]`
- Sheet 1: `[(x_1, y_1)]`
- _The "second row" isn't erased; it was moved/stretched to the "second sheet"._

### 3. The "Magic" of Broadcasting (The Subtraction)

When you do `A - B`, NumPy sees the shapes (2,1,2) and (1,2,2). It stretches the `1`s to match the bigger numbers.

#### Step A: Stretch `A` (The Vertical Stretch)

`A` has only 1 row, but it needs to match `B`'s 2 rows. It **duplicates its row** downward.

- Sheet 0 becomes: `[(x_0, y_0), (x_0, y_0)]`
    
- Sheet 1 becomes: `[(x_1, y_1), (x_1, y_1)]`
    

#### Step B: Stretch `B` (The Depth Stretch)

`B` has only 1 sheet, but it needs to match `A`'s 2 sheets. It **duplicates the whole sheet** into a second layer.

- Sheet 0: `[(x_0, y_0), (x_1, y_1)]`
    
- Sheet 1: `[(x_0, y_0), (x_1, y_1)]`
    

### 4. The Final Calculation (The "NxNxK" Tensor)
Now that they both look like (2,2,2), they subtract element-wise:
**Sheet 0 (Differences relative to P0​):**
```
[(x0​,y0​)    [(x0​,y0​)    [(P0​−P0​)
 (x0​,y0​)​] −  (x1​,y1​)​] =  (P0​−P1​)​]
````
**Sheet 1 (Differences relative to P1​):**
```
[(x1​,y1​)    [(x0​,y0​)    [(P1​−P0​)
 (x1​,y1​)​] −  (x1​,y1​)​] =  (P1​−P1​)​]
```
NxNxK = 2sheets by 2rows by 2 columns

### 5. The Mathematical "Collapse"
To turn those (x,y,z) differences into one distance number, we use the Euclidean distance formula:

d= sqrt ( Δx2+Δy2+Δz2 )

In NumPy, we do this in two steps that "eat" the 3rd axis:
1. **Square everything:** `disps**2` (Still N,N,K)
2. **Sum along the K axis:** This is the "collapsing" step.
	1. this sums up on axis 2, which is the columns, so it sums every column for each row 
	2. [(x0 + y0), [x1 + y1])
	3. this leaves a NxNx1, and in NumPy, the x1 gets dropped
3. **Square root:** The final touch.

- If you _want_ it to stay as **(2, 2, 1)**, you can tell NumPy: `np.sum(disps**2, axis=2, keepdims=True)`

<hr>


2. Distance Matrix:
- A **_distance matrix_** is a table that shows the _distance_ between pairs of objects. For example, in the table below we can see a distance of 16 between A and B, of 47 between A and C, and so on. By definition, an object’s distance from itself, which is shown in the _main diagonal_ of the table, is 0. Distance matrices are sometimes called _dissimilarity matrices_.
- ![](https://mlkeww00jjj8.i.optimole.com/cb:_P4T.27e/w:446/h:46/q:mauto/f:best/https://www.displayr.com/wp-content/uploads/2018/04/Screen-Shot-2018-04-12-at-4.21.53-pm.png)
-  ![How to create a distance matrix](https://mlkeww00jjj8.i.optimole.com/cb:_P4T.27e/w:467/h:264/q:mauto/f:best/https://www.displayr.com/wp-content/uploads/2018/04/How-to-create-a-distance-matrix.png) 

	1. get difference tensor of NxNxK, getting displacement
		- A[]
			Row 0: [[10, 20]]
			Row 1: [[30, 40]]
	2. collapse K (which is just the [x,y] inside, so you get a singular value for each cell in the 2x2 grid.
	- 
	```python
	
	disps = X[:,np.newaxis,:] - X[np.newaxis,:,:] # gives NxNxK tensor of differences b/w 
	dist_sq = disps**2
	# sum on axis 2 (which is the columns, so inside every [x,y] coord)
	dists = np.sqrt(np.sum(dist_sq, axis=2)) 
	return dists
	```
	1. 


- Numpy Mean Numpy Standard Deviation
	- 
- Implement Cosine Similarity given Cosine Similarity function
	- **A.B / ||A|| * ||B||**


## SVD
- SVD - data reduction tool / dimensionality reduction tool
	- 1 of most important algorithms in linear algebra to make money
	- data-driven generalization of the Fourier transform (FFT)
	- 1 most useful transformations in math based on cos/sin expansions to approx functions, etc.
	- tailors a coord / transformation system based on info we have
		- INTO simple/interpretable, understandable model that you can build models on
		- scalable, can build onto very large datasets (Google)

	- you can use it for solving linear matrix systems Ax = b
		- non square A
		- regression
		- PCA - principal component analysis
			- taking high D matrix and distill it down to the principal/key features used to interpret and model that data

	- used In Google Page ranking
	- used In FaceBook face recognition
	- used In recommender systems in Amazon/Netflix

### SVD Math
- Computer matrix **`X = UΣV^T`**
	- **U** and **V** are **orthogonal matrices**
		- UU^T = Identity mxm
		- VV^T = Identity mxm
	- **Σ** is a **diagonal matrix**
		- nonnegative & 
		- hierarchically ordered in **decreasing magnitude**
			- *sigma1 ≥ sigma2 ≥ ... ≥ sigmam ≥ 0*

- WHAT THIS MEANS:
	- each column of U, which corresponds to each sigma,
	- and each column of V, which corresponds to each sigma
	- are somehow **decreasingly less important than the prior columns in describing the info of the data matrix X**

- <span style="background:#fff88f">the relative importance of these columns of U and V are given by the "Corresponding Singular Value" within Σ</span>

- **U - left singular values**
- **Σ - singular values**
- **V - right singular values**

- we only approximate X by the first few values of sigma

- V_i represents the time series (in the case of a physics flow model)
	- in case of face images, first col of V^T tells mixture of columns with U that adds up to X1

- **the SVD is unique and guaranteed to exist**


Ex Problem X:
- each vector column of N can represent a skinny version of a singular image
- if an image was 100MB, those 100MB of pixels are stretched into a singular column, x_1
- say each column is 1,000,000 pixels

**`X = UΣV^T`**
- U is NxN square matrix
	- each col u_i are the "eigen" faces
	- u1 col is hierarchically more important than u2, in describing the variants in the columns of X
	- U is same size as vector x_i
- Σ is diagonal matrix of size MxM
	- since only M columns in X
	- everything else below will be 0
- V^T = vector size M

## Cosine Similarity:
### A. Dot Product on Vector
- calculate dot product of query vector and Database matrix

### B. Normalize Distances of Vector and Dataset
- find normalized distance of q and normalized distances of D
### C. The Formula: `dot_products / (norm_q * norms_D)` 
This is the "Standardization" step for angles. By dividing the dot product by the lengths, you are "stripping away" the size of the vectors. You are left with a value between **-1 and 1**:
- **1.0:** The vectors are pointing in the exact same direction.
- **0.0:** The vectors are perpendicular (they have nothing in common).
- **-1.0:** They are pointing in opposite directions.

### D . The Winner: `np.argmax(similarities)`
- This just finds the index of the highest number in your list of 1,000 similarities.
- To get the _value_ of the highest similarity: `similarities[np.argmax(similarities)]`
- To get the _top k indices_: `np.argsort(similarities)[-k:]` (for ascending order, reverse for top)
- To get the _top k values_: `similarities[np.argsort(similarities)[-k:]]`



# Lab 4: 
- penguins dataset