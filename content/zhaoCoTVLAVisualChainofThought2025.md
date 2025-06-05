+++
title = "CoT-VLA: Visual Chain-of-Thought Reasoning for Vision-Language-Action Models"
author = ["Fangyuan Wang"]
draft = false
+++

This paper introduces explicit visual chain-of-though (CoT) reasoning into vision-language-action models by predicting future image frames autoregressively as visual goals before generating a short action sequence to achieve these goals.


## Training {#training}

1.  Pretrain the base 7B VILA-U model on robot demonstrations and action-less videos. Three components, the LLM backbone, projector, and depth transformer are optimized during training, while the vision tower fixed.

2.  Adaptation phase for downstream closed-loop deployment is using task-specific robot demonstrations, and trained with same config as pretrain phase.

3.  The VILA-U model has the ability of generating images.

4.  Action chunk size is set to 10. Learning rate is set to \\(1e-4\\). Learning rate scheduler is Cosine decay. The global batch size is 2048. The epoch is set to 10.


## Improvements {#improvements}

1.  It might not easy for the VLM to generation subgoal images directly, and may consume large training burden.

2.  Is one subgoal image enough? It might be useful to have subgoal chunks, which of course will come with much more burden but it definitely will have more power.

3.  "Think visually" means the model first generate subgoal image, then generate action conditioned on subgoal image. Maybe "think visually" is not a efficiency way?
