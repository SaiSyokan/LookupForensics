# [IEEE ACCESS 2025] LookupForensics: A Large-Scale Multi-Task Dataset for Multi-Phase Image-Based Fact Verification

**LookupForensics** is a large-scale, multi-task dataset designed for **multi-phase image-based fact verification**.  
It supports four tightly connected tasks — **forgery identification**, **forgery localization**, **fact retrieval**, and **end-to-end fact verification** — enabling systematic evaluation of modern multimodal reasoning systems.

This dataset was introduced in [PDF](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=11059876):

> **Shuhan Cui**, Huy H. Nguyen, Trung-Nghia Le, Chun-Shien Lu, Isao Echizen  
> *LookupForensics: A Large-Scale Multi-Task Dataset for Multi-Phase Image-Based Fact Verification*  
> IEEE Access, 2025.

---

## 📝 Motivation

Real-world image-based disinformation often involves **content-preserving** or **content-aware edits** that subtly distort factual information.  
Traditional binary classifiers or purely pixel-level forgery detectors fail to fully capture these complexities.

LookupForensics addresses these challenges by:

- Offering a **multi-phase design** aligned with practical fact-checking workflows  
  (1) detect manipulations → (2) retrieve original evidence → (3) verify facts  
- Including **diverse manipulations** beyond simple synthetic forgeries  
- Providing a **large, scalable retrieval corpus** to test reasoning under ambiguity  
- Allowing **modular benchmarking** of each step or the full pipeline

---

## 📦 Dataset Overview

### **Image Statistics**
- **40,000 real images**
- **50,000 forged images** (10,000 per manipulation type)

### **Forgery Types**
1. **Copy-Move**  
2. **Image Splicing**  
3. **Object Removal**
4. **Colorization**
5. **Real-World Forgeries** (collected from online posts)

### **Annotations**
- Image-level **real/fake** labels  
- **5-way forgery type** labels  
- **Pixel-level masks** (copy-move, splicing, removal)  
- **Bounding boxes / instances** for retrieval evaluation  
- **Multiple difficulty levels** via controlled augmentations  
  (compression, resizing, noise, cropping, rotation)

---

## 🔍 Fact Retrieval Corpus

To support scalable fact verification, LookupForensics includes:

- **~20,000 manipulated queries**
- **~60,000 distractor queries**
- **~800,000 reference images** in the evidence corpus

Both **global retrieval** and **local retrieval** (using forgery masks/segments) are supported.

---

## 🧪 Tasks Supported

### **1. Forgery Identification**
- Binary classification (Real vs. Fake)  
- 5-class manipulation classification  

### **2. Forgery Localization**
- Pixel-level detection of manipulated regions  
- Bounding box localization for segment-level retrieval  

### **3. Fact Retrieval**
- **Global retrieval:** match full manipulated image to its original  
- **Local retrieval:** match manipulated region to the correct region in the corpus  
- Evaluate retrieval difficulty across augmentation levels  

### **4. End-to-End Fact Verification (Two-Phase Framework)**
LookupForensics enables benchmarking of the **two-phase verification pipeline**:

1. **Phase I — Forgery Identification**  
   Detect forgeries and identify manipulated regions

2. **Phase II — Fact Retrieval**  
   Retrieve corresponding original reference(s)

---

## 🧩 Dataset Structure

```text
LookupForensics/
├── data/
│   ├── images/                 # Real and forged images
│   ├── masks/                  # Pixel-level annotations (copy-move, splicing, removal)
│   ├── metadata/               # CSV/JSON: labels, bbox, difficulty levels
│   ├── retrieval/
│   │   ├── queries/            # Forged + distractor queries
│   │   ├── corpus/             # ~800k reference images
│   │   └── indices/            # Predefined splits for benchmarking
│   └── augmentations/          # Multi-level augmentations for robustness testing
├── code/
│   ├── identification/         # Forgery classification & detection baselines
│   ├── localization/           # Pixel-level segmentation models
│   ├── retrieval/              # Global + local retrieval models
│   ├── verification/           # Full two-phase verification pipeline
│   └── utils/
├── LICENSE
├── CITATION.cff
└── README.md
```

---

## 📥 Download

Dataset release is currently in preparation.  
Links will be provided here once available.

---

## 📚 Citation

If you use LookupForensics in your research, please cite:

```bibtex
@ARTICLE{11059876,
  author={Cui, Shuhan and Nguyen, Huy H. and Le, Trung-Nghia and Lu, Chun-Shien and Echizen, Isao},
  journal={IEEE Access}, 
  title={LookupForensics: A Large-Scale Multi-Task Dataset for Multi-Phase Image-Based Fact Verification}, 
  year={2025},
  volume={13},
  number={},
  pages={136505-136523},
  keywords={Forgery;Artificial intelligence;Splicing;Feature extraction;Multitasking;Accuracy;Visualization;Transformers;Reliability;Digital images;Datasets;neural networks;forgery detection;image copy detection;fact verification},
  doi={10.1109/ACCESS.2025.3584395}
}
```

## 📩 Contact

For questions, early access, or collaboration:

Shuhan Cui

The University of Tokyo / National Institute of Informatics

📧 syokan [at] g.ecc.u-tokyo.ac.jp
