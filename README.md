# WinLeak: A Thermal + RGB Image Dataset for Window Air Leakage Detection

**BuildSys ’25 · Dataset Short Paper**\
Anveshika Kamble, Naman Gupta, Nishanth Pullabhotla, Daniel Mossé, Stephen Lee, Benjamin Rottman, Dilip Teja

---

## Overview

**WinLeak** is a publicly available thermal + RGB image dataset designed for **automated window air-leakage detection** in residential buildings.\
It addresses the lack of scalable, low-cost thermal data for building-energy diagnostics by combining **high-end (FLIR E50)** and **consumer-grade (FLIR ONE Edge Pro)** thermal imagery captured under controlled indoor–outdoor temperature differentials (≥ 18 °F / 10 °C).

> Traditional blower-door or manual thermography tests are expensive and not scalable.\
> WinLeak provides an annotated, multi-modal resource enabling machine-learning models to detect window leaks efficiently and reproducibly.

---

## Abstract (Summary)

Window air leakage can contribute up to 40 % of residential heating-and-cooling inefficiencies. WinLeak offers 1,266 paired thermal and RGB images from 7 buildings and 27 windows across multiple configurations.\
Each pair includes **expert-verified segmentation masks** of leaky regions, generated through a semi-automated process that blends temperature-threshold sweeps with majority-vote human selection.\
To demonstrate dataset utility, a **dual-encoder U-Net** model leveraging both modalities was trained for pixel-wise segmentation of leakage zones.

---

## Dataset Highlights

| Category                  | Details                                             |
| ------------------------- | --------------------------------------------------- |
| **Total Images**          | 1,266 thermal + 1,266 RGB                           |
| **Buildings / Windows**   | 7 buildings / 27 windows                            |
| **Window Types**          | 7 (sliding, single-hung, double-hung, picture etc.) |
| **Classes**               | OPEN (431) · LEAK (562) · NO\_LEAK (273)            |
| **Date Range**            | 2024-09-09 → 2025-03-22                             |
| **Indoor Temp**           | 64 – 77 °F                                          |
| **Outdoor Temp**          | 11 – 66 °F                                          |
| **Gap Settings (cm)**     | 0 · 0.5 · 1 · 2                                     |
| **Camera Heights (m)**    | 1 · 1.6                                             |
| **Angles (°)**            | −30 · 0 · +30                                       |
| **Thermal Contrast Rule** | ≥ 18 °F (10 °C) indoor–outdoor differential         |

---

## Imaging Hardware

| Specification              | **FLIR E50** | **FLIR ONE Edge Pro**   |
| -------------------------- | ------------ | ----------------------- |
| Thermal Resolution         | 240 × 180    | 160 × 120               |
| RGB Resolution             | 2048 × 1536  | 640 × 480               |
| Thermal Sensitivity (NETD) | 50 mK        | 70 mK                   |
| Emissivity Used            | 0.97 (both)  |                         |
| Accuracy                   | ± 2 %        | ± 5 %                   |
| Thermal FOV                | 25° × 19°    | 54° × 42°               |
| RGB FOV                    | 53° × 41°    | ≈ 72° × 56° (estimated) |

Both cameras capture synchronized thermal and visual frames. Emissivity was fixed at 0.97 for materials such as glass, vinyl, paint, and wood.

---

## Data-Collection Methodology

- **Locations & Scope:** Seven residential sites across the U.S.; each window photographed in four closure states (0, 0.5, 1.0, 2.0 cm gap).
- **Angles & Distances:** Captured from multiple heights and oblique/frontal views to mimic realistic inspector variability.
- **Environmental Control:** Indoor–outdoor ΔT ≥ 10 °C ensured visible IR contrast.
- **Alignment:** Minor spatial offsets between RGB and IR sensors corrected via post-processing alignment.
- **Leak Simulation:** Mechanical props ensured repeatable small-gap openings.
- **Annotation:** Semi-automated threshold-sweep masks → expert majority-vote refinement.

---

## Comparison with Existing Datasets

| Dataset            | Focus                       | Modalities                | Air-Leakage Masks |
| ------------------ | --------------------------- | ------------------------- | ----------------- |
| **WinSet (2021)**  | Window state                | Thermal + RGB + LiDAR     | No                |
| **IR Survey**      | Window / door detection     | Thermal + RGB (1 camera)  | No                |
| **CIDIS**          | Cross-spectral registration | Thermal + RGB             | No                |
| **Street Scene**   | Window detection (urban)    | RGB                       | No                |
| **WinLeak (ours)** | Air leakage detection       | Thermal + RGB (2 cameras) | ✅ Yes             |

WinLeak is the **first** dataset to pair high-end and low-cost thermal imaging for controlled air-leakage segmentation at the residential-window level.

---

## Dataset Access

The WinLeak dataset is publicly available on Kaggle:

**Download:** [https://www.kaggle.com/datasets/namangupta99/winleak/data](https://www.kaggle.com/datasets/namangupta99/winleak/data)

---

## Baseline Results by Authors

A dual-encoder U-Net combining RGB and thermal inputs was trained for pixel-wise segmentation by the research team.

| Metric (Level)        | Score |
| --------------------- | ----- |
| **Pixel Accuracy**    | 0.98  |
| **Precision**         | 0.53  |
| **Recall**            | 0.47  |
| **F1 / Dice (Pixel)** | 0.50  |
| **IoU (Pixel)**       | 0.33  |
| **IoU (Region)**      | 0.76  |
| **Dice (Region)**     | 0.85  |

Region-level metrics show the model reliably captures contiguous leak patterns even when pixel-level precision is moderate.

---

## License and Citation

**License:** Creative Commons Attribution 4.0 (CC BY 4.0)\
[https://creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/)

### Citation

```bibtex
@inproceedings{winleak_buildsys25,
  author    = {Anveshika Kamble and Naman Gupta and Nishanth Pullabhotla and
               Daniel Moss{\'e} and Stephen Lee and Benjamin Rottman and Dilip Teja},
  title     = {WinLeak: A Thermal and RGB Image Dataset for Window Air Leakage Detection in Residential Buildings},
  booktitle = {Proceedings of the 12th ACM International Conference on Systems for Energy-Efficient Buildings, Cities, and Transportation (BuildSys ’25)},
  year      = {2025},
  address   = {Golden, CO, USA},
  doi       = {10.1145/3736425.3770112},
  isbn      = {979-8-4007-1945-5/2025/11}
}
```

---

## Acknowledgments

This work used resources from the **University of Pittsburgh Center for Research Computing (H2P cluster)** supported by **NSF OAC-2117681** and partially by **NSF #2324873**.\
We thank participating homeowners and research collaborators for enabling data collection and validation.

---

## Contact

**Anveshika Kamble**\
📍 University of Pittsburgh\
📧 [LinkedIn Profile](https://www.linkedin.com/in/anveshika-kamble-706087113)

**Naman Gupta**\
📍 University of Pittsburgh\
📧 [LinkedIn Profile](https://www.linkedin.com/in/naman-gupta99)

**Nishanth Pullabhotla**\
📍 University of Pittsburgh\
📧 [LinkedIn Profile](https://www.linkedin.com/in/nishanth-pullabhotla-550910230)

**Dilip Teja**\
📍 University of Pittsburgh\
📧 [LinkedIn Profile](https://www.linkedin.com/in/dilipteja)

---

*This site mirrors the accepted **BuildSys 2025** dataset short paper and will evolve with future releases of metadata, annotations, and benchmark updates.*
