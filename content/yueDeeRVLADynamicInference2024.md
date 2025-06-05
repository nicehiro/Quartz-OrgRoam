+++
title = "DeeR-VLA: Dynamic Inference of Multimodal Large Language Models for Efficient Robot Execution"
author = ["Fangyuan Wang"]
tags = ["VLA"]
draft = false
+++

This paper tries to address the challenge that current VLAs high computation and memory capacities. They introduce Dynamic Early-Exit for Robotic VLA models that automatically adjusts the size of the activated MLLM based on each situation at hand, allowing the model to terminate processing once a proper size of the model has been activated for a specific situation, thus avoiding further redundant computation.

During training, they randomly sample features from max-pooling-ed all hidden states of MLLM. During inference, they activate an appropriate size of MLLM based on an exit criterion, which accounts for the current situation and predefined computational and GPU memory budgets.

Training details:

1.  Initially, they jointly train the trainable components of the MLLM alongside the action head.

2.  Since the backbone MLLM is pretrained and converges more rapidly, they later freeze the MLLM and finetune only the action head.
