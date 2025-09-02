# Efficient Wi-Fi Sensing for IoT Forensics with Lossy Compression of CSI Data
**One-liner:** Lossy compression of Wi-Fi Channel State Information (CSI) for resource-constrained IoT forensics — preserving sensing accuracy while drastically reducing storage needs.

[Paper (arXiv)](https://arxiv.org/pdf/2505.03375)

## Overview
This repository focuses on Wi-Fi sensing, which uses Channel State Information (CSI) from existing Wi-Fi signals to detect human activity without requiring dedicated sensors. Wi-Fi sensing is not only a key component of intelligent IoT systems but also has potential applications in forensic investigations.

One of the main challenges in Wi-Fi sensing is the high dimensionality of CSI data, which creates storage, transmission, and processing bottlenecks in resource-constrained IoT environments. This project investigates the impact of lossy compression on Wi-Fi sensing accuracy, comparing traditional techniques with a deep learning-based approach.

### Compression Techniques

We explore four lossy compression methods for CSI data, balancing storage reduction and sensing accuracy:

- **PCA (Principal Component Analysis)**  
  Reduce dimensionality by projecting CSI frames onto a low-dimensional orthogonal basis. Retain the components capturing the most variance. Simple, interpretable, and computationally inexpensive.
- **Scalar Quantization (SQ)**  
  Apply a Lloyd-Max or uniform quantizer to subcarriers or PCA coefficients. The number of quantization levels controls the trade-off between compression ratio and reconstruction fidelity.
- **Vector Quantization (VQ)**  
  Cluster high-dimensional CSI vectors (e.g., k-means) and replace each vector with the nearest centroid index. Captures joint structure better than scalar quantization, enabling higher compression.
- **Variational Autoencoder (VAE)**  
  Learn a compact probabilistic latent representation of the CSI data. Compress by quantizing or entropy-coding latent variables (e.g., μ₁, μ₂, σ₁, σ₂ for a 2-D Gaussian). Data-driven and robust, capable of high compression ratios at the cost of additional computation.

---

### Preprocessing & Pipeline

1. **Amplitude extraction & normalization**  
   Extract CSI amplitude, remove non-informative subcarriers, and normalize per window.
2. **Windowing**  
   Segment the data into windows with configurable length and stride (presence detection: 3 s windows; activity recognition: longer sliding windows).
3. **Compression**  
   Apply the chosen method (PCA, SQ, VQ, or VAE) to each window and store the compressed representation.
4. **Reconstruction & Classification**  
   Decompress when needed and feed reconstructed data to downstream classifiers for evaluation.


## Findings

- These methods can significantly reduce CSI data volume while maintaining classification performance, making them ideal for lightweight IoT forensic applications.
- Deep learning models excel in more complex tasks like activity recognition, achieving compression ratios up to 16,000:1 with minimal impact on performance—but they require careful tuning and more computational resources.

By evaluating two different sensing scenarios, this work demonstrates that integrating lossy compression into Wi-Fi sensing pipelines can enhance IoT efficiency and reduce storage demands in forensic contexts.

## What’s in this repository
This repository contains the code and notebooks used to run the experiments and analyses presented in the paper. **Datasets are not included** in this repository.
