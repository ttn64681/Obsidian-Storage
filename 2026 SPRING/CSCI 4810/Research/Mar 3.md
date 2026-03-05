Jason Dinh, Asher Oortman

- The Aliasing Problem in Computer-Generated Shaded Image
- Crow 1977

Intro:
- 1970s, more computer-shaded images
- problem: artifacts... jagged edges, and missing details
- paper: how to minimize this efficiently
- problem: graphic defects (Jagged Sharp Edges)
	- solution: Anti-Aliased Edges

- previous solutions
	- higher res displays

	- Problems:
		- computationally intensive and slow


	- Solution:
		- convolutional filtering: very computationally
		- apply low pass filter before sampling
		- remove high frequencies

	- Strategy:
		- treat each sample point as finite area rather than infinite spot
		- this allows for computation
		- we apply a 2D convolutional filter

2D Discrete Convolution and Separable Filter

Approximation
- done via filter


Results:
- added polygons

Strengths:
- with the filtering algorithm, no issue of smaller polygons disappearing and tagging areas allows for less computing which reserves the aliasing for creases and edges

supersampling

mipmapping





**3D Transformations of Images in Scanline Order**
by canonicalizing light/viewer positions

- we want texture mapping, but we don't have hardwire-friendly way to do perspective like wraps

- ex:
	- wanting to put flat texture onto a 3d sphere mesh
	- want to warp image onto mesh with geometry and perspective

2 sweeps:
- horizontal sweep and vertical sweep

initial problems:
- inverse mapping was expensive
- simple sample can produce aliasing, holes, and overlaps
- perspective projection makes the mapping non-linear
- hardware prefers sequential reads, not scanline read

- Before scanline warping:
- inverse map every destination pixel to (u,v): leads to heavy math per pixel subdivide polygons itno many small pieces to approximate perspective

Key idea: 2 pass technique
- Pass1, horizontal: for each v scanline, warp along u to produce x'
	- write intermediate image to a frame bugger
- Pass2, vertical: for each x' column, warp along v to produce y'
- handles affine and many perspective mappings
- designed for stream processors: sequential read, sequential writes


2 pass pipeline
1. define mapping


each pass is a 1d resampling problem




- create edge table as you sweep back and forth
- then use edge table to 
- similar to convolution kernels

- 1st phase of scanline: get edges
- 2nd phase of scanline: go back and forth on x-axis