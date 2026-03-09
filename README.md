# Biomedical Image Analysis (BE 5370)
**University of Pennsylvania | Master’s in Biomedical Engineering**

This repository contains two major computational projects focused on advanced medical imaging pipelines. The work spans from artifact correction and 3D deep learning segmentation to optimization-based image registration using high-field MRI and atlas datasets.

---

## Projects

### 1. [Ex Vivo 7T Brain MRI Segmentation](./Segmentation_Project/)
Developed a 3D deep learning pipeline for the automated segmentation of high-resolution brain MRI scans.
* **Core Focus:** Overcoming 7T "dropout artifacts" via N4 Bias Field Correction.
* **Technical Highlights:** Implemented 3D patch extraction and trained **nnU-Net** models for tissue classification.
* **Impact:** Improved Gray Matter (GM) and White Matter (WM) segmentation in clinically significant regions using UPenn AD/FTD Research Center data.

### 2. [Medical Image Registration in PyTorch](./Registration_Project/)
Implemented a robust registration suite to align multi-modal 3D brain volumes.
* **Core Focus:** Global and local anatomical alignment using gradient-based optimization.
* **Technical Highlights:** Developed **Rigid/Affine** registration and the **LogDemons** deformable framework within PyTorch.
* **Impact:** Leveraged auto-differentiation to compute dense velocity fields for consistent human cortical labeling.

---

* **Language:** Python
* **Deep Learning & Optimization:** PyTorch, nnU-Net v2
* **Image Processing:** SimpleITK, NumPy
* **Visualization & QC:** ITK-SNAP, Matplotlib

---
*Author: Jina Kim (kimgina@seas.upenn.edu)*