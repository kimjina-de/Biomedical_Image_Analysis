# Ex Vivo 7T Brain MRI Segmentation Pipeline
**Biomedical Image Analysis | University of Pennsylvania**

## Project Overview
This project involved developing a multi-phase computational pipeline for the processing and automated segmentation of **7 Tesla (7T) ex vivo MRI scans** of the human brain. The core objective was to improve tissue segmentation accuracy in the presence of significant intensity inhomogeneity (dropout artifacts) and to train a deep learning model (**nnU-Net**) to automate the classification of Gray Matter (GM), White Matter (WM), and background.

## Dataset: 7T Ex Vivo MRI
The dataset comprises anonymized ex vivo MRI scans from 33 brain donors via the **UPenn Alzheimer’s Disease and Frontotemporal Dementia Research Centers**.
* **T2-weighted Scans:** High-resolution ($0.3 \text{ mm}^3$ isotropic) providing excellent GM/WM contrast, though subject to "dropout artifacts" (signal loss) in the anterior and posterior regions.
* **CISS Scans:** Constructive Interference in Steady State ($0.5 \text{ mm}^3$ isotropic) scans with higher signal stability, utilized for anatomical masking and registration support.

---

## Pipeline Architecture

### Phase 1: Artifact Correction & Intensity Normalization
To mitigate 7T-specific magnetic field inhomogeneities, I implemented a robust preprocessing workflow:
* **Bias Field Correction:** Applied the **N4 algorithm (SimpleITK)** to T2-weighted scans. This involved complex downsampling using **Recursive Gaussian smoothing** to prevent aliasing.
* **Statistical Evaluation:** Quantified the correction success using **Cohen’s $d$ statistics**. This measured the separability of tissue intensity classes (WM vs. GM and WM vs. Background) to ensure the normalization improved automated segmentation readiness.

### Phase 2: Multi-Modal Patch Extraction & QC
To prepare the high-resolution data for deep learning, I developed a Python-based sampling strategy:
* **3D Patch Extraction:** Generated $64^3$ voxel patches from N4-corrected T2 and CISS scans.
* **Constraint-Based Sampling:** Implemented logic to ensure each patch contained $>50\%$ brain tissue with $<20\%$ volumetric overlap between samples.
* **Quality Control (QC):** Performed visual registration audits in **ITK-SNAP**, rejecting samples with poor T2-CISS alignment to maintain high training data integrity.

### Phase 3: Deep Learning Segmentation (nnU-Net)
The final phase utilized the **nnU-Net** framework for automated 3D segmentation:
* **Data Engineering:** Architected the `nnUNet_raw` directory structure and generated `dataset.json` metadata for 3D U-Net training.
* **Inference:** Deployed the model on unseen whole-hemisphere test volumes.
* **Analysis:** Evaluated model generalization, specifically observing how the network handled global anatomical structures despite being trained only on localized 3D patches.

---

* **Languages:** Python
* **Primary Libraries:** SimpleITK, NumPy, nnU-Net v2
* **Specialized Software:** ITK-SNAP (3D Visualization & Manual QC)

---
*: This project was completed as part of the BE 5370 Biomedical Image Analysis curriculum at the University of Pennsylvania.*