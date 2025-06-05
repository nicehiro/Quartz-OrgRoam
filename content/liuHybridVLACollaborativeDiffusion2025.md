+++
title = "HybridVLA: Collaborative Diffusion and Autoregression in a Unified Vision-Language-Action Model"
author = ["Fangyuan Wang"]
tags = ["VLA"]
draft = false
+++

Existing autoregressive VLA methods ([VLAS: Vision-Language-Action Model With Speech Instructions For Customized Robot Manipulation]({{< relref "zhaoVLASVisionLanguageActionModel2025.md" >}})) leverage large-scale pretrained knowledge, they disrupt the continuity of actions. Meanwhile, some VLA methods ([Diffusion-VLA: Scaling Robot Foundation Models via Unified Diffusion and Autoregression]({{< relref "20250110103838-diffusion_vla_scaling_robot_foundation_models_via_unified_diffusion_and_autoregression.md" >}})) incorporate an additional diffusion head to predict continuous actions, relying solely on VLM-extracted features, which limits their reasoning capabilities. This paper introduces HybridVLA, which seamlessly integrates the strengths of both autoregressive and diffusion policies within a single large language model, rather than connecting them as additional head.
