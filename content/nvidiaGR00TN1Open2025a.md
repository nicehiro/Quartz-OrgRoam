+++
title = "GR00T N1: An Open Foundation Model for Generalist Humanoid Robots"
author = ["Fangyuan Wang"]
tags = ["humanoid", "VLA"]
draft = false
+++

GR00T N1 is a vision-language-action model with a dual-system architecture. The vision-language module interprets the environment through vision and language instructions. The diffusion transformer module generates fluid motor actions in **real time**.

Several key information of this model:

1.  Using an MLP per embodiment to project robot state and action (noise) to a shared embedding dimension <span class="underline">as input to the diffusion action head</span>.

2.  Using Eagle-2 VLM pretrained on Internet-scale data. The LLM and image encoder are aligned over a broad set of vision-language tasks pretrained.

3.  They freeze LLM backbone during training, and found that <span class="underline">using middle-layer instead of final-layer LLM embeddings resulted in both faster inference speed and higher downstream policy success rate</span>. They use the presentations from the 12th layer.

4.  By training action model using VQ-VAE, they obtain a model that can generate latent action by giving current state images obtained from internet (human videos). (But how to execute those latent actions?)
