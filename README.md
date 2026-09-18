# 🖐️ Fingerprint Recognition System

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![OpenCV](https://img.shields.io/badge/OpenCV-Computer%20Vision-green.svg)](https://opencv.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

This repository contains a modular **Fingerprint Recognition & Feature Extraction Pipeline** implemented in Python. The system processes raw fingerprint images through image enhancement, noise reduction, ridge orientation, skeletonization, and minutiae extraction (ending and bifurcation points) to generate biometric templates for matching.

---

## 📌 Pipeline Overview

The fingerprint processing pipeline follows a structured biometric feature extraction workflow:

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│ Raw Input Image │ ──> │ Normalization & │ ──> │   Orientation   │
│                 │     │ Noise Filtering │     │    Estimation   │
└─────────────────┘     └─────────────────┘     └────────┬────────┘
                                                         │
┌─────────────────┐     ┌─────────────────┐              │
│ Minutiae & Feature│ <──│ Thinning &      │ <────────────┘
│ Matching Points │     │ Skeletonization │
└─────────────────┘     └─────────────────┘
```

### ⚙️ Key Processing Steps

1. **📷 Preprocessing & Normalization:** Standardizes image intensity and dynamic range to reduce variance caused by sensor differences or pressure.
2. **🌀 Orientation & Frequency Estimation:** Calculates local ridge flow patterns and frequencies to prepare for contextual filtering.
3. **✨ Gabor Enhancement & Binarization:** Applies tuned Gabor filters along ridge orientations to remove noise and repair broken ridges, converting the image to binary black-and-white mask.
4. **🦴 Thinning / Skeletonization:** Reduces ridge width down to 1-pixel thickness while maintaining topological continuity.
5. **🔍 Minutiae Extraction:** Detects key biometric minutiae points:
   * **Bifurcations** (where a ridge splits into two)
   * **Endings** (where a ridge terminates)

---

## 🚀 Quickstart & Usage

### 1. Prerequisites

Ensure you have Python 3.8+ installed along with necessary image processing packages:

```bash
git clone https://github.com/sonlechiht/Fingerprint-Recognition.git
cd Fingerprint-Recognition
pip install -r requirements.txt
```

### 2. Run the Pipeline

Execute the main pipeline script to process input images from `./sample_inputs/` and export visual results into `./output/`:

```bash
python fingerprint_pipeline.py
```

---

## 📚 References & Acknowledgments

* **FVC2002 / FVC2004:** Fingerprint Verification Competition datasets.
* **Raymond Thai:** *Combinatoric Fingerprint Enhancement and Minutiae Extraction Algorithms*.
* **Hong, L., Wan, Y., and Jain, A. K. (1998):** *Fingerprint image enhancement: Algorithm and performance evaluation*. IEEE TPAMI.
