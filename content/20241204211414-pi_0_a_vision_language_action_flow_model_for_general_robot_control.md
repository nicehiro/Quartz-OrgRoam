+++
title = "$\\pi_0$: A Vision-Language-Action Flow Model for General Robot Control"
author = ["Fangyuan Wang"]
tags = ["manipulation", "VLA"]
draft = false
+++

This paper proposes a novel [Flow Matching]({{< relref "20241204211606-flow_matching.md" >}}) architecture built on the top of a pre-trained vision-language model (paligemma) and introduces details of how to build and train on a large and diverse dataset from multiple robot platforms. The flow matching algorithm is a variant of diffusion, which allows to handle high-frequency action chunks and highly  dexterous tasks.

Some interesting ideas from the paper:

1.  The axis along which human intelligence most outpaces machine intelligence is <span class="underline">versatility</span>: the ability to solve diverse tasks situated in varied physical environments.

2.  Three major challenges in developing generalist robot policies: (1) Large scale (model); (2) Right model structures; (3) Right training recipe.

3.  The training process contains 2 stages: (1) Pre-training phase for training a base model that exhibits broad capabilities and generalization, but is not necessarily specialized for high performance on any one task; (2) Post-training phase for specific downstream tasks by using high-quality curated data.

4.  They also mention that utilizing a high-level policy (such as [SuSIE: Subgoal Synthesis via Image Editing]({{< relref "20231019122353-susie_subgoal_synthesis_via_image_editing.md" >}})) that decomposes high-level tasks into more immediate subtasks to assist the proposed VLA to complete more complex tasks.


## Training {#training}

1.  They use the PaliGemma VLM as basebone, with the following differences: (1) additional input and output projections for the robotics-specific tokens, including the robot states and actions, (2) additional MLP for the flow matching timestep information, (3) a second, smaller set of weights for the action expert.

2.  The action chunk size is set to 50.

3.  The action expert / head is implemented as a single transformer with two sets of weights, where each token is routed to one of the experts; the weights interact only through the transformer's self-attention layers.

4.  The image and language prompt are routed to the VLM backbone, while the robot states and noise actions are routed to the action expert.

5.  The model structure is quite interesting: it contains one gemma-2b for llm reasoning, and one gemma-300M for action expert. The image and text tokens will input to llm head, and the robot state and action noise will input to action head. And they use attention to connect the output of llm head and the robot state.
