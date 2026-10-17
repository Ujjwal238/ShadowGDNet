<div align="center">

# ShadowGDNet: Gated and Decoupled Fusion of Unreliable Scene Priors for Mask-Free Shadow Removal

**[Ujjwal Mishra](https://scholar.google.co.in/citations?user=Ggw7z6sAAAAJ&hl=en)<sup>1</sup>, Kailash A. Hambarde<sup>2</sup>, Hugo Proença<sup>2</sup>, Sachin Chaudhary<sup>3</sup>, Praful Hambarde<sup>4</sup>, Amit Shukla<sup>4</sup>**

<sup>1</sup>Indian Institute of Information Technology Una &nbsp; <sup>2</sup>University of Beira Interior, Instituto de Telecomunicações &nbsp; <sup>3</sup>UPES &nbsp; <sup>4</sup>Indian Institute of Technology Mandi

Paper (coming soon) · [Supplementary material](supplementary/ShadowGDNet_supplementary.pdf)

</div>

---

## Overview

Mask-free shadow removal networks often take depth, surface normals and semantic
features from frozen foundation models as extra inputs. These priors are computed
from the shadowed image, so the shadow affects them too: on ISTD+, the depth
estimated from a shadowed image differs from the depth of its shadow-free pair
6.9 times more inside the shadow than outside it.

ShadowGDNet makes two changes to the DenseSR backbone so that the network learns
where to rely on these priors.

- **Gated Skip Fusion (GSF)** learns a per-pixel, per-channel gate on each skip
  connection.
- **Decoupled Multi-Modal Attention (DMMA)** gives each prior its own group of
  attention heads, so an error in one prior no longer affects every head.

Together they add 0.04M parameters to the backbone.

|                 | ISTD  | ISTD+ | WSRD+ | WSRD+, noisy geometric priors |
| --------------- | ----- | ----- | ----- | ----------------------------- |
| DenseSR         | 30.64 | 33.98 | 26.28 | −1.21 dB                      |
| **ShadowGDNet** | **31.41** | **34.43** | **26.42** | **−0.42 dB**          |

PSNR in dB. The last column is the PSNR drop when Gaussian noise (σ = 0.2) is
added to the geometric priors at test time.

## Code

The complete codebase will be released in this repository once the paper is
public.

## Supplementary material

The supplementary material is included in this repository as a PDF:
[supplementary/ShadowGDNet_supplementary.pdf](supplementary/ShadowGDNet_supplementary.pdf).
It covers the architecture specification, the prior-reliability protocol, the
design ablations, the depth-model study on all datasets, the robustness analyses
and the full cost breakdown.

## Contact

[ujjwalmishra238@gmail.com](mailto:ujjwalmishra238@gmail.com)
