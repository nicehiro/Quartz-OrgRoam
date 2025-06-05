+++
title = "Language Modeling from Scratch"
author = ["Fangyuan Wang"]
tags = ["LLM", "CS336"]
draft = false
+++

The most time-consuming process is coping data from GPU memory to Computer. So the trick is: organize computation to maximize utilization of GPUs by minimizing data movement.

Data movement between GPUs is even slower, but same 'minimize data movement' principle holds.

-   Use collective operations (e.g., gather, reduce, all-reduce)
-   Shard (parameters, activations, gradients, optimizer states) across GPUs
-   How to split computation: {data, tensor, pipeline, sequence} parallelism

Scaling law:

-   With more FLOPs, you can train more big model within same tokens (data).
-   With more FLOPs, you can train more tokens (data) on same model.
-   TL;DR, \\(Tokens^\* = 20 Model Params^\*\\).
