```table-of-contents
```
# Intro
- Focus on linear systems and determinants
- Links solutions of linear systems to intersections of lines or planes

- efficient desc of large data sets using feature vectors
- Constructing low-dimensional approximations of the available data thru projection and least squares

## Why Linear Algebra
- Under the hood of every algorithm:
	- **Regression:** Minimizing squared errors (Linear Algebra)
		- modeling relationship to **predict value of dependent var based on independent**
	- **PCA:** Finding principal axes (Linear Algebra)
		- simplifies complex datasets by transforming them into a **lower-dimensional space**, which can help in *visualization, noise reduction, and improving the efficiency of machine learning algorithms*
	- **Neural Networks:** Matrix multiplication (Linear Algebra)

- **NumPy / PyTorch / TensorFlow handle the math**

### 3 Fundamental Metrics
- *Scalar*
	- single number (x in R)
	- Ex: Learning rate, bias term
- *Vector (1-D Tensor):*
	- **an Array or list of attributes**
	- Ordered list of nums (x in R^n)
	- Ex: Single row in database
- *Matrix (2-D Tensor):*
	- A 2D grid of nums (A in R^(mxn))
	- Ex: An Excel sheet (Samples x Features)
		- ***samples = x***
		- ***features = y***

![[Drawing 2026-01-20 13.24.50.excalidraw]]

### High-Dimensional Metrics
- Tensor:
	- Matrices of N-dimensions
	- **Rank-3 Tensor:** Time series data
		(Rows x Cols x Time)
	- **Rank-4 Tensor:** Image Batch
		(Batch Size x Height x Width x Color)
		- Each color/pixel is split into r,g,b

# Vectors:
- an array or list of attributes

## Data point:
- represented using vectors or collection of vectors (matrix)
- Ex:
	- A "House" vector: [2000,3,500]
	- 2,000 sq. ft, 3 beds, $500k

-  a collection of vectors is matrix

## Vector operations:
- Vector Addition
- Vector Subtraction
- Scalar Multiplication

### Dot Product:
- math def: 
	- a x b
	- helpful for vector multiplication
- geometric def:
	- ->a x ->b = |->a| |->b| cosO

### Cosine Similarity
- tells us which direction 
- Range: -1 (Opposite) to 1 (Identical)
	- 0 = Perpendicular
	- *helpful for recommendation systems*

## Vector Norm
- A function that measures the **size** or **magnitude** of a vector by *quantifying its length from the origin*
- The vector norm |x|\_p for p = 1,2,... is defined as:
	- |x|\_p = 
- Properties:
	- non-neg |x| > 0 when x≠0
	- Definite |x| = 0 iff x = 0
	- Triangle ineq |x+y| ≤ |x| + |y|

- L1-norm: p=1
	- dist b/w two city blocks
- L2-norm: p=2
	- euclidean distance
- L3-norm
- L4-norm
- L(inf)-norm

## Transformation
- y = Ax
- Input: Vector x
- Function: Matrix A
- Output: Vector y

- Matrices only perform Linear Transformations:
	- Rotate, Scale, Shear, Reflect

Indentity
Reflection
Translation
Scale
Rotation
Shear-X
Shear-Y

## Matrix Multiplication
- Inner dimensions must match
- (mxn) x (nxp) = (m x p)
- Application - 
	- Neural Networks: a chain of matrix multiplications
	- Layer\_2(Layer1( )) 

- **Identity Matrix (I)**
	- Square matrix w/ 1s on diagonal, 0s elsewhere
	- **A x I = A**
- **Inverse MAtrix (A^-1)**
	- **A x A^-1 = I**
	- A square matrix that does not have a matrix inverse is a Singular Matrix

## Solving Systems of Equations
- The problem: Ax = b
- A: Data/Features
- x: Weights (Unknown)
- b: Targets/Labels 

- Solution: x = A^-1 b
- Inverting large matrices is slow/unstable
- Use approximation algorithm (Gradient Descent)


# Big Data
- **data that's high-dimensional**
	- high volume
- as dimensions increase, data becomes sparse
	- "More features aren't always better"
	- **Distance metrics (Euclidean) lose meaning**
	- **Models overfit (memorizing noise instead of signal)**

- you can have 2 points similar in one dimension (x and z), but not in another 2 dimensions (y and z)
- that's why more dimensions make it harder to define similarity
	- this causes overfitting, since it's hard to find similarities, and instead memorize
		- model underperforms/fails

## What is Information?
- in Linear Algebra, information ~= Variance.
- If a feature (column) never changes (variance = 0), it tells us nothing
- If 2 features are perfectly correlated, one is redundant
- **Rank** helps us measure this

## Matrix Rank
- **Rank:** the num of *linearly independent* rows or cols
- **Linear Independence:**
	- a set of vectors in Linearly Independent if *no vector can be built from a combination of the others*
- How do you find it?

- the num of non-zero rows in its **row echelon form**, which corresponds to the number of picots
	- row echelon form of matrix represents 0 vectors/rows
	- 0 rows at bottom of matrix
	- for each col/feature try to get pivots, that would be the non-zero val, and 
	- reduce it to 1s and 0s
- How do you transform a matrix into it's row echelon form?

## Revisiting Solving Linear Systems (Gaussian Elimination)
2x + 4y - 2z = 14
x + 3y + z = 11
3x + 2y + z = 11

->
(Matrix/Augmented form)

| 2   | 4   | -2  | 13  |
| --- | --- | --- | --- |
| 1   | 3   | 1   | 11  |
| 3   | 2   | 1   | 11  |
- swap rows
- Create the first pivot:
	- R1 <-> R2
->

| *1*   | *3*   | *1*   | *11*  |
| --- | --- | --- | --- |
| *2*   | *4*   | *-2*  | *13*  |
| 3   | 2   | 1   | 11  |
- Eliminate below the first pivot:
	- R2 <- R2 - 2R1
	- R3 <- R3 - 3R1
->

| 1     | 3      | 1      | 11     |
| ----- | ------ | ------ | ------ |
| **0** | **-2** | **-4** | **-9** |
| **0**     | **-7**     | **-2**     | **-22**    |
- Create the second pivot:
	- R2 <- -½ R2

| 1     | 3     | 1     | 11      |
| ----- | ----- | ----- | ------- |
| **0** | **1** | **2** | **4.5** |
| 0     | -7    | -2    | -22     |
- Eliminate below the second pivot:
	- R3 <- R3 + 7R2
->

| 1     | 3     | 1     | 11      |
| ----- | ----- | ----- | ------- |
| **0** | **1** | **2** | **4.5** |
| 0     | 0     | 12    | 6       |
- **This is our Row Echelon Form** 
- Row echelon form conditions:
	- All rows consisting entirely of zeros are at bottom of matrix



- From the augmented matrix,
	- x + 3y + z = 11
	- y + 2z = 4.5
	- 12z = 6

- Use back-substitution to find the values of **x,y,z**

## How does Row Echelon Form help in calculating Rank?
### Row Echelon Transformation
- R2 <- R2 - 4R1
- R3 <- R3 - 5R1
- R3 <- R3 - R2

A = 

| 1   | 2   | 3   |
| --- | --- | --- |
| 4   | 5   | 6   |
| 5   | 7   | 9   |
- which row(s) are dependent on other rows?
- After simplification, we discover that **one of the rows is a linear combination of the others, making it redundant**. (579)
- after you simplify them to row echelon transformation,
	- you discover there are only 2 rows that are linearly independent, so the **rank is 2**.
- This reveals the **true intrinsic dimensionality** of the data, indicating the effective number of independent "features" or "dimensions."
	- Thus, we have reduces noise and redundancy
	- reducing overfitting and computational cost
->

| 1   | 2   | 3   |
| --- | --- | --- |
| 0   | -3  | -6  |
| 0   | -3  | 9   |
->

| 1   | 2   | 3   |
| --- | --- | --- |
| 0   | -3  | -6  |
| 0   | 0   | 0   |

# Eigenvalues & Eigenvalues
- Eigen roughly translates to "own" or characteristics
- Eigenvalues and eigenvectors are only for square matrices
- Eigenvectors are by definition non-zero
- Eigenvalues may be equal to zero

- Let A be an nxn matrix
	- an Eigenvector of A is a **nonzero vector** *v* in R^n such that Av = λv, for some scalar λ
	- An Eigenvalue of A is a scalar *λ* such that the equation Av = λv has a nontrivial solution
- If Av = λv for vA = 0, we say that λ is the eigenvalue for v, and that v is an eigenvector for λ.

- for a matrix, it could have eigenvalues (not always), but if you do, you also have eigenvectors
- for a problem, you'd be given just the matrix, and from that you have to find the eigenvalues and eigenvectors
- you calc this by doing the equation Av = λv

- They identify _what those principal independent dimensions are_ (eigenvectors) and _how much variance each dimension accounts for_ (eigenvalues). This is crucial for reducing high-dimensional data by keeping only the eigenvectors associated with the largest eigenvalues, effectively reducing noise and redundancy while retaining the most important information.

## Finding Eigenvalues & Eigenvectors of a Matrix
- consider the matrix and vectors
- A =
[2 2]
[-4 8]
- v =
[1]
[1]
- w = 
[2]
[1]

- Av = λv
- 



- Consider Matrix A = 

| 4   | 1   |
| --- | --- |
| 2   | 3   |
- Av = λv => (A-λI)v = 0
- For a non-zero vector v to exist, the matrix (A - λI) must be Singular (non-inevitable), i.e., det(A - λI) = 0

Matrix A = 

| 4   | 1   |
| --- | --- |
| 2   | 3   
,
A - λI = 

| 4 - λ | 1     |
| ----- | ----- |
| 2     | 3 - λ |
- det(A - λI) = (4 - λ) (3 - λ) - (1) (2) = 0
	- λ^2 -7λ + 12-2 = 0
	- λ^2 - 7λ + 10 = 0
	- (λ-5)(λ-2 = 0
	- λ1 = 5, λ2 = 2

- Finding v :
	- For λi = 5,
```
[-1 1] [x]   [0]
[2 -2] [y] = [0]
```

```
-x + y = 0 }
2x -2y = 0 } -> y = -2x
```

- Check if the product is a scalar multiple of the vector
	- Av 


- Fail-safe identification - face identification
- instead of having all features, if you just get the eigenvectors and eigenvalues, the most important features(columns)/pixels of the face, then you can recognize the face

- basically we covered today the issue with high dimensionality, so we need to reduce the features and dimensions
- we do this efficiently by identifying the important rows/cols via row echelon form
	- since data is just matrices

- using eigenvalues, we generate eigenvectors, we generate "Principal Axes" of the data
- Useful in PCA, SVD

# Singular Value Decomposition (SVD)
- SVD works on any matrix A in R^(mxn)
- It is the foundation of PCA (Principal Component Analysis)
- Image Compression
- Recommender Systems
- Denoising Data

## Anatomy of SVD
- A = U ∑ V^T
	- A (mxn): original data
	- U (mxm): "Left Singular Vectors." (Orthonormal).
		- Describes the Sample Space
	- ∑ (mxn): "Singular Values" (Diagonal).
		- Describes the Strength/Importance.
	- V^T (nxn): "Right Singular Vectors." (Orthonormal).
		- Describes the Feature space

# Notes
- you can have 2 points similar in one dimension (x and z), but not in another 2 dimensions (y and z)
- that's why more dimensions make it harder to define similarity
	- this causes overfitting, since it's hard to find similarities, and instead memorize
		- model underperforms/fails


# Model Uncertainty
## Deterministic vs Stochastic Systems
**Deterministic**
- **Zero randomness; outcomes are fixed**
- Same inputs always yield the same output
- 100% predictable if initial conditions known
- Simple, rigid and efficient
**Stochastic**
- **Inherent randomness or uncertainty**
- Same inputs yield a distribution of possible outcomes
- Only probabilistic predictions
	- (e.g., averages or likelihoods)
- Complex, statistical frameworks

## Model Uncertainty
- In deterministic systems, uncertainty is a practical limitation
	- e.g. position of object given initial velocity and position
- **In stochastic systems, uncertainty is a built-in feature of reality**
	- e.g. population of country in 5 yrs

# Statistical Learning
![[statistical learning models ex.png]]
- X - independent variables (predictors)
- Y - dependent variables (response)

- We assume there is some relationship b/w Y and X = (X1,X2,...,Xp), which can be written in the general form
	- **Y = f(X) + ε**
		- f(X) - estimation function given input X
		- ε - error term
- In essence statistical learning refers to a set of approaches for estimating f

## Why estimate f?
- in many situations, a set of inputs X are available, but output Y cannot be easily obtained
	- ^Y = ^f(X)
	- **(Predicted response) = (estimation function given X)**
- Reducible and irreducible error
	- Reducible - error due to imperfections of model
		- you can reduce error by choosing better model, improving estimation technique, or getting better/more data
	- Irreducible - error that cannot be eliminated no matter what.
		- comes from noise or randomness (ε) in data itself
		- even with the true f(X), can't predict Y perfectly

# Probability
- The uncertain phenomenon of interest
- P(event) = times event occurs / total repetitions

- given sample space **Omega**, let C be collection of events, a probability measure P is a function, which maps events in C to a number b/w 0 and 1, satisfying the following axioms:
	- All probabilities are nonnegative, P(A) ≥ 0 for any event A in C
	- Probability of sample space is one, P(**Omega**) = 1
	- If events A1, A2, ... , An in C are disjoint, then prob of their union equals sum of their indiv probabilities

## Random Var
- a measurable fn X:Omega -> E mapping the sample space to a measurable space
- *function that maps an outcome from the sample space (`w`) to a real number.*
	- Consider a probability space representing 2 rolls of a 6-sided die
	- Each possible outcome can be encoded as a vector w/ 2 entries
```
w:= [w1],      w1,w2 in {1,2,3,4,5,6}
    [w2]
    
w1 = outcome 1st roll
w2 = outcome 2nd rolls
```
1. Modeling result of first roll:
	- ~a(w) := w1
		- ~a - random var that maps sample space to real number
		- this function seems to give the result of the first roll
	- the range of ~a is {1,2,3,4,5,6}
```
For ~a = 1:
	{w:~a(w) = 1} := {[1],[1],[1],[1],[1],[1]}
					 {[1],[2],[3],[4],[5],[6]}
```

# Calculating diff types of Random Vars
## Probability Mass Function (PMF)
- **Meaning:** For **discrete** random variables (like a die roll, where outcomes are distinct, countable numbers), the <span style="background:#fff88f">PMF gives the exact probability for each possible outcome.</span>
- **Point:** It allows you to visualize and calculate the likelihood of _each specific value_ a discrete random variable can take. For your `~a` (first roll of a die), the PMF would state P(`~a` =1) = 1/6, P(`~a` =2) = 1/6, etc.

- if the ~a is a discrete variable, a mathematical function to map the probability of ai,
	- p_~a (ai) = P(~a=ai)
- Properties:
	- o ≤ p_~a (ai) ≤ 1
	- Σp_~a (ai) = 1
![[PMF.png]]

## Probability Density Function (PDF)
- **Meaning:** For **continuous** random variables (e.g., height, temperature, time), the PDF describes the _relative likelihood_ for a random variable to take on a given value. You cannot get a direct probability for a single point, but rather for a range.
- **Point:** It allows you to calculate the probability that a continuous random variable falls within a certain range (by integrating the PDF over that range).
	- DOESN'T APPLY TO DICE EXAMPLE

- if the ~a is a continuous var, the function maps probability density
	- P(a-ε ≤ ~a ≤ a) = Integral_a-ε to a [f_~a(ai)]
![[PDF.png]]

## Cumulative Distribution Function (CDF)
- **Meaning:** For both discrete and continuous random variables, the CDF gives the cumulative probability that a random variable will be less than or equal to a certain value `a`.
- **Point:** It provides a complete picture of the probability distribution, showing the probability of getting _up to_ a certain value. For your `~a`, F_`~a`(3) would be P(`~a` ≤ 3) = P(`~a`=1) + P(`~a`=2) + P(`~a`=3) = 1/6 + 1/6 + 1/6 = 3/6 = 1/2.

- the function to map the probability of ~a ≤ a
	- F_~a(a) := P(~a ≤ a)
- Consider the following CDF:
![[CDF.png]]

## Expected Value
- **Point:** It represents the **long-run average** or mean of a random variable. If you were to repeat the experiment many times, the expected value is what you'd expect the average outcome to be. For a single 6-sided die roll, E[X] = (1*1/6) + (2*1/6) + ... + (6*1/6) = 3.5.

- Weighted Average where each possible outcome is multiplied by its probability
	- Discrete variable: E[X] = SUM xi \* P(xi)
	- Continuous variable: E[X] = Integral_-INF to INF [ x \* f(x) dx]
![[Expected value 6 sided die.png]]


# Characterizing Distributions
## Moments
- quantitative measures that describe the **shape and characteristics of a probability distribution** (or a set of data points).
- Different moments reveal different properties of the distribution.

- The n-th moment of a random variable is the expected value of its n-th power.
	- Let X be a random var and n in N
	- if μ_x (n) = E[X^n] exists and finite, this is n-th **moment** of X
		- 
	- 𝜇̄_x (n) = E[(X - E[X])^n] is the n-th **central moment**
		- this is the spread or deviation from avg expected value
		- This is the expected value of the _deviation of X from its mean_ (E[X]), raised to the power of `n`.

## First Moment
- Mean μ
- Measures central tendency
- Highly sensitive to outliers

## Second Moment
-  Variance sigma^2
- Measures the dispersion from mean μ
- Var(X) = E[(X -μ)^2]
	- μ is E[X]

## Third Moment
- Skewness gamma_1
- Measures the asymmetry
- gamma_1 = E[ (x-μ)^3 / sigma]
- Figure:
	- left-skewed (negative)
		- tells how flat the tail is
![[Left skew.png]]
## Fourth Moment
- Kurtosis K
- Measures the "tailedness"
- K = E[ (X-μ)^4 / sigma]
![[Kurtosis.png]]


# Notes
*   **Model Uncertainty**:
    *   **Deterministic Systems**: Zero randomness, fixed outcomes, 100% predictable.
    *   **Stochastic Systems**: Inherent randomness, outcomes are distributions, only probabilistic predictions.
    *   Uncertainty is a practical limit in deterministic, a built-in feature in stochastic.
*   **Statistical Learning**:
    *   Relationship: `Y = f(X) + ε` (response = estimation function + error).
    *   **Reducible Error**: Can be reduced by improving the model, estimation, or data.
    *   **Irreducible Error**: Cannot be eliminated; comes from inherent noise (`ε`).
*   **Probability**:
    *   `P(event) = times event occurs / total repetitions`.
    *   Axioms: Nonnegative `P(A) ≥ 0`, `P(Omega) = 1`, disjoint union `P(∪Aᵢ) = ΣP(Aᵢ)`.
*   **Random Variable (`~a` or `X`)**:
    *   A function mapping outcomes from a sample space (`w`) to real numbers.
    *   Example: `~a(w) := w1` (maps two-roll outcome `w` to the first roll `w1`).
*   **Probability Mass Function (PMF)**:
    *   For **discrete** random variables.
    *   `p_~a(aᵢ) = P(~a=aᵢ)`: Gives the exact probability of each specific outcome.
    *   Properties: `0 ≤ p ≤ 1`, `Σp = 1`.
*   **Probability Density Function (PDF)**:
    *   For **continuous** random variables.
    *   `f_~a(a)`: Describes relative likelihood; probability is found by integrating over a range.
*   **Cumulative Distribution Function (CDF)**:
    *   For both discrete and continuous variables.
    *   `F_~a(a) := P(~a ≤ a)`: Gives the cumulative probability of `~a` being less than or equal to `a`.
*   **Expected Value (`E[X]`)**:
    *   The **long-run average** or mean of a random variable.
    *   Weighted average: `ΣxᵢP(xᵢ)` for discrete, `∫x f(x) dx` for continuous.
*   **Moments**: Quantitative measures describing the **shape and characteristics** of a distribution.
    *   **n-th Moment**: `μ_x(n) = E[X^n]`.
    *   **n-th Central Moment**: `𝜇̄_x(n) = E[(X - E[X])^n]`. Measures deviation from the mean.
*   **First Moment (n=1)**: **Mean (μ)**; measures central tendency.
*   **Second Moment (n=2)**: **Variance (σ²)**; measures dispersion from the mean.
*   **Third Moment (n=3)**: **Skewness (γ₁)**; measures asymmetry.
*   **Fourth Moment (n=4)**: **Kurtosis (K)**; measures "tailedness" (peakedness/heavy tails).

**In essence**: You learn about Model Uncertainty to understand _why_ we need these tools. Then, Probability and Random Variables provide the _framework_ to represent uncertain events numerically. PMF/PDF/CDF are the _detailed maps_ of how probabilities are distributed. Finally, Expected Value and Moments are the _summary statistics_ that help you quickly grasp the center, spread, and shape of these probability distributions, which is vital for analysis and prediction in statistical learning



# Intro


μ - sample mean of data
## Central Limit Theorem (CLT)
- **n increase, sample means distrib --> normal distrib (bell-shape)**
- sampling distrib of sample means approaches a normal distrib as sample size (n )gets larger
- Independent of distrib of population

# Variance vs Covariance
- Variance measures variation (spread) of single random var
	- random var - could be a feature
	- variance shows us how far it is from mean
- Covariance is a measure of how much 2 random vars vary together

## Covariance Matrix
- a square matrix Ci,j = sigma(xi,xj) where C in R^dxd , d num of random vars (features)
- Symmetrical
- The diagonal entries of the covariance matrix are the variances
```
Covariance Matrix =
[*sig(x,x)* sig(x,y)]
[sig(y,x) *sig(y,y)*]

These are indeed the variances: `Var(x)` and `Var(y)`.
```


## SVD (Singular Value Decomposition)
- SVD is a powerful matrix factorization technique that decomposes any rectangular matrix `A` into three other matrices:  
	`A = U Σ V^T`

**Point/Importance of SVD:**  
SVD is incredibly useful in various fields like data science, image processing, and recommender systems. It allows you to:

- **Dimensionality Reduction:** By keeping only the largest singular values, you can approximate the original matrix with fewer dimensions, effectively compressing data or reducing noise (e.g., in PCA).
- **Data Compression:** Representing complex data with fewer components.
- **Feature Extraction:** Identifying the most important features in a dataset.
- **Noise Reduction:** Separating signal from noise.
## Anatomy of SVD
`A = U Σ V^T`  
Where:

- `U`: An `m x m` **orthogonal matrix** whose columns are the **left singular vectors** of A. These are the eigenvectors of `A A^T`.
- `Σ` (Sigma): An `m x n` **diagonal matrix** containing the **singular values** of A on its diagonal. The singular values (σ) are the square roots of the non-negative eigenvalues (λ) of `A^T A` (or `A A^T`), arranged in descending order.
- `V^T`: An `n x n` **orthogonal matrix** (transpose of V) whose rows are the **right singular vectors** of A. These are the eigenvectors of `A^T A`.
## Calculation in SVD

### EX:
- Consider Matrix A = 
```
[3 2 2]
[2 3-2]
```
- A^T A =
```
[3 2]
[2 3] [3 2 2]
[2-2] [2 3-2]
```
- λ1 = 25,  
- λ2=9, 
- λ3=0
	- eigenvalues
- eigenvectors =?

- σ1 = sqrt(25) = 5
- σ2 = sqrt(9) = 3
- σ3 = sqrt(0) = 0

- For U, ui = 1/σi \* Avi
- u1 =
```
1/5 *
[]
```

**Finally**
- A = U SUM(V^T)
- (2x3) = (2x2)(2x3)(3x3)



# Intro
- Python is an interpreted language
- has override operations to determine the types on-the-go

# UFuncs
- looping over millions of elements is slow
- UFuncs (Universal Functions) allow for vectorized operations on arrays, significantly faster than Python's native loops for large datasets.

## Arithmetic UFuncs
- Numpy wraps standard Python math operators  

```python
import numpy as np
x = np.array([0, 1, 2, 3]) # Initialize x as a NumPy array
y = x + 5 # Addition
z = x _2 # Multiplication
print(f"x: {x}")
print(f"x + 5: {y}")
print(f"x_ 2: {z}")
```

- Common arithmetic ufuncs include `np.add`, `np.subtract`, `np.multiply`, `np.divide`, `np.power`, `np.mod`

## Loop speed
```
import numpy as np
rng = np.random.default_rng(seed=2196)

def compute_reciprocals(values):
	output = np.empty(len(values))
	for i in range(len(values)):
		output[i] = 1.0 / values[i]
		
	return output
```

- can  `%timeit

## Aggregations
- Computes summary statistics from a large dataset
	- ex: includes `sum`, `min`, `max`, `mean`, `median`, `std` (standard deviation).
- The axis argument specifies the dimension the aggregation is performed, effectively "collapsing" that dimension
	- axis = 0: "Compute the rows"
		(Compute column statistics)
	- axis = 1: "Collapse the columns"
		()Compute row statistics)

## sum,min,max
- Python has built-in
	- sum, min, max
	- sum(x,2)
		initializes sum. to 2
	- np.sum(x,2)
		sums along axis 2

# Broadcasting
- a set of rules for applying binary UFuncs on arrays of diff sizes
- Ex:
	- Adding a scalar to an array (arr + 5)
	- The 5 is "broadcast" (stretched) to match the array shape.

## Broadcasting Rules
1. If 2 arrays differ in their # of dimensions, the shape of the one w/ fewer dimensions is PADDED w/ ones on its leading (left) side
2. If the shape of 2 arrays DON'T MATCH in any dimension, the array w/ shape equal to 1 in that dimension is stretched to match the other shape
3. If in any dimension the sizes disagree and neither is equal to 1, anerror is raised

## Ex 1: 
```python
  M = np.ones((2,3))
  a = np,arange(3)
```
- M.shape is (2,3)
- a.shape is (3)

1. whichever shape is smaller in dimensions, but a leading 1 (left)
	1. a = np.arange(1,3)

2. then copy those values and stretch it across the dimension its lacking in

## Ex 2: 
```python
  M = np.ones((3,2))
  a = np,arange(3)
```
- cannot be done
- dimension mismatch (needs a 1 in one of M's axis)

# Boolean Masks
- Using comparison ops (<, >, \==) on arrays returns a bool array

# Linear Algebra submodule
- numpy.linalg, numpy.matrix
	- linalg contains SVD
	- Dot Product: np.dot(a,b) or a@b (Python 3.5+)
	- Transpose: A.T swaps rows and cols
	- Inverse: A.I
	- eigenvalues and eigenvectors: la, v = linalf.eig(A)


# Intro - Summary Statistics
- to obtain the summary statistics:
	- central tendency (mean, median, mode, etc.)
	- dispersion and shape of dataset's distribution
		- **DataFrame.describe()**
			- for numerical data: count, mean, std, min, max, percentiles
			- for object data: count, unique, top, freq


# Groupby: split-apply-combine
- **Splitting** the data into groups based on some criteria
	- groupby() - splits data into several chunks based on param vals
- **Applying** a function to each group independently
	- Aggregation
	- Transformation
	- Filtration
- **Combining** the results in a data structure
	- 

## Apply step:
- **Aggregation:** 
	- compute a summary statistic(s) for each group
- **Transformation:** 
	- perform some group-specific computations and return a like-index object
- **Filtration:** 
	- discard some groups, according to a group-wise computation that evaluates to True or False

## Groupby:
- given animals, their class, animal order, and max_speed, what is a good key to group by?
	- *class*
		- animal order is unique, so no

- grouped = speeds.groupby("class")
- grouped['max_speed'].mean()

- speeds.groupby['class'].max()

## Passing Aggregator Functions
- combines specific statistics
- `df.groupby('key').aggregate(['min','max',np.median()])`

- can pass in dicts as param of aggregate func:
- ``df.groupby('key').aggregate( {'f1': ['min','max'], ... } )`
	- compacts dataframe query op

## Filter:
- Filtering op is *specifically for groupby operation* 
- allows you to drop data based on group properties

- *Ex:*
- `df.groupby('key').std()`
	- returns 

- *what if we only want to include std over a threshold?*
```
def filter_func(x):
	return x['f2'].std() > 4
```
- *Now we can do:*
	- **`df.groupby('key').filter(filter_func)`**

- We can shorten via lambda:
- `df.groupby('key').filter( lambda x: x['f2'].std() > 4 )` 
	- x - the dataframe from groupby

### Built-in Filtrations in Pandas:
- head(): Select the top row(s) of each group
- nth(): Select the nth row(s) of each group
- tail(): Select the bottom row(s) of each group


## Transform
- ```
  def center(x):
  	return x - x.mean()
  	
  df.groupby('key').transform(center)
  ```

- this results in type error if its columns with non numerical info
- you can select certain columns via `df.groupby.['col'].transform ` instead of .transform

## Apply:
- some ops on grouped data might not fit into aggregation, transformation, or filtration categories

```
def norm_by_data2(x):
	# x is a DataFrame of group values
	x['f1'] /= x['f2'].sum()
	return x
	
df.groupby('key').apply(norm_by_data2)
```

- only for data that needs to be flexible



# Vocab:
**describe**
- .describe() - on a df
	- bikes \[\['Berri1', 'Villeray']].describe

**groupby()**
**mean()**
- grouped = speeds.groupby("class")
- grouped['max_speed'].mean()

**filter()**
- `df.groupby('key').filter( lambda x: x['f2'].std() > 4 )` 

# Intro
- a recursive proces
- more time spent thinking than doing

# Epicycles of Analysis
1. Stating the Question
2. Exploratory Data Analysis
3. Model Building
	- goes hand-in-hand w/ interpretation
4. Interpret
5. Communicate

# 6 Types of Questions
**Data Questions**
1. Descriptive
2. Exploratory
3. Inferential
4. Predictive
5. Causal
6. Mechanistic

## 1. Descriptive
- Seeks to summarize characteristic of a set of data
- Ex:
	- proportion of males
	- mean num of servings of fresh fruits per day
	- frequency of viral illness in a set of data
- NO interpretation of result itself
## 2. Exploratory
- Analyzes data to see if patterns, trends, or relationships exist
- Often called **"hypothesis-generating" analyses**
- Looking for patterns to support proposing a hypothesis
- Ex:
	- *you find that:* individuals who ate a diet high in certain foods had fewer viral illnesses than..
	- *So, you propose hypothesis:* "Among adults, eating 5 servings is associated w/ fewer viral illnesses that year"
## 3. Inferential
- Restatement of a proposed hypothesis as a question
- Answered by analyzing a diff set of data
- Determines if an association holds in a representative sample
- Infers what is true, on average, for a population
## 4. Predictive
- Asks what types of things predict an outcome
- Less interested in what causes the outcome
- Focuses purely on what predicts the behavior or outcome
- Ex:
	- "What is possibility of x happening in future?"
## 5. Causal
- Asks whether changing one factor changes another factor
- Focuses on avg change in a population
- Often utilizes data collected in a randomized trial
- Sometimes the underlying design of the data collection allows for the question to be causal
## 6. Mechanistic
- Asks exactly how a factor leads to an outcome
- Explains the underlying mechanism
- Not the cause, but the process

# Epicycles of Question Formulation
- Establishing expectation about question

# 5 Characteristics of Good Questions
1. Of Interest

## 1. Of Interest
- Of interest to audience
- Audience depends on context and environment

## 2. Not Already Answered

## 3. Plausible Framework
- ensure grounding by using subject area knowledge and research
## 4. Answerable

## 5. Specificity
- refines plan of attack
 - directly informs what steps to take when looking at data
- leads to more interpretable answer at end of analysis


# Translating a Question into Data Analysis

## Pitfalls: Inappropriate Data
- Scenario:
## Pitfalls: Confounding Variable
- External factor that influences both the observed "cause" and "effect", making it seem like there's a direct relationship where there isn't, or masking a true relationship
- **Ex:** 
	- If you observe that people who drink more coffee also live longer, you might think coffee causes longer life. 
	- However, if coffee drinkers tend to also exercise more (the confounder), it might be the exercise, not the coffee, that's contributing to longevity.

## Pitfalls: Biased Data Collection
- Recall bias:
	- occurs when remembering past events differently when a health condition is present
- Selection bias:
	- occurs when data collection inflates the proportion of people w/ both characteristics
- Biased underlying data collection leads to uninterpretable results

## Pitfalls: 


# Case study:
- Which demographic and health characteristics identify users who are most likely to have chronic drowsiness, defined as at least one episode of drowsiness at least every other day?

# Intro
1. The Question!

- <span style="background:#fff88f">What is the main component of Data Analysis???</span>
## Questions
- **Descriptive:** *(1 feature)*
	- What is mean body mass
	- What is most prevalent gender
	- What is most common bill length
- **Exploratory:** *exploring relation between 2+ features*
	- Which species has highest body mass?
	- Is there a correlation b/w flipper length and body mass?
	- Is mean bill length of species larger than another species?
- **Inferential:** 
	- is bill length related to gender
- **Predictive**:
	- does larger body mass = larger bill length?
	- do males avg longer bill lengths than female penguins?
- **Causal:**
	- Is body mass affected by size of bill?
- **Mechanistic:**
	- Why is body mass proportional to size/depth of bill?

## What is Main Component of Data Analysis?
- <span style="background:#fff88f">DATA is the most important thing.</span>
	- without it, you cannot move forward

- Factors:
	- **Quality**:

# Data Types
- **Structured**
	- highly organized
	- can be seamlessly included in a database
	- readily searched via simple search ops
- **Unstructured**
	- devoid of any underlying structure

- **Record**
	- Data Matrix
	- Document-term Data
	- Transaction Data
- **Graph-based**
	- Relationships among objects
	- Objects that are graphs
- **Ordered**

- *In most cases, data is unstructured, and you must structure it*
	- **Data Pre-Processing**

## Structured Data
- csv, json, 

## Unstructured Data

### Challenges w/ Unstructured Data
- Compilation + Organizing it is time/energy-consuming
- Structured data is akin to Machine Language, in that:
	- it makes info much easier to be parsed by computers
- Unstructured data is often how "humans communicate" (natural language)
	- NLP's (nat lang processors)

## Record Data
- Data that consists of collection of records, each of which consists of fixed set of attributes
	- Usually stored either in flat files or in relational databases
	- Basic form of record data does not have explicit relationship among records or attributes, every record has same set of attributes

- Data Matrix:
	- Data set represented by an m by n matrix, where there are m rows, one for each object, and n cols, one for each attributes

- Document-term Data
	- Each doc becomes a 'term' vector
	- Each term is component (attribute) of the vector
	- The val of each component is the num of times the corresponding term occurs in doc

- Transaction Data:
	- A special type of record data
	- Each transaction involves a set of items
	- Can represent transaction data as record data

## Graph Data
- relationships among data
- objects that are graphs
- ex:
	- parent-child relationships:
		- web-based links / user web-history/activity

## Ordered Data
- **Sequential transaction data**
	- an extension of transaction data
	- each transaction has a time associated w/ it

| Time | Customer | Items Purchased |
| ---- | -------- | --------------- |
| t1   | C1       | ...             |
| t2   | C2       |                 |
| t2   | C3       |                 |
| t3   | C4       |                 |
| t4   | C5       |                 |
| t5   | C6       |                 |

- **Sequence data**

- **Temporal data**
	- each record is a time series

- Spatio-Temporal data
	- Have spatial attributes, such as positions or areas, in addition to other types of attributes
	- Often such measurements are collected over time, and thus, the data consists of time series at various locations

## Handling non-record data
- most algs are for record data or its variations, like transactions and matrix data
- for non-record data, 


## Data Storage and Presentation
- CSV (Comma,Separated Values)
	- standard, more generic, and useful to read and machine to interpret
	- **no specialized tools needed to read or manipulate**
		- can use excel, word, sheets, works most of time
	- using "comma" prohibits having "comma" in data format

- TSV (Tab-Separated Values)
	- **used for raw data and can be imported into and exported from spreadsheet software**
	- files are raw
	- not as human-readable
	- ...

- XML (eXtensible Markup Language)
	- **Designed to be both human- and machine-readable**
	- Data is stored in plain text format, it provides a software- and hardware- independent way of storing data
	- Easier to create data that can be shared by different applications

- RSS (Really Simple Syndication)
	- *Used to share data b/w services*
	- Format of RSS follows XML standard usage, defines the names of specific tags
	- *RSS data is small and fast loading*
	- ex:
		- want to get updates from news article page:
			- every update sends RSS feed (info from website)
			- can capture RSS feed and read it
		- when you get tweet:
			- you get notification from ...

- JSON (JavaScript Object Notation)
	- *A lightweight data-interchange format*
	- **Easy for humans to read and write**
	- **Easy for machines to parse and generate**

# Data Pre-processing
1. Cleaning
2. Integration
3. Transformation
4. Reduction


- Data in real world is often dirt or unorganized
- Indicators of dirtiness:
	- Incomplete
	- Noisy
	- Inconsistent (different metrics/units)

## Data Cleaning
- **Data Munging**
	- Convert unorganized/unstructured data to more convenient or desirable format (structured)
	- No specific one rule, No specific scientific method available
	- Done manually, automatically, or in many cases, semi-automatically
- Ex: "Add 2 dices tomatoes, three cloves of garlic, and a pinch of salt in the mix"
	- ???How would this be done automatically?

- **Handling Missing Data**
	- Due to various reasons
		  Faculty data collection
		  System or human error while storing or transferring
	- Strategies: (active research area)
		- ignoring records (dropping)
		- using global constant to fill up
		- Imputation

- **Smooth Noisy Data**
	- Data may be corrupted (inconsistent) or noise present
	- Strategies:
		- Removing outliers
		- Resolve inconsistencies systematically
## Data Collections
- Open Data
	- Public, 
	- Accessible, 
	- Described, 
	- Reusable, 
	- Complete, 
	- Timely, 
	- Managed 
	- post-release
- Examples of Sources (Open Data)
	- Data.gov, 
		- Gov
	- HHS Open Data
		- Health
	- openBIGdata.org
	- Datasets at the Library of Congress
	- Kaggle
		- diff versions of Open Datasets and research/analysis

	- MIMIC 
		- dataset for medical patient data
		- MIMIC v3
		- MIMIC v4
			- constantly updated/maintained

- Social Media Data
	- API provided by the companies to researchers and developers
	- goldmine for collecting data to analyze for research or marketing purposes

# Review
- Stopped at Data cleaning

-  **Data Munging**
	- converting unorganized/unstructured data to structured
	- no scientific method
- *Handling Missing Data*
	- Strategies: 
		- dropping records
		- using global constant to fill up
			- fill with mean val
		- imputation, etc.
			- learn from vals and impute them

- This time, continue Data Cleaning process

# Intro
## Smooth Noisy Data
- data my be corrupted/inconsistent or noise present
- Strategies:
	- Removing outliers
	- resolve inconsistencies systematically

- Sometimes, outliers are important:
	- identifying RARE occurrences
	- and you want to learn the outlier 'patterns'

	- in data mining tasks, it is important
	- for normal data analysis, its not important

# Data Pre-Processing
- Cleaning
- Integration
- Transformation
- Reduction

## Data Integration
- only relevant for multiple data sources
- combines data from multiple sources into a coherent storage place (e.g., a single file or a database)
- schema integration, e.g., A.cust_id and B.cust_number
- Combining of metadata from diff sources

- **Detect and resolve data value conflicts**
	- diff representations or different scales/metrics
- **Address redundant data in data integration**
	- *Redundant data is commonly generated in the process of integrating multiple databases*
		- Same attribute with different names in different databases
		- "Derived" attributes
	- **Correlation analysis may detect instances of redundant data**


## Data Transformation
- Generalization
- Attribute
- Feature Creation
- 

### 1. Generalization
- Concept hierarchy climbing
	- A way to organize concepts defined in a knowledge domain
	- Multilevel organization of concepts
- **Ex: categorical variables**
-  ![[Drawing 2026-02-19 13.34.15.excalidraw]]
### 2. Discretization and Binarization
- **Discretization is the process of converting a continuous attribute into an original attribute**
- **Binarization maps a continuous or categorical attribute into one or more binary vars**

### 3. Attribute Transformation
- A func that **maps the entire set of vals** of a given attribute **to a new set of replacement vals**
	- **Simple funcs:** x^k, logx, e^x, |x|
	- **Normalization:**
		- Refers to various techniques to adjust to differences among attributes in terms of frequency of occurrence, mean, variance, range
		- Ex: Min-max
			- say age is 10-30
			- income 10k-50k
			- *if we normalize min to be 0, max to be 10, you **standardize** the values*
		- Z-score (standardization)
	- Decimal Scaling

### 4. Feature Creation
- create new attributes that can capture the important info in a data set much more efficiently than the original attributes

- 3 General Methods:
	- Feature extraction
		- Ex: Extracting edges from images
			- could use the features as something to train the model to learn
	- Feature Construction
		- Combining multiple features to create new features
	- Mapping data to new space
		- Ex: Fourier and wavelet analysis


## Data Reduction
- Obtains reduced representation of data set that is much smaller in volume yet produces same (or almost) analytical results
- Strategies:
	- Data Cube Aggregation
	- Dimensionality Reduction
	- Numerosity Reduction
	- Discretization and Concept Hierarchy generation

#### Data Cube Aggregation
- **Data Cube**: A multidimensional array used for data analysis.
- **Purpose**: Reduce data to a single entity of interest.
- **Method**: Focus on a specific object, then aggregate the data to a higher-level concept.
    - **Ex**: Aggregate sales by region or by month.
- **Benefit**: Good for summarizing data and identifying trends at different granularities.

### Dimensionality Reduction
- Feature selection (i.e., attribute subset selection):
	- probablity distribution of diff classes given vals for those feature sis as close as possible to original distribution given vals of all feats
	- reduce num of patterns in the patterns
	- easier to understand
- Heuristic methods (due to expon. num of choices):
	- step-wise forward selection
	- step-wise backward elimination
	- combining forward selection and backward elimination
	- decision-tree induction

#### Ex of Decision Tree Induction
- if tree can closely identify object w/o all the features, we reduce our attribute sets from initial attribute set


# Intro
Main
1. Supervised Learning
	1. given labels, you learn the data/features
2. Unsupervised Learning
	1. no labels on data, must come up with own object

3. Semi
4. Transfer
5. Reinforced

## Learning from the data
- What is "learning"?
- "...learning is about predicting the future based on the past"
- **Past:** Training data
	- Fully labeled, unsupervised, semi-supervised
	- Classification, Regression
- **Future:** Testing data
	- 
- **Predicting**: Model
	- Linear mode, kernel method, nearest neighbor, decision trees, neural networks

## Statistical Learning
- Input var X ~ predictive, independent var
- Output var Y ~ response, dependent var

1. **Modeling Reality:** When you try to build a model `Y = f(X)` to explain an output variable `Y` based on input variables `X`, there's almost always some part of `Y` that `f(X)` cannot explain perfectly. This unexplained part is the "error" or "noise."
2. **Assumption:** Assuming this error is Gaussian means that the errors are symmetrically distributed around zero (most errors are small, large errors are less common), and their distribution can be described by a bell curve.
3. **Why it matters:**
    - **Simplicity:** It's a common and mathematically convenient assumption.
    - **Statistical Properties:** Many statistical methods (like Ordinary Least Squares regression) perform optimally when errors are normally distributed, especially for constructing confidence intervals and performing hypothesis tests.
    - **Real-world:** Often, the accumulation of many small, independent random factors can lead to an overall error distribution that is approximately Gaussian (Central Limit Theorem).


# Why estimate f?
1. prediction
2. inference

### **Prediction**
- in many situations, a set of inputs X are readily available, but the output Y cannot be easily obtained
			Y^ = f^(X)
- Reducible and irreducible error

- E(Y - Y^2) = E[f(X) + epsilon - f^X]^2
			= [f(X) - f^(X)]^2 + Var(epsilon)]
				*> Reducible*          *> Irreducible*

<span style="background:#fff88f">- predicting sales based on advertising budget/values</span>
- combined predicting the y
### **Inference**
- we are often interested in understanding the association b/w Y and X1, .. , Xp.
- In this situation we wish to estimate f,  but our goal is not necessarily to make predictions for Y
	- Which predictors are associated w/ the response?
	- What is the relationship b/w the response and each predictor?
	- Can the relationship b/w Y and each predictor be adequately summarized?

<span style="background:#fff88f">- how is advertising and sales related?</span>

### Case Study:


# How do we estimate f?
### Parametric methods
- Two-step model-based approach
	- Make an assumption about the functional form or shape of f
	- After a model is selected, fit the model to estimate parameters B0, B1, ... , Bp

	**f(X) = B0 + B1X1 + B2X2 + ... + BpXp**

- fitting data based on data
- tilting the plane to fit model with least mean error, comparing with the data
- we train the models to estimate the coefficients

- the model might not be good


### Non-parametric methods
- we don't look for coefficients
- we try to fit a model that goes close to the data wew have
- Seek an estimate of that gets as close to data points as possible
- avoids assumption of a particular function form of f

- spline fit methods (non-parametric method) which is not a linear plane
- in 2d its a curve, in 3d, its a spline


# Which method to use in analysis?
- if you care about details of ^f(X)? => 
	- you want to perform statistical inference
- Fine w/ treating ^f(X) as a black-box? =>
	- Your interest is prediction

## Prediction flexibility vs Model interpretability
- Prediction accuracy depends on model flexibility
	- Simpler the parametric form of model -> The easier it is to interpret

![[Drawing 2026-02-23 13.56.44.excalidraw]]
- E.g. Deep Learning - High flexibility, low interpretability:
	- you can extract weights, but doesn't say that the weights of this feature are more important than these other weights

- **Parametric models**, for which we can write down a math expression for f(X) before observing the data, a priori (e.g., a linear regression), **are inherently less flexible**
	- popular in analysis


# Notes:
- **Parametric models**, for which we can write down a math expression for f(X) before observing the data, a priori (e.g., a linear regression), **are inherently less flexible**



# Intro
- flexibility of models

# Supervised
- each observation of predictor measurement(s) xi,i = 1, ..., n there is an associated response measurement yi.
- We are to fit a model that relates to the predictors, with the aim of
	- accurately predicting the response for future observations **(prediction)** or 
	- better understanding the relationship b/w the response and the predictors **(inference)**

- will try to mimic the responses
# Unsupervised
- for every observation, i = 1, ..., n we observe vector of measurements xi but no associated response yi
- We can seek to understand the relationships b/w the vars or b/w the observations
	- Ex learning tool: cluster analysis

# Regression vs Classification Problems
- Types of variables:
	- Quantitative:
		- Takes nominal values
		- Ex:
			- person's age, height, income, value of a house, and price of a stock
	- Qualitative (categorical):
		- Ex:
			- classification problems
			- putting into bins

## Quality of Fit (Mean Squared Error)
- we don't want simple error summing:
- *Why?*
	- if you have error of +30 and -30, they cancel out, so mean error is 0, but our model is flawed. That is why we want MEAN SQUARED ERROR (MSE)
		- square cancels out the negative

- in regression setting, most commonly-used measure is Mean Squared Error
	MSE = 1/n SUM(i=1,n) [yi - ^f(xi)]^2
- We want to choose method that gives lowest test MSE, as opposed to lowest training MSE

## Model flexibility
- Orange line **(simple linear regression):**
	- an inflexible, fully parametrized model 
	- Cannot provide a good estimate of f(X)
	- Cannot overfit by modeling the noisy deviations of the data from f(X)
- Green line
	- overly flexible, nonparametric model
	- it can provide a good estimate f(X)
	- BUT it goes too far and overfits by modeling the noise

- the Orange line in second graph is u shape
- why is it u shape?
## Expected Test MSE
- obtained by repeatedly estimating f using large num of training sets, and tested each at x0
- In order to minimize the expected test error,
	- select a statistical learning method that simultaneously achieves low variance and low bias

- 3 components of MSE:
	- variance of model
	- bias of model
	- variance of error

- to lower, we get variance close to zero (variance is just positive)
- this causes orange line to get U shape


## Variance and Bias
- variance refers to amount by which ^f  ...
- bias refers to  ...

**Linear Regression fits**
- if the data points are more curved/parabolic, but linear regression is straight, this is HIGH BIAS
**Spline fits (3d curve)**
- comparatively, this would have LESS BIAS, but still makes error
- but still, since too flexbile, model will have HIGH VARIANCE

- either of these are bad models for us: we want LOW BIAS and LOW VARIANCE

## Bias-Variance Variance trade-off
- dotted line is irreducible error (lowest error we can get)
- non linear data distribution
- still a trade-off even with s curve model

### Sales Ex:
- y - sales
- x - tv advertising budget

- is there a relationship b/w advertising budget and sales?
	- **Exploratory Data Analysis**
- if there is association, how strong is relationship b/w advertising budget and sales?
- if there is, what is the strength of relationship
- How large is association b/w each medium and sales?

- How accurately can we predict future sales?
	- **Prediction**
- Is relationship linear?
- for given level of tv, radio, or newspaper advertising, determine prediction for sales and accuracy of prediction

- is there synergy among the advert media?
- in marketing, this is known as a synergy effect, while in statistics it is called an interaction effect


