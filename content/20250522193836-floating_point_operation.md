+++
title = "Floating-point Operation"
author = ["Fangyuan Wang"]
draft = false
+++

FLOP stands for "Floating-point OPeration". It is the basic unit we count when we talk about how much numerical work an algorithm or hardware performs. A single FLOP is one arithmetic operation (addition, subtraction, multiplication, division, fused-multiply-add, etc.)

FLOPS stands for FLOP per second.


## Examples {#examples}


### Dot product of two length-N vectors {#dot-product-of-two-length-n-vectors}

\\[
\text{FLOPs} = 2 N
\\]


### Dense layer: input x weights (M x K) to output (M x N) {#dense-layer-input-x-weights--m-x-k--to-output--m-x-n}

\\[
\text{FLOPs} = 2 MKN
\\]


### 3x3 convolution, stride 1, no groups on a feature map (C channels, H×W spatial) {#3x3-convolution-stride-1-no-groups-on-a-feature-map--c-channels-h-w-spatial}

\\[
\text{FLOPs} = 9 \times H \times W \times C\_{in} \times C\_{out}
\\]
