+++
title = "Accelerating Vision-Language-Action Model Integrated with Action Chunking via Parallel Decoding"
author = ["Fangyuan Wang"]
tags = ["VLA"]
draft = false
+++

The performance of VLA models can be improved by integrating with [Action Chunking]({{< relref "20250317101732-action_chunking.md" >}}) for effective control. However, action chunking linearly scales up action dimensions in VLA models with increased chunking sizes. This paper aims to tackle this problem by proposing PD-VLA, a parallel decoding framework for VLA models. This paper tries to use Jacobi Decoding method in VLA model.
