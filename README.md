# DATA304 Final Project  
## Hierarchical Multi-Label Text Classification (Weak Supervision)

This repository contains the code for an **DATA304 final project** on hierarchical multi-label text classification under **weak supervision**.

---

## Task & Constraints

- **Dataset**: Amazon product descriptions  
- **Labels**: 531 classes organized as a DAG taxonomy  
- **Supervision**: No human-annotated labels (silver labels only)
- **Constraints**:
  - Frozen BERT encoder (no fine-tuning on Amazon data)
  - No rule-based hierarchy enforcement at inference

Each document may have **multiple labels (2–3)** and predictions must respect **parent–child relations**.

---

## Method Overview

The pipeline consists of four stages:

1. **Silver Label Generation**
   - Keyword matching between text and class keywords
   - Keyword-matched classes = *core labels*
   - Ancestors added via hierarchy expansion

2. **Stage 1: Core-Aware Training (Teacher)**
   - Frozen BERT document encoder
   - Hierarchy-aware label modeling
   - Core-aware weighted BCE loss

3. **Stage 2: Soft Self-Training**
   - Teacher generates soft targets
   - Soft labels reduce noise from hard pseudo labels

4. **Stage 3: Confidence-Aware Training (Student)**
   - Samples weighted by label confidence
   - Early stopping based on validation Sample-F1

Hierarchy-aware inference combines **local (GAT)** and **global (path-based)** signals using multi-head attention.

---

## Reproducibility

- Fixed random seeds used throughout
- Experiments can be run in order using the notebooks above`
- .pth File Link = https://drive.google.com/drive/folders/1Vgz2qQqheWOmM5RH6pyxPqtEs8FzxIle?usp=sharing

---

## Evaluation

- **Sample-level F1** 
- **Hierarchy Violation Rate (HVR)**
- **PCA / t-SNE** for representation analysis

**Best Kaggle F1**: **0.25581**

---

## Author

Julia Irsalina  
DATA304 – Final Project



