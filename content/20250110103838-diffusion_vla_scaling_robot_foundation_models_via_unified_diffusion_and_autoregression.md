+++
title = "Diffusion-VLA: Scaling Robot Foundation Models via Unified Diffusion and Autoregression"
author = ["Fangyuan Wang"]
tags = ["diffusion", "VLA", "manipulation"]
draft = false
+++

This paper proposes a Diffusion-VLA model, taking the advatages of the reasoning power of autoregressive models with the robustness of high-frequency action generation offered by diffusion models.

Specifically, it takes Qwen2-VL for vision-language processing to generate reasoning tokens and action tokens.
For action generation, it takes action tokens into the diffusion model as conditional inputs for action decoding and the final embedding from the tokenized ouput of reasoning tokens through Feature-wise Linear Modulation (FiLM). The reasoning tokens function as an auxiliary enhancement to provide contextual depth without dominating the primary decision-making flow.

The idea behind this paper is pretty same as [TraceVLA: Visual Trace Prompting Enhances Spatial-Temporal Awareness for Generalist Robotic Policiy]({{< relref "20250110095745-tracevla_visual_trace_prompting_enhances_spatial_temporal_awareness_for_generalist_robotic_policies.md" >}}), which also takes the reasoning ability of VLM into VLA. The difference are:

-   TraceVLA uses reasoning ability of VLM in the input of VLA, and the action token directly used for action generation.
-   Di-VLA uses reasoning ability of VLM in the action generateion part, aka diffusion model.
