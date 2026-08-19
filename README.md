# 💊 AI-Driven Drug-Target Binding Affinity Predictor

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![PyTorch Geometric](https://img.shields.io/badge/PyTorch_Geometric-GNN-orange)
![RDKit](https://img.shields.io/badge/RDKit-Cheminformatics-green)
![Streamlit](https://img.shields.io/badge/Streamlit-App-red)

An end-to-end Bio-AI pipeline that predicts small-molecule drug binding affinity ($\text{pK}_{\text{d}} = -\log_{10} \text{K}_{\text{d}}$) directly from 2D molecular structures using **Graph Convolutional Networks (GCN)** and **PyTorch Geometric**.

---

## 🔬 Scientific & Computational Background

[cite_start]In computational drug discovery, determining how tightly a candidate drug molecule binds to its target protein is essential for lead optimization[cite: 646]. 
[cite_start]Rather than relying purely on tabular 2D fingerprints (ECFP), this project converts raw chemical **SMILES strings** into mathematical graph objects $G = (V, E)$[cite: 647]:
* [cite_start]**Nodes ($V$):** Atoms encoded with 4 chemical descriptors[cite: 647]:
  1. Atomic Number
  2. Degree (Connectivity)
  3. Aromaticity Indicator
  4. Hybridization State ($sp, sp^2, sp^3$)
* [cite_start]**Edges ($E$):** Covalent chemical bonds between atoms[cite: 647].

---

## 🧠 Neural Network Architecture

[cite_start]The prediction engine is a multi-layer Graph Convolutional Network[cite: 648]:
1. [cite_start]**Graph Convolutions:** 3-layer `GCNConv` message passing with Batch Normalization (`BatchNorm1d`) and ReLU activations[cite: 648].
2. [cite_start]**Readout Layer:** Global Mean Pooling (`global_mean_pool`) to aggregate variable-sized atom features into a fixed molecule-level vector[cite: 649].
3. [cite_start]**Dense Prediction Head:** Fully connected layers to output the continuous binding affinity score ($\text{pK}_{\text{d}}$)[cite: 650].

---

## 📊 Model Performance

[cite_start]Evaluated on benchmark small-molecule kinase inhibitors and ligands[cite: 651]:

| Metric | Baseline GNN | Enhanced Multi-Layer GNN |
| :--- | :--- | :--- |
| **$R^2$ Score** | `0.0353` | **`0.9665`** |
| **RMSE** | `1.9044` | **`0.3551`** |

---

## 🚀 Installation & Interactive Demo

### 1. Clone & Install Dependencies
```bash
git clone [https://github.com/](https://github.com/)<your-username>/ai-drug-binding-predictor.git
cd ai-drug-binding-predictor
pip install -r requirements.txt