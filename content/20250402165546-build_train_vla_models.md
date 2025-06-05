+++
title = "Build & Train VLA Models"
author = ["Fangyuan Wang"]
tags = ["LLM", "VLA"]
draft = false
+++

From [MoLe-VLA: Dynamic Layer-skipping Vision Language Action Model via Mixture-of-Layers for Efficient Robot Manipulation]({{< relref "zhangMoLeVLADynamicLayerskipping2025.md" >}}):

> A 7B VLA model running on a commercial-grade GPU like the RTX 4090 generally achieves an inference frequency of approximately 5-12 Hz.


## Training Parameters {#training-parameters}


### Data Collator {#data-collator}

Core functionality:

1.  Batch creation.
2.  Padding. Ensuring all samples in a batch (such as variable-length text inputs) have the same dimensions.
3.  Convert Python objects to PyTorch.
4.  Create attention masks or add special tokens.
