+++
title = "From LLMs to Actions: Latent Codes as Bridges in Hierarchical Robot Control"
author = ["Fangyuan Wang"]
tags = ["VLA", "robotic", "LLM"]
draft = false
+++

This paper introduce a hierarchical robot control method, Latent Codes as Bridges, which uses a learnable latent code to act as a bridge between LLMs and low level polices.

They category current LLMs based control system as two:

1.  calling a set of pre-defined skills or APIs.
    -   needs to have semantics attached to them that make linguistic sense.
    -   constrains the set of skills to a closed vocabulary and prevents any form of generalization to new skills or capability.
    -   tunes those pre-defined skills are challenging.

2.  language as interface: not directly use premitive skills but those simple language command as input of policy
    -   not all high level tasks can be decomposed into subtasks in simple language.
    -   end-to-end fine-tuning might erase reasoning capabilities that the LLM originally had.

This paper proposes an learnable &lt;ACT&gt; token which act as a learned intermediary: instead of mapping directly from natural language to actions, the token's context-dependent embedding creates a latent space that can better capture subtle details necessary for low-level control.


## Model {#model}

The model contains two components: a pre-trained LLM (LLaVA) and a pre-trained policy (Actor Diffusion). The model is trained to output &lt;ACT&gt; corresponding tokens. Then the &lt;ACT&gt; tokens' embeddings, which is extracted from the last-layer embedding features, will considered as conditional latent input of the action policy, along with environment observations, to output the action.


## Training {#training}

Two stages:

1.  aligning the embeddings (&lt;ACT&gt;) produced by the LLM with the feature space of the policy by freezing the action policy;

2.  then fine-tuning all models.

Theyuse LoRA with a rank of 16, and takes about 8 hours to finish on an 8 80GB A100 GPU.


## Questions {#questions}

-   How many tokens/embeddings used for action policy?

-   What's the structure of all MLPs?

-   Is this a VLA?

    Yes. But with a pre-trained action policy.

-   Any improvements?
    -   Need to align the &lt;ACT&gt; with the action policy

    -   The latent space information are not verified or proved. It may contains unnessary information or less acurate information to help the action policy to generate actions.
