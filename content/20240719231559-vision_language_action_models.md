+++
title = "Vision-Language-Action Models"
author = ["Fangyuan Wang"]
tags = ["VLA"]
draft = false
+++

From RT-2 (Google DeepMind):

> We propose to co-fine-tune state-of-the-art vision-language models on both robotic trajectory data and Internet-scale vision-language tasks, such as visual question answering. In contrast to other approaches, we propose a simple, general recipe to achieve this goal: in order to fit both natural language responses and robotic actions into the same format, <span class="underline">we express the actions as text tokens and incorporate them directly into the training set of the model in the same way as natural language tokens</span>. We refer to  such category of models as vision-language-action models (VLA) and instantiate an example of such a model, which we call RT-2.

Vision-Language-Action models typically utilize pre-trained vision-language models (VLMs) as their base and are fine-tuned to predict robotic actions. The models that do not rely on pre-trained VLMs are referred to here as **Robotic Foundation Models**.


## VLA Models {#vla-models}

We categorize current VLA architectures into two broad families:

-   Single‑system VLAs. A single vision–language model handles perception, reasoning, and action prediction. Continuous motor commands are first discretized by a learned action tokenizer (derived from the text tokenizer), and the model simply generates these tokens in sequence.

-   Dual‑system VLAs. High‑level understanding and low‑level control are split. A vision–language backbone encodes the current images and instruction, while a dedicated action‑policy network produces continuous commands from those embeddings.

Two principal mechanisms are used to connect the vision–language backbone to the action head:

-   Special‑token-bridged. During VLM fine‑tuning, a reserved token such as <span class="underline">&lt;ACT&gt;</span> is appended; its final embedding is passed directly to the policy.

-   Feature‑pooling-bridged. The full sequence of hidden states is aggregated—via max‑pooling, mean‑pooling, or learned attention—to yield a compact feature vector fed to the policy.


### Single-system VLA {#single-system-vla}

-   **LoHoVLA**: A Unified Vision-Language-Action Model for Long-Horizon Embodied Tasks, arxiv, May 31 2025. [[Paper](http://arxiv.org/abs/2506.00411)]

-   **UniVLA**: Learning to Act Anywhere with  Task-centric Latent Actions, The University of Hong Kong, arxiv, May 9 2025. [[Paper](http://arxiv.org/abs/2505.06111)] [[Code](https://github.com/OpenDriveLab/UniVLA)]

-   **3D-CAVLA**: 3D-CAVLA: Leveraging Depth and 3D Context to Generalize Vision–Language Action Models for Unseen Tasks, New York University, arxiv, May 9 2025. [[Paper](http://arxiv.org/abs/2505.05800)] [[Website](https://3d-cavla.github.io/)]

-   **NORA**: NORA: A SMALL OPEN-SOURCED GENERALIST VISION LANGUAGE ACTION MODEL FOR EMBODIED TASKS, Singapore University of Technology and Design, arxiv, Apr 28 2025. [[Paper](http://arxiv.org/abs/2504.19854)]

-   **CoT-VLA**: [CoT-VLA: Visual Chain-of-Thought Reasoning for Vision-Language-Action Models]({{< relref "zhaoCoTVLAVisualChainofThought2025.md" >}}), NVIDIA &amp; Stanford, arxiv, Mar 27 2025. [[Paper](http://arxiv.org/abs/2503.22020)] [[Website](https://cot-vla.github.io/)]

-   **PD-VLA**: [Accelerating Vision-Language-Action Model Integrated with Action Chunking via Parallel Decoding]({{< relref "songAcceleratingVisionLanguageActionModel2025.md" >}}), HKUST (GZ), arxiv, Mar 4 2025. [[Paper](http://arxiv.org/abs/2503.02310)]

-   **VLAS**: [VLAS: Vision-Language-Action Model With Speech Instructions For Customized Robot Manipulation]({{< relref "zhaoVLASVisionLanguageActionModel2025.md" >}}), Westlake University, arxiv, Feb 21 2025. [[Paper](http://arxiv.org/abs/2502.13508)] [[Code](https://github.com/whichwhichgone/VLAS)]

-   **VLA-Cache**: Towards Efficient Vision-Language-Action Model via Adaptive  Token Caching in Robotic Manipulation, University of Sydney, arxiv, Feb 4 2025. [[Paper](http://arxiv.org/abs/2502.02175)]

-   **Spatial-VLA**: SpatialVLA: Exploring Spatial Representations for  Visual-Language-Action Models, Shanghai AI Lab, arxiv, Jan 28 2025. [[Paper](https://arxiv.org/abs/2501.15830)] [[Website](https://spatialvla.github.io)] [[Code](https://github.com/SpatialVLA/SpatialVLA)] [[Model](https://huggingface.co/collections/IPEC-COMMUNITY/foundation-vision-language-action-model-6795eb96a9c661f90236acbb)]

-   **TRACEVLA**: [TraceVLA: Visual Trace Prompting Enhances Spatial-Temporal Awareness for Generalist Robotic Policiy]({{< relref "20250110095745-tracevla_visual_trace_prompting_enhances_spatial_temporal_awareness_for_generalist_robotic_policies.md" >}}), University of Maryland, arxiv, Dec 25 2024. [[Paper](http://arxiv.org/abs/2412.10345)]

-   **OpenVLA**: [OpenVLA: An Open-Source Vision-Language-Action Model]({{< relref "20240718161839-openvla_an_open_source_vision_language_action_model.md" >}}), Stanford University &amp; UC Berkeley &amp; Toyota Research Insititute, arxiv, Jun 13 2024. [[Website](https://openvla.github.io)] [[Paper](http://arxiv.org/abs/2412.03293)] [[Code](https://github.com/openvla/openvla)] [[Model](https://huggingface.co/openvla)]

-   **RT-2**: RT-2: Vision-Language-Action Models Transfer Web Knowledge to Robotic Control, Google DeepMind, July 28 2023.


### Dual-system VLA {#dual-system-vla}


#### Special-token-bridged {#special-token-bridged}

-   **OpenHelix**: [OpenHelix: A Short Survey, Empirical Analysis, and Open-Source Dual-System VLA Model for Robotic Manipulation]({{< relref "cuiOpenHelixShortSurvey2025.md" >}}), Westlake University, arxiv, May 6 2025. [[Paper](http://arxiv.org/abs/2505.03912)]

-   **MoLe-VLA**: [MoLe-VLA: Dynamic Layer-skipping Vision Language Action Model via Mixture-of-Layers for Efficient Robot Manipulation]({{< relref "zhangMoLeVLADynamicLayerskipping2025.md" >}}), Nanjing University &amp; HK PolyU &amp; Peking University, Mar 26 2025. [[Paper](http://arxiv.org/abs/2503.20384)] [[Website](https://sites.google.com/view/mole-vla)] [[Code](https://github.com/RoyZry98/MoLe-VLA-Pytorch/)]

-   **FuSe**: Beyond Sight: Finetuning Generalist Robot Policies with  Heterogeneous Sensors via Language Grounding, UC Berkeley, arxiv, Jan 8 2025. [[Website](https://fuse-model.github.io/)] [[Paper](http://arxiv.org/abs/2501.04693)] [[Code](https://github.com/fuse-model/FuSe)] [[Model](https://huggingface.co/datasets/oier-mees/FuSe)]

-   **Diffusion-VLA**: [Diffusion-VLA: Scaling Robot Foundation Models via Unified Diffusion and Autoregression]({{< relref "20250110103838-diffusion_vla_scaling_robot_foundation_models_via_unified_diffusion_and_autoregression.md" >}}), East China Normal University, arxiv, Dec 4 2024. [[Website](https://diffusion-vla.github.io/)] [[Paper](http://arxiv.org/abs/2412.03293)]

-   **CogACT**: [CogACT: A Foundational Vision-Language-Action Model for Synergizing Cognition and Action in Robotic Manipulation]({{< relref "liCogACTFoundationalVisionLanguageAction2024.md" >}}), Tsinghua University, arxiv, Nov 29 2024. [[Paper](http://arxiv.org/abs/2411.19650)] [[Website](https://cogact.github.io)] [[Code](https://github.com/microsoft/CogACT)] [[Model](https://huggingface.co/CogACT)]


#### Feature-pooling-bridged {#feature-pooling-bridged}

-   **SmolVLA**: [SmolVLA: A Vision-Language-Action Model for Affordable and Efficient Robotics]({{< relref "shukorSmolVLAVisionLanguageActionModel2025.md" >}}), Hugging Face, arxiv, Jun 4 2025. [[Paper](http://arxiv.org/abs/2506.01844)] [[Website](https://huggingface.co/blog/smolvla)] [[Model](https://huggingface.co/blog/smolvla)]

-   **\\(\pi\_{0.5}\\)**: \\(\pi\_{0.5}\\): a Vision-Language-Action Model with Open-World Generalization, Physical Intelligence, arxiv, Apr 22 2025. [[Paper](http://arxiv.org/abs/2504.16054)] [[Website](https://www.pi.website/blog/pi05)]

-   **Hi Robot**: Hi Robot: Open-Ended Instruction Following with Hierarchical  Vision-Language-Action Models, Physical Intelligence &amp; Stanford University, arxiv, Feb 26 2025. [[Paper](http://arxiv.org/abs/2502.19417)] [[Website](https://www.pi.website/research/hirobot)]

-   **ChatVLA**: ChatVLA: Unified Multimodal Understanding and Robot Control  with Vision-Language-Action Model, Midea Group &amp; East China Normal University, arxiv, Feb 21 2025. [[Paper](http://arxiv.org/abs/2502.14420)] [[Website](https://chatvla.github.io/)]

-   **DexVLA**: DexVLA: Vision-Language Model with Plug-In Diffusion Expert for General Robot Control, Midea Group &amp; East China Normal University, arxiv, Feb 9 2025. [[Paper](http://arxiv.org/abs/2502.05855)] [[Website](https://dex-vla.github.io/)] [[Code](https://github.com/lesjie-wen/dexvla)]

-   **UP-VLA**: A Unified Understanding and Prediction Model for Embodied Agent, Tsinghua University &amp; Shanghai Qi Zhi Institute, arxiv, Feb 3 2025. [[Paper](http://arxiv.org/abs/2501.18867)]

-   **iRe-VLA**: [Improving Vision-Language-Action Model with Online Reinforcement Learning]({{< relref "guoImprovingVisionLanguageActionModel2025.md" >}}), Tsinghua University &amp; Shanghai Qi Zhi Institute, arxiv, Jan 28 2025. [[Paper](http://arxiv.org/abs/2501.16664)]

-   **FAST**: FAST: Efficient Action Tokenization for  Vision-Language-Action Models, Physical Intelligence &amp; UC Berkeley &amp; Stanford, arxiv, Jan 16 2025. [[Website](https://pi.website/research/fast)] [[Paper](http://arxiv.org/abs/2501.09747)] [[Tokenizer](https://huggingface.co/physical-intelligence/fast)] [[Code](https://github.com/Physical-Intelligence/openpi)]

-   \\(\pi\_0\\): \\(\pi\_0\\): A Vision-Language-Action Flow Model for  General Robot Control, Physical Intelligence, arxiv, Oct 31 2024. [[Website](https://physicalintelligence.company/blog/pi0)] [[Paper](http://arxiv.org/abs/2410.24164)] [[Code](https://github.com/Physical-Intelligence/openpi)]

-   **DeeR-VLA**: [DeeR-VLA: Dynamic Inference of Multimodal Large Language Models for Efficient Robot Execution]({{< relref "yueDeeRVLADynamicInference2024.md" >}}), Tsinghua University, NeurIPS 24. [[Paper](https://openreview.net/forum?id=QKp3nhPU41&referrer=%5Bthe%20profile%20of%20Yizeng%20Han%5D(%2Fprofile%3Fid%3D~Yizeng_Han1))] [[Website](https://github.com/yueyang130/DeeR-VLA)] [[Code](https://github.com/yueyang130/DeeR-VLA)]


#### Others {#others}

-   **OFT**: Fine-Tuning Vision-Language-Action Models: Optimizing Speed and Success, Stanford, arxiv, Apr 28 2025. [[Paper](https://arxiv.org/abs/2502.19645)] [[Website](https://openvla-oft.github.io/)] [[Code](https://github.com/moojink/openvla-oft)] [[Model](https://huggingface.co/moojink?search_models=oft)]

-   **HybridVLA**: [HybridVLA: Collaborative Diffusion and Autoregression in a Unified Vision-Language-Action Model]({{< relref "liuHybridVLACollaborativeDiffusion2025.md" >}}), Peking University, Mar 13 2025. [[Paper](http://arxiv.org/abs/2503.10631)] [[Website](https://hybrid-vla.github.io)] [[Code](https://github.com/PKU-HMI-Lab/Hybrid-VLA)]


### For Humanoid Robots {#for-humanoid-robots}

-   **GR00T N1**: [GR00T N1: An Open Foundation Model for Generalist Humanoid Robots]({{< relref "nvidiaGR00TN1Open2025a.md" >}}), NVIDIA, Mar 27 2025. [[Paper](http://arxiv.org/abs/2503.14734)] [[Website](https://developer.nvidia.com/isaac/gr00t)] [[Code](https://github.com/NVIDIA/Isaac-GR00T)] [[Dataset](https://huggingface.co/datasets/nvidia/PhysicalAI-Robotics-GR00T-X-Embodiment-Sim)]

-   **NAVILA**: NAVILA: LEGGED ROBOT VISION-LANGUAGEACTION MODEL FOR NAVIGATION, UC San Diego, arxiv, Dec 5 2024. [[Website](https://navila-bot.github.io/)] [[Paper](http://arxiv.org/abs/2412.04453)]

-   **Humanoid-VLA**: Humanoid-VLA: Towards Universal Humanoid Control with Visual Integration, Westlake University &amp; Zhejiang University, arxiv, Feb 21 2025. [[Paper](http://arxiv.org/abs/2502.14795)]

-   **GO-1**: [AgiBot World Colosseo: Large-scale Manipulation Platform for Scalable and Intelligent Embodied Systems]({{< relref "agibot-worldAgiBotWorldColosseo.md" >}}), AgiBot-World (Shanghai AI Lab &amp; AgiBot Inc.), AgiBot World, Mar 10 2025. [[Paper](https://agibot-world.com/blog/go1#:~:text=Paper:-,agibot_go1.pdf)] [[Website](https://agibot-world.com)] [[Code](https://github.com/OpenDriveLab/Agibot-World)] [[Model](https://huggingface.co/agibot-world)]
