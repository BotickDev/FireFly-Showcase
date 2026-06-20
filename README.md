# Project Firefly V4: Physics-Informed Computational Lithography

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![PyTorch](https://img.shields.io/badge/PyTorch-2.0-orange)
![License](https://img.shields.io/badge/License-Proprietary-red)

> **"Software is the new Lens."**

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://firefly-demo.streamlit.app)

> **[Launch Interactive Demo →](https://firefly-demo.streamlit.app)**  
> *Hosted on Streamlit Community Cloud — may take ~30 seconds to wake up if inactive.*  
> *Demo source: [BotickDev/Firefly-Demo](https://github.com/BotickDev/Firefly-Demo)*

> 📄 **Technical Whitepaper:** [English](WHITEPAPER.md) | [Español](WHITEPAPER_ES.md)

---

## The Problem: EUV Economics vs. Moore's Law

As the semiconductor industry moves toward **2nm (N2)** and **1.8Å (18A)** nodes, the cost of High-NA EUV scanners has exceeded **$500M per unit**. Scaling Moore's Law is no longer purely a physics problem — it is an economic one.

The central question Firefly explores: *can algorithmic correction on low-cost UV hardware substitute for mechanical precision that is priced out of reach for most fabs?*

---

## Approach

Firefly is a research project exploring **physics-informed deep learning for computational lithography**. It uses a **U-Net architecture** conditioned on a differentiable **Hopkins Diffraction model** (via FFT) to learn optical proximity correction (OPC) directly from simulated exposure data.

The key architectural choices:

- **Differentiable Fourier Optics:** The aerial image simulation is embedded inside the training loop, letting the network learn corrections that are physically grounded rather than purely data-driven.
- **Binary Mask Constraint:** Outputs are constrained to manufacturable chrome/glass masks (0/1), not continuous grayscale predictions.
- **Stochastic Emitter Model:** Training includes randomized emitter failure to force the network to generalize across degraded hardware conditions.

This is a **personal research project** — not a product or a deployed system. Results presented here are from controlled simulations on synthetic datasets. All claims should be read in that context.

---

## V3 → V4: From Intensity Recovery to ILT

![Comparison V3 vs V4](docs/images/comparison_v3_vs_v4.png)

The core evolution between versions:

- **V3 (top):** The network learned to bridge broken intensity regions (visible as yellow fill), but outputs were grayscale — not suitable for direct mask fabrication.
- **V4 (bottom):** Added the Hopkins diffraction layer and binary constraint. The network now produces binary masks and learns to place **OPC assist features** (serifs, dog-ears) at corners to pre-compensate for diffraction rounding.

![Firefly V4 Inference Result](docs/images/firefly_v4_inference_result.png)

---

## Technical Details

| Component | Implementation |
|---|---|
| Backbone | Physics-Informed U-Net |
| Optical model | Hopkins partial coherence (FFT-based, differentiable) |
| OPC features | Learned — serifs and dog-ears emerge from training, not rule-based |
| Hardware target | 193nm immersion / low-cost solid-state UV emitters |
| Output | Binary chrome mask (manufacturable format) |

For the full derivation of the optical model, loss function, and training setup, see the [whitepaper](WHITEPAPER.md).

---

## Repository Contents

This is a **showcase repository** — it contains results and documentation only. No training code or model weights are published here.

```text
FireFly-Showcase/
├── docs/
│   └── images/             # Inference results and physics validation plots
├── WHITEPAPER.md           # Technical paper (English)
├── WHITEPAPER_ES.md        # Technical paper (Spanish)
└── README.md
```

The interactive demo (Streamlit app + model weights) lives in [BotickDev/Firefly-Demo](https://github.com/BotickDev/Firefly-Demo).

---

## Status

This project is under active personal development. The results shown represent simulation experiments conducted through 2025. No external validation against real silicon has been performed.

Feedback from engineers in EDA, computational lithography, or optical simulation is welcome — open an issue or reach out directly.
