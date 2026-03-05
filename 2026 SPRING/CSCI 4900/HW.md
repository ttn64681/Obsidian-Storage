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

# HW2
- requires to build on top of HW1 , using convolutional layer this time to get ≥ 75% testing accuracy.
- In first CONV layer, have to use 5x5 kernel size, stride size 1, no padding, num filters 32
	- so 32 feature maps
	- later on must visualize output of feature map
- no limit on filter size and fcl for other layers
- include training accuracy in final report
- add as many conv layers as you want, but too much is slow
- CHOOSE GPU from CoLab

- train networks 3 times from scratch
	- what this mean?
		- when you initialize network, you train it and get some percent
		- then next time, when you use different weights, your percent increases
	- train and run it several times and report the mean and standard deviation of 3 accuracies
		- can use numpy.std() to calc standard deviation
- set up a random seed for model training process (refer to random_seed_and_deterministic)
- make sure you give real results and provide seed so others can replicate your results

- torch.backends.cudnn.benchmark = False # make it run faster turning this off
- print(torch.rand(1,3)) # first time give random num
- print(torch.rand(1,3)) # second time give random...?

- during training, store training accuracy and testing accuracy at end of each traning epoch,
- at end of training, need to draw single plot

- visualize testing image


- expect 92% accuracy on the resnet20_cifar19_pretrained.pt dataset (use this as sanity check)

- measure MACs (the computation cost) of your model and the resnet-20 model, using THOP package/library
	- everyone uses THOP to measure computation cost
- should measure during testing not training

- inference time should be measured based on single input