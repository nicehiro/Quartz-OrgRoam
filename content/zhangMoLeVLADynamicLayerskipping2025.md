+++
title = "MoLe-VLA: Dynamic Layer-skipping Vision Language Action Model via Mixture-of-Layers for Efficient Robot Manipulation"
author = ["Fangyuan Wang"]
tags = ["VLA"]
draft = false
+++

This paper tries to skip adjacent layers to reduce high computation of current VLA models since:

1.  Current VLA models have low inference frequency (5-12 Hz running VLA on RTX 4090, while 50-1000 Hz generally on robotic arms)

2.  Using all 24 layers of the Flamingo model improves task success rates by only 3.2% compared to using 6 layers.

3.  The cosine similarity between consecutive layers outputs exceeds 90%, while features from the first and last layers differ significantly.

Several key information of MoLe VLA:

1.  Drawing inspiration from the Shadow Brain Hypothesis, they try to mimics the signal flow in the human brain and enables dynamic layer activation via a router to improve model efficiency.

2.  Proposing a spatial-temporal information layer-decision router, STAR, to leverage the spatial information of the inputs.

3.  Proposing a self-knowledge distillation paradigm, CogKD, to recover cognitive information lost due to layer-skipping in sparse LLMs.


## Training {#training}

1.  The single-view RGB input is resized to \\(224 \times 224\\), and the robot state is aligned with the predicted actions (7 DOF ee poses).

2.  Trained with batch size of 64\*8 and 8 diffusion steps per sample, using pre-trained weights for the vision and language modules.

3.  The vision module (vision tower) is freezed, and the LLM module (LLaMA-2) and the action module (diffusion) are trained end-to-end with a constant learning rate of \\(2 \times 10^{-5}\\) for \\(1K\\) iterations.

4.  It was trained on \\(8\\) A800 GPUs in 1.5 hours using PyTorch's Fully Sharded Data Parallel (FSDP) framework.

5.  The learning rate of MLLM and action head is \\(2e-5\\). The learning rate schedule is constant. The warmup steps are 2500. The LSTM and MLP dropout is 0.4. The training epochs is set to 100.
