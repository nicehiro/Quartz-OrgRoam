+++
title = "CogACT: A Foundational Vision-Language-Action Model for Synergizing Cognition and Action in Robotic Manipulation"
author = ["Fangyuan Wang"]
tags = ["VLA"]
draft = false
+++

This paper seems the first one that proposes a specialized action module conditoned on VLM output, rather than directly repurpose VLM for action prediction by simple action quantization. They employ advanced diffusion-based transformers (DiT) as action module, preconditioned on VLM output via attention mechanism.
