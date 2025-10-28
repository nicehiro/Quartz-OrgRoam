+++
title = "Small Batch Size Training for Language Models: When Vanilla SGD Works, and Why Gradient Accumulation Is Wasteful"
author = ["Fangyuan Wang"]
draft = false
+++

Conventional wisdom dictates that small batch sizes make language model pretraining and fine-tuning unstable, motivating gradient accumulation, which trades off the number of optimizer steps for a proportional increase in batch size. While it is common to decrease the learning rate for smaller batch sizes, other hyperparameters are often held fixed.

In small batch size training experiments, one may observe loss spikes and heavy instability. This paper shows that if instead of holding \\(\beta\_2\\) fixed, it holds the half-life of \\(\beta\_2\\) fixed (measured in number of tokens), stable training is possible all the way down. \\(\beta\_1\\) can hold \\(0.9\\).
