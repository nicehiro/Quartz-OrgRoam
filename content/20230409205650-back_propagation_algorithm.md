+++
title = "Back Propagation Algorithm"
author = ["Fangyuan Wang"]
draft = false
+++

1.  Forward pass: Computation of function signals for each neuron,
2.  Backward pass: Starts at the output layer, recursively compute \\(\sigma\\) for each neuron from output layer towards the first hidden layer. At each layer, the synaptic weights are changed accordingly to the delta rule:
