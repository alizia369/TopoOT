# Topology-Aware Optimal Transport for Source-Free Test-Time Adaptation in Anomaly Segmentation

[![NeurIPS 2026](https://img.shields.io/badge/NeurIPS-2026-4b44ce.svg)](https://neurips.cc/Conferences/2026)
[![arXiv](https://img.shields.io/badge/arXiv-2601.20333-b31b1b.svg)](https://arxiv.org/abs/2601.20333)
[![PDF](https://img.shields.io/badge/Paper-PDF-blue.svg)](https://arxiv.org/pdf/2601.20333)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Official implementation of **TopoOT** (NeurIPS 2026). Preprint: [arXiv:2601.20333](https://arxiv.org/abs/2601.20333).

> [Ali Zia](https://ali-zia.me/), [Usman Ali](https://scholar.google.com/citations?user=2A32xVQAAAAJ), [Umer Ramzan](https://scholar.google.com/citations?user=D3AhoccAAAAJ), [Abdul Rehman](https://scholar.google.com/citations?user=ZTuS-yUAAAAJ), Abdelwahed Khamis, [Wei Xiang](https://scholar.google.com/citations?user=VxQUr90AAAAJ)

## Abstract
Deep topological data analysis (TDA) offers a principled framework for capturing structural invariants such as connectivity and cycles that persist across scales, making it a natural fit for anomaly segmentation (AS). Unlike threshold-based binarisation, which produces brittle masks under test-time distribution shift (TTDS), TDA allows anomalies to be characterised as disruptions to global structure rather than local fluctuations. We introduce TopoOT, a topology-aware optimal transport (OT) framework for source-free test-time adaptation in AS. Our key innovation is Optimal Transport Chaining, which sequentially aligns persistence diagrams (PDs) across thresholds and filtrations, yielding geodesic stability scores that identify features consistently preserved across scales. These stability-aware pseudo-labels supervise a lightweight head updated online using only unlabelled target samples, without access to source data or target labels, with OT-consistency and contrastive objectives, ensuring robust adaptation under TTDS. Across standard 2D and 3D anomaly detection benchmarks, TopoOT achieves state-of-the-art performance, outperforming second-best methods by up to +24.1% mean F1 on 2D datasets and +10.2% on 3D AS benchmarks.

---

## 1) Environment

Create the conda environment from `environment.yml`:

```bash
conda env create -f environment.yml
```

## 2) Datasets (Official Download Links)

* **[MVTec AD (2D)](https://www.mvtec.com/company/research/datasets/mvtec-ad)** 
* **[MVTec 3D-AD](https://www.mvtec.com/company/research/datasets/mvtec-3d-ad)**
* **[VisA (2D)](https://github.com/amazon-research/spot-diff)**
* **[Real-IAD (2D)](https://realiad4ad.github.io/Real-IAD/)** 
* **[Anomaly-ShapeNet (3D)](https://github.com/Chopper-233/Anomaly-ShapeNet)**

After downloading, set the dataset path in `configs/patchcore.py`.

---

## 3) Repository structure

```
TopoOT/
├─ anomaly_scores/
│  └─ patchcore/
│     ├─ class1/
│     │  ├─ sample_000.npy
│     │  ├─ sample_001.npy
│     │  └─ ...
│     └─ class2/
│        └─ ...
├─ features/
│  └─ patchcore/
│     ├─ class1/
│     │  └─ features.pkl
│     └─ class2/
│        └─ features.pkl
└─ environment.yml
```

Example run (3D / CMM):
```bash
python patchcore-main.py "classname" i.e: "bottle"
```


## 4) Minimal run checklist

1. `conda env create -f environment.yml && conda activate <env-name>`  
2. Download a dataset (e.g., **MVTec-AD**) and set its path in `configs/patchcore.py`.  
3. Export anomaly maps into `anomaly_scores/patchcore/<class>/*.npy`.  
4. Export features into `features/patchcore/<class>/features.pkl`.  
5. Run main script.

---

## Citation

If you find this code useful, please cite:

```bibtex
@inproceedings{zia2026topoot,
  title     = {Topology-Aware Optimal Transport for Source-Free Test-Time Adaptation in Anomaly Segmentation},
  author    = {Zia, Ali and Ali, Usman and Ramzan, Umer and Rehman, Abdul and Khamis, Abdelwahed and Xiang, Wei},
  booktitle = {Advances in Neural Information Processing Systems (NeurIPS)},
  year      = {2026}
}
```

## License

Released under the [MIT License](LICENSE).
