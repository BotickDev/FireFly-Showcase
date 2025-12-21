# Project Firefly V4: Physics-Informed Computational Lithography

![Firefly V4 Banner](docs/images/firefly_v4_inference_result.png)

## 🚀 Overview
**Firefly** is a next-generation Computational Lithography engine that uses deep learning to enable sub-3nm semiconductor manufacturing on imperfect hardware.

The semiconductor industry currently relies on perfect, mechanically precise optics ($350M ASML machines). Firefly replaces mechanical precision with algorithmic intelligence. Using a **Physics-Informed U-Net**, it learns to correct for stochastic hardware failures and optical diffraction in real-time.

> 📄 **[Read the Full Technical Whitepaper (Español)](WHITEPAPER.md)**

## 🔬 The Breakthrough: V3 vs V4
We have successfully evolved from simple intensity recovery to full Inverse Lithography Technology (ILT).

![Comparison V3 vs V4](docs/images/comparison_v3_vs_v4.png)

* **V3 (Top):** Learned to bridge gaps (yellow intensity) but produced grayscale outputs not suitable for chrome masks.
* **V4 (Bottom):** Implements **Fourier Optics** and **Binary Constraints**. The AI now generates manufacturing-ready binary masks (0/1) and automatically adds **OPC features** (serifs/dog-ears) to corners to compensate for light diffraction.

## ✨ Key Features
* **Fourier Optics Simulation:** Implements a differentiable **Hopkins Diffraction Model** using FFT.
* **Stochastic Resilience:** Recovers **97.6%** of logic gate integrity even with **20% emitter failure rates**.
* **Binary Mask Constraint:** Enforces physically manufacturable outputs (Chrome/Glass compatible).
* **Edge Computing Ready:** Designed for parallel "Mosaic Inference" on FPGA clusters.

## 📂 Repository Structure (Showcase)
This repository contains the documentation and results of the Firefly Project.

```text
FireFly/
├── docs/
│   └── images/             # High-resolution results and physics tests
├── WHITEPAPER.md           # Full Scientific Paper (Spanish)
└── README.md               # Project Overview
```

## License
Copyright (c) 2026 Project Firefly

All rights reserved.

The contents of this repository, including but not limited to the text, images, and methodology descriptions, are the intellectual property of the author.

Unauthorized copying, modification, distribution, or use of the proprietary source code or trained models associated with this project is strictly prohibited.
