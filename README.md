# 🚀 Enhancing Supernova Detection with Super Resolution

This repository presents our Computer Vision project that explores the use of Super-Resolution (SR) techniques to improve the performance of deep learning-based supernova detection, particularly in noisy and low-resolution astronomical imagery.

## 📌 Project Overview

Supernovae are powerful cosmic explosions crucial for astrophysical research. However, astronomical images often suffer from noise and resolution issues, making detection difficult. This project integrates super-resolution models with a YOLOv8 object detection pipeline to enhance image quality and improve detection accuracy.


## 📂 Datasets

### 1. [Pan-STARRS](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/JGO6VI)
- 12,447 clean, high-resolution difference images (302x302).
- Minimal observational noise.
- Ideal for testing standard object detection pipelines.

### 2. [Popular Supernova Project (PSP)](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/JGO6VI)
- 716 real-world noisy astronomical images.
- Includes alignment issues, low SNR, and environmental distortions.
- Used to evaluate SR-enhanced robustness.

## 🧪 Methodology

### 🔍 Detection Pipeline
- Backbone: **YOLOv8** (PyTorch)
- All models trained with:
  - Optimizer: AdamW (lr=0.002, momentum=0.9)
  - Epochs: 100
  - Batch size: 32
  - Input size: 320×320 (baseline), 640×640 (SR-enhanced)

### 🖼️ Super-Resolution Techniques
- **RDN** (Residual Dense Network)
- **RRDN** (Residual-in-Residual Dense Network)
- **ESRGAN** (Enhanced SR GAN)
- Compared against baseline YOLOv8 without SR

### ⚙️ Preprocessing
- Standardization, resizing, and denoising
- SR applied to both datasets before detection

## 📊 Evaluation Metrics

- **Precision**: Correctness of predicted detections
- **Recall**: Completeness of supernova detections
- **mAP@50 / mAP@50–95**: Object localization accuracy
- **Timing**: Preprocessing, inference, and postprocessing latency


## 🎥 Project Presentation Video

We recorded a full presentation of this project to demonstrate the methodology, experiments, and results visually. You can watch it here:

**[📺 Enhancing Supernova Detection with Super‑Resolution — Project Presentation](https://www.youtube.com/watch?v=l6uBqnTtBT0)**

In the video, we cover:
- The motivation and background behind applying super‑resolution to astronomical imaging  
- A walkthrough of the YOLOv8 detection pipeline integrated with SR models  
- Comparative results between clean (Pan‑STARRS) and noisy (PSP) datasets  
- Visual examples of how SR preprocessing improves detection in noisy samples  
- Discussion of timing overheads and future research directions  


## 📈 Results Summary

### Pan-STARRS (Clean Dataset)
| Model         | Precision | Recall | mAP@50 | mAP@50–95 |
|---------------|-----------|--------|--------|-----------|
| Baseline      | 0.972     | 0.865  | 0.929  | 0.657     |
| RDN Enhanced  | 0.944     | 0.877  | 0.918  | 0.575     |

> SR did not improve performance due to already optimal image quality.

### PSP (Noisy Dataset)
| Model        | Precision | Recall | mAP@50 | mAP@50–95 | Pre (ms) | Infer (ms) | Post (ms) |
|--------------|-----------|--------|--------|-----------|----------|------------|-----------|
| Baseline     | 0.777     | 0.738  | 0.781  | 0.319     | 0.7      | 6.2        | 3.5       |
| RDN          | 0.833     | 0.775  | 0.840  | 0.453     | 2.5      | 6.1        | 3.1       |
| ESRGAN       | 0.840     | 0.739  | 0.803  | 0.384     | 2.5      | 5.0        | 3.4       |
| RRDN         | 0.848     | 0.789  | 0.840  | 0.400     | 2.5      | 5.3        | 3.6       |

> SR notably improved detection in noisy environments with minimal overhead.

## 🎯 Key Takeaways

- Super-resolution helps significantly in low-quality datasets like PSP.
- Clean datasets (Pan-STARRS) may not benefit from SR and can even degrade slightly.
- ESRGAN and RDN proved most effective among the tested SR methods.


## 🔮 Future Work

* Fine-tune SR models for astronomical image characteristics.
* Incorporate multi-band (UV/IR) data.
* Develop noise-aware training for more robust detection.

## 📚 References

1. [Yin et al. – Supernova Detection Framework](https://www.mdpi.com/1424-8220/21/5/1926)
2. [Pan-STARRS Dataset](https://star.pst.qub.ac.uk/ps1threepi/psdb/)
3. [PSP Dataset](http://psp.china-vo.org/)
4. [ESRGAN GitHub](https://github.com/sanghyun-son/EDSR-PyTorch)


---

📌 *This project was developed as part of the Computer Vision course (BBM 418) at Hacettepe University.*


