# HW1
- its okay if training accuracy changes lower to higher to lower etc.
- this is because you're hopping between the local minima

- don't need to iterate through entire epoch

- for conv layers, define how many layers
- how many filters for each of the layers

- NAS technique: neural architecture search (both FCL and CNN)
	- converting manual trial and error process to automatic trial and error process
	- randomly pick combination ...
	- train it
	- if testing result is bad
	- use greedy search to try and pick other combinations and get better result
	- could try and train 10 combinations over epoch, and find best result