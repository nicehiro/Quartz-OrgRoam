+++
title = "VLAS: Vision-Language-Action Model With Speech Instructions For Customized Robot Manipulation"
author = ["Fangyuan Wang"]
tags = ["VLA"]
draft = false
+++

Existing VLAs rely heavily on vision-language models (VLMs) that only support text-based instructions, neglecting the more natural speech modality for human-robot interaction. Moreover, the transcription procesedure would lose non-semantic information in the raw speech, such as voiceprint, which may be crucial for robots to complete customized tasks.

This work first focuses on coarse-grained modality alignment between speech and text, achieved by fine-tuning the model using the LibriSpeech-360 speech recognition dataset, by only un-freezing the MLP layer between the speech encoder and the LLM backbone. Then it uses Speech Question Answering (SQA) dataset for enhancing the ability to process information from multiple input modalities. Finally, the model is fine-tuned on the CALVIN with Speech Instructions (CSI) dataset.
