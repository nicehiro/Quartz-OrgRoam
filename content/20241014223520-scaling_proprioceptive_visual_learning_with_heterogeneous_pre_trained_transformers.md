+++
title = "Scaling proprioceptive-Visual Learning with heterogeneous Pre-trained Transformers"
author = ["Fangyuan Wang"]
tags = ["robotic", "VLA"]
draft = false
+++

This paper proposes a pre-training concept, which

1.  maps different embodiments, each with its own proprioception (e.g., the pose of eef), and vision sensors (e.g., the input image of embodiments, like camera), to a shared latent space by embodiment-specific tokenizers
2.  trains a shared transformer trunk on the union of all heterogeneous datasets
3.  transfers to different embodiment with a small, new tokenizer learned at transferring time

The biggest novelty of this paper should be the first one. Nowadays, a lot of works are using different decoders to fit different embodiments, while this paper first proposes to encoding the different embodiments to a shared latent space so that the unseen embodiments can fit well too.
