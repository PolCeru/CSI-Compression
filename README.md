# Efficient Wi-Fi Sensing for IoT Forensics with Lossy Compression of CSI Data
**One-liner:** Lossy compression of Wi-Fi Channel State Information (CSI) for resource-constrained IoT forensics — preserving sensing accuracy while drastically reducing storage needs.

[Paper (arXiv)](https://arxiv.org/pdf/2505.03375)

## Overview
This repository focuses on Wi-Fi sensing, which uses Channel State Information (CSI) from existing Wi-Fi signals to detect human activity without requiring dedicated sensors. Wi-Fi sensing is not only a key component of intelligent IoT systems but also has potential applications in forensic investigations.

One of the main challenges in Wi-Fi sensing is the high dimensionality of CSI data, which creates storage, transmission, and processing bottlenecks in resource-constrained IoT environments. This project investigates the impact of lossy compression on Wi-Fi sensing accuracy, comparing traditional techniques with a deep learning-based approach.

Our findings show that:

- Principal Component Analysis (PCA) and similar interpretable methods can significantly reduce CSI data volume while maintaining classification performance, making them ideal for lightweight IoT forensic applications.
- Deep learning models excel in more complex tasks like activity recognition, achieving compression ratios up to 16,000:1 with minimal impact on performance—but they require careful tuning and more computational resources.

By evaluating two different sensing scenarios, this work demonstrates that integrating lossy compression into Wi-Fi sensing pipelines can enhance IoT efficiency and reduce storage demands in forensic contexts.

## What’s in this repository
This repository contains the code and notebooks used to run the experiments and analyses presented in the paper. **Datasets are not included** in this repository.
