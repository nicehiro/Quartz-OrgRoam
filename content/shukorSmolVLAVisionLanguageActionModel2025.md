+++
title = "SmolVLA: A Vision-Language-Action Model for Affordable and Efficient Robotics"
author = ["Fangyuan Wang"]
tags = ["VLA"]
draft = false
+++

SmolVLA is a compact and efficient VLA model that skipping layers in the VLM, using a minimal number of visual tokens, leveraging small pretrained VLM and interleaving self-attention layers with lighter cross-attention layers.

It uses SmolVLM-2 for backbone, which relies on SigLIP to encode visual features for SmolLM2 language decoder and reduces visual token count through a <span class="underline">token-shuffling</span> technique for efficiency.

<span class="underline">The proprioceptive states are projected into a single token via a linear layer, then visual, language and state tokens are concatenated and passed to the language decoder.</span>

<span class="underline">They also use a linear projection to adapt the VLM features to align with the action expert's dimension.</span>

For faster inference through layer skipps, they find the feature of half the total layers offers a good tradeoff between speed and performance.

They use a conditional Flow Matching Transfomer as action expert.
