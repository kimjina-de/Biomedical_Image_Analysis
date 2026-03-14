# Medical Image Registration Pipeline in PyTorch
**Biomedical Image Analysis | University of Pennsylvania**

## Project Overview
This project focuses on the implementation and optimization of core medical image registration algorithms using the **PyTorch** deep learning framework. The pipeline facilitates the alignment of multi-modal 3D brain MRI volumes through both global geometric transformations and local deformable modeling.

## Dataset: Multi-Label Brain MRI
The dataset utilized consists of 20 anonymized 3D MRI brain images, resampled to a consistent isotropic resolution of $2.0 \text{ mm}^3$ ($96 \times 116 \times 128$ voxels). 
* **Atlas & Target Volumes:** Includes 15 "atlas" images and 5 "target" images for cross-subject registration.
* **Anatomical Segmentations:** Each volume is accompanied by a multi-label segmentation map covering approximately 140 distinct brain regions, following the Klein and Tourville labeling protocol.

---

## Pipeline Architecture

### Phase I: Rigid and Affine Registration
A global registration framework leveraging PyTorch’s autograd engine for iterative optimization:
* **Geometric Transformations:** Implemented affine and rigid transformation matrices to handle global rotation, translation, scaling, and shearing.
* **Optimization:** Utilized gradient-based optimization to minimize image intensity differences, effectively aligning pairs of anatomical volumes.

### Phase II: Deformable Registration (LogDemons)
To account for non-rigid anatomical variability, I implemented a deformable registration suite:
* **LogDemons Framework:** Developed a PyTorch-based implementation of the LogDemons algorithm to compute dense, non-linear displacement fields.
* **Velocity Fields:** Managed registration through stationary velocity fields to ensure diffeomorphic (topology-preserving) mappings between subjects.

---

* **Framework:** PyTorch (leveraging auto-differentiation and GPU acceleration) 
* **Language:** Python
* **Data Format:** NIfTI (.nii.gz) 
* **Visualization:** ITK-SNAP and Matplotlib for plotting cross-sectional slices and alignment overlays 

---
This project was completed as part of the BE 5370 Biomedical Image Analysis curriculum at the University of Pennsylvania.*