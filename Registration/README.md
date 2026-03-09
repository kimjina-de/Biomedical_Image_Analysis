# Medical Image Registration Pipeline in PyTorch
**Biomedical Image Analysis | University of Pennsylvania**

## Project Overview
[cite_start]This project focuses on the implementation and optimization of core medical image registration algorithms using the **PyTorch** deep learning framework. [cite_start]The pipeline facilitates the alignment of multi-modal 3D brain MRI volumes through both global geometric transformations and local deformable modeling[cite: 6, 7].

## Dataset: Multi-Label Brain MRI
[cite_start]The dataset utilized consists of 20 anonymized 3D MRI brain images, resampled to a consistent isotropic resolution of $2.0 \text{ mm}^3$ ($96 \times 116 \times 128$ voxels)[cite: 9, 10]. 
* [cite_start]**Atlas & Target Volumes:** Includes 15 "atlas" images and 5 "target" images for cross-subject registration[cite: 10].
* [cite_start]**Anatomical Segmentations:** Each volume is accompanied by a multi-label segmentation map covering approximately 140 distinct brain regions, following the Klein and Tourville labeling protocol[cite: 12, 13].

---

## Pipeline Architecture

### Phase I: Rigid and Affine Registration
[cite_start]I developed a global registration framework leveraging PyTorch’s autograd engine for iterative optimization[cite: 6]:
* [cite_start]**Geometric Transformations:** Implemented affine and rigid transformation matrices to handle global rotation, translation, scaling, and shearing[cite: 6].
* [cite_start]**Optimization:** Utilized gradient-based optimization to minimize image intensity differences, effectively aligning pairs of anatomical volumes[cite: 6].

### Phase II: Deformable Registration (LogDemons)
To account for non-rigid anatomical variability, I implemented a deformable registration suite:
* [cite_start]**LogDemons Framework:** Developed a PyTorch-based implementation of the LogDemons algorithm to compute dense, non-linear displacement fields[cite: 7].
* [cite_start]**Velocity Fields:** Managed registration through stationary velocity fields to ensure diffeomorphic (topology-preserving) mappings between subjects[cite: 7].

---

* [cite_start]**Framework:** PyTorch (leveraging auto-differentiation and GPU acceleration) [cite: 5, 18]
* **Language:** Python
* [cite_start]**Data Format:** NIfTI (.nii.gz) [cite: 10]
* [cite_start]**Visualization:** ITK-SNAP and Matplotlib for plotting cross-sectional slices and alignment overlays [cite: 20]

---
This project was completed as part of the BE 5370 Biomedical Image Analysis curriculum at the University of Pennsylvania[cite: 1].*