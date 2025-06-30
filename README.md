# TA-TiTok & MaskGen Layer Shape Analysis

## Headers

# TA-TiTok
## Layers
### Input Layer : 256 x 256
### Latent tokens shape: torch.Size([32, 768])
### Text guidance shape: torch.Size([1, 77, 768])

| Layer Name | Depth | Output Size | Parameter Count |
|------------|-------|-------------|-----------------|
| TATiTok | -- | [1, 3, 256, 256] | 24,576 |
| TiTokEncoder | 1-1 | [1, 32, 1, 32] | 222,720 |
| Conv2d | 2-1 | [1, 768, 16, 16] | 590,592 |
| LayerNorm | 2-2 | [1, 289, 768] | 1,536 |
| ModuleList | 2-3 | -- | -- |
| ResidualAttentionBlock (12 layers) | 3-1 to 3-12 | [289, 1, 768] | 7,087,872 each |
| LayerNorm | 2-4 | [1, 32, 768] | 1,536 |
| Conv2d | 2-5 | [1, 32, 32, 1] | 24,608 |
| TATiTokDecoder | 1-2 | [1, 3, 256, 256] | 376,832 |
| Linear | 2-6 | [1, 32, 1024] | 17,408 |
| Linear | 2-7 | [1, 77, 1024] | 787,456 |
| LayerNorm | 2-8 | [1, 366, 1024] | 2,048 |
| ModuleList | 2-9 | -- | -- |
| ResidualAttentionBlock (24 layers) | 3-13 to 3-36 | [366, 1, 1024] | 12,596,224 each |
| LayerNorm | 2-10 | [1, 256, 1024] | 2,048 |
| Sequential | 2-11 | [1, 3, 256, 256] | -- |
| Conv2d | 3-37 | [1, 768, 16, 16] | 787,200 |
| Rearrange | 3-38 | [1, 3, 256, 256] | 0 |
| Conv2d | 2-12 | [1, 3, 256, 256] | 84 |
| Total Parameters | -- | -- | 390,202,484 |
| Trainable Parameters | -- | -- | 0 |
| Non-trainable Parameters | -- | -- | 390,202,484 |
| Total Mult-Adds (Giga) | -- | -- | 90.51 |
| Input Size (MB) | -- | -- | 1.02 |
| Forward/Backward Pass Size (MB) | -- | -- | 665.55 |
| Parameters Size (MB) | -- | -- | 1041.87 |
| Estimated Total Size (MB) | -- | -- | 1708.45 |
## MaskGen
