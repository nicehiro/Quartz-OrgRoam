+++
title = "OpenHelix: A Short Survey, Empirical Analysis, and Open-Source Dual-System VLA Model for Robotic Manipulation"
author = ["Fangyuan Wang"]
tags = ["survey", "VLA"]
draft = false
+++

Several limitation of current VLAs:

1.  The large model size of VLAs makes achieving efficient real-time performance difficult.

2.  The end-to-end fine-tuning of pre-trained VLAs on embodied data is challenging due to domain shift and catastrophic forgetting.

What is dual-system VLAs:

[From LLMs to Actions: Latent Codes as Bridges in Hierarchical Robot Control]({{< relref "20240714161824-from_llms_to_actions_latent_codes_as_bridges_in_hierarchical_robot_control.md" >}}) first proposed the dual-system VLA structure, which consists of two system: system 1 closely resembles traditional lightweight policy networks, which are efficient but often task-specific, and system 2 is computationally heavy but offer superior generalization capabilities.

Key design of dual-system VLAs:

1.  MLLM selection. What kind of MLLM model is lightweight enough yet sufficient to complete robotic tasks?

2.  Policy selection. Current general policy models are based on DiT structure and Flow Matching structure. However, dense policy and other new architectures, downstream small models may also see new designs.

3.  Latent feature representation selection. Some are choosing last layers hidden embeddings, some are choosing selected hidden embeddings from middle layers. Some are useing maxpooling of the last layer embeddings. Some are introducing special token, such as &lt;ACT&gt; or &lt;Cognition&gt; token.
