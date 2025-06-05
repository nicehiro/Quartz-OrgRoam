+++
title = "TraceVLA: Visual Trace Prompting Enhances Spatial-Temporal Awareness for Generalist Robotic Policiy"
author = ["Fangyuan Wang"]
tags = ["manipulation", "VLA"]
draft = false
+++

Current VLA models often struggle to maintain awareness of their past movements, leading to decisions that are more reactive to current inputs rather than informed by spatial history. This paper introduces a fine-tuned model based on OpenVLA, equipping the VLA model with the necessary context to better understand both temporal and spatial dynamics.

Specifically, they first use Co-tracker to extract dense point trajectories, and then overlay active point trajectories on robot's initial observation frame as visual trace prompting.
