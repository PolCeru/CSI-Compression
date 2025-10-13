# Efficient Wi-Fi Sensing for IoT Forensics with Lossy Compression of CSI Data

**One-liner:** Exploring how lossy compression of Wi-Fi Channel State Information (CSI) can make IoT forensics more efficient — cutting storage needs without losing key sensing accuracy.

[Paper (arXiv)](https://arxiv.org/pdf/2505.03375)

---

## Overview

This project looks at how Wi-Fi sensing — which uses CSI data from regular Wi-Fi signals — can detect human activity without extra sensors. It’s a growing area in intelligent IoT systems and can also support forensic investigations where sensor data is limited or unavailable.

A key issue with CSI-based sensing is that the data is huge. High-dimensional CSI samples are expensive to store, transmit, and process, especially on low-power IoT devices.  
Our work studies how **lossy compression** can help, and how much compression you can apply before sensing accuracy starts to drop. We compare traditional methods with a deep learning–based approach.

---

## Compression Methods

We evaluated four lossy compression techniques for CSI data. Each one offers a different balance between storage efficiency and accuracy:

- **PCA (Principal Component Analysis)**  
  Projects CSI frames onto a smaller set of orthogonal components. It’s fast, easy to interpret, and works well for sensing tasks.

- **Scalar Quantization (SQ)**  
  Quantizes CSI values or PCA coefficients into a limited number of levels. The number of bits per sample directly controls compression and quality.

- **Vector Quantization (VQ)**  
  Groups CSI vectors using clustering (like k-means) and represents each window by its cluster index. It captures relationships between subcarriers better than SQ.

- **Variational Autoencoder (VAE)**  
  Uses a neural network to learn a compact latent representation of the CSI data. It can achieve very high compression ratios, though it needs more compute and tuning.

---

## Processing Pipeline

1. **Preprocessing:** Extract and normalize CSI amplitude; remove noisy or irrelevant subcarriers.  
2. **Windowing:** Segment data into fixed-length windows (e.g., 3 s for 'presence detection', longer for 'activity recognition').  
3. **Compression:** Apply PCA, SQ, VQ, or VAE to each window and store the compressed version.  
4. **Reconstruction & Evaluation:** Decompress the data when needed and run it through classifiers to measure sensing performance.

---

## Findings

- CSI data can be **compressed by several orders of magnitude** with little to no loss in sensing accuracy.  
- Deep learning–based compression (VAE) performs best on complex tasks like activity recognition, achieving up to **16,000× compression** while maintaining accuracy.  
- Traditional methods like PCA or VQ are still valuable for lightweight setups that need quick, interpretable results.

Overall, integrating lossy compression into Wi-Fi sensing pipelines makes IoT forensics **more scalable and practical**, especially when working with limited bandwidth and storage.

---

This repository includes the code and notebooks used in the experiments described in the paper.  
**Note:** Datasets are not included.
