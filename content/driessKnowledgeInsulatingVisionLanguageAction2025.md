+++
title = "Knowledge Insulating Vision-Language-Action Models: Train Fast, Run Fast, Generalize Better"
author = ["Fangyuan Wang"]
tags = ["VLA"]
draft = false
+++

**The constrains of single-system based VLAs are:**

1.  tens or hundreds of billions of parameters,
2.  operate on discrete tokens rather than the continuous-valued outputs that are required for controlling robots.

To alleviate the constrains of above, two-system based VLAs that implements an special action expert with low-dimensional parameters to generate continuous actions.

**Interesting question:**

1.  Whether action experts training preserve or degrade the semantic knowledge contained in the pretrained VLM?
2.  What effect action experts training have on the VLA training dynamics?

**The key idea of this paper:**

1.  During training, they use next-token prediction loss for both language prediction (to preserve the semantic knowledge of VLM) and discrete action (to add robotic's observation knowledge to VLM), and flow-matching based continuous action expert loss (to predict continuous actions).
2.  During inference, they use only the action expert to generate actions for fast inference.

Other interesting conclusion of current VLAs in this paper:

**Action representations**:

1.  Naive discretization. Each dimension of each action in a chunk is discretized, and then each discretization bin is associated with a special text token. So a chunk \\(a\_{1:H}\\) is mapped into \\(H \times d\\) tokens. Robot action prediction then is framed as a next-token prediction problem and the model can be trained as if it was a non-robot specific VLM with a cross-entropy loss. The naive discretization is that for high-frequency and high-dim. $&pi;_0$-FAST is a accelerating token encoding method to encode action chunks.
2.  Action expert/head. Recent proposed VLAs have used diffusion or flow matching to generate continuous actions.

**State representations**:

1.  Text state after discretization by simply taking state as text.
2.  Special token state after discretization by taking each dimention's state as a special token.
3.  Continuous state by directly mapping the continuous state into the backbone with a learned projection, into the model (action expert).

**Empirical experience**

1.  Autoregressive VLAs are slow.
2.  Robotic specific architectures and modality adapters don't benifit as much from VLM pretraining. While part of these models are initialized from pre-trained VLMs, the robotic-specific modules are initialized from scratch. The naive training with a randomly initialized action expert harms the model's ability to follow language commands.
3.  VLM pretraining does not have sufficient representations for robotics, i.e., freezing doesn't work.
