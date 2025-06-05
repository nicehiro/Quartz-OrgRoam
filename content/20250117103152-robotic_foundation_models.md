+++
title = "Robotic Foundation Models"
author = ["Fangyuan Wang"]
tags = ["robotic"]
draft = false
+++

Robotic foundation models are models that consider inputs and outputs in robotic domain. It can be categorized into three:

-   pre-trained visual representations for robotics. Some works use pre-trained CNN (ResNet) and vision transformer backbones to extract features from inputs and then use latent vector for later tasks.

-   vision language models for robotics. Some works train a multimodal language model, which allows multimodal inputs (image and text) to answer questions, such as PaLM.

-   dynamics models (learn system dynamics such as Q-value, state and reward)

-   end-to-end control policies (generate action for robots to execute directly)

    The main difference between transformer-based and VLA models are: <span class="underline">transformer-based models do not contains any pre-trained VLMs</span>.

    -   [Transformer-based Robotic Models]({{< relref "20250115221200-transformer_based_robotic_models.md" >}})

    -   [Vision-Language-Action Models]({{< relref "20240719231559-vision_language_action_models.md" >}})
