+++
title = "Pytorch Stack"
author = ["Fangyuan Wang"]
tags = ["pytorch"]
draft = false
+++

Concatenates a sequence of tensors along a new dimension.
把一组向量沿新的维度组合。

```python
a = torch.randn((4, 5))
b = torch.stack((a, a, a), dim=0)
#=> (3, 4, 5)
c = torch.stack((a, a, a), dim=1)
#=> (4, 3, 5)
d = torch.stack((a, a, a), dim=2)
#=> (4, 5, 3)
```
