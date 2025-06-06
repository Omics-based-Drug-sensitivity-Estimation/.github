# 💊 Multi-Omics-Based Drug Sensitivity Estimation  
*6th YAICON — Spring 2025 · **Second Prize***

---

## 📌 Overview
Accurately predicting how a cancer cell line responds to a drug (IC-50) remains an open challenge: the outcome depends not only on the drug’s chemistry but also on the cell’s intricate molecular profile.  
We present an end-to-end deep-learning pipeline that **fuses three omics layers (GEP, MUT, CNV)** with advanced **drug-embedding models (ChemBERTa & graph-based GNN)** and a **bi-directional cross-attention mechanism**. Our approach improves upon the 2025 benchmark paper  
[*“Anticancer drug response prediction integrating multi-omics pathway-based difference features and multiple deep-learning techniques.”*](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1012905)

<p align="center">
  <img src="../assets/input.png" width="49%" />
  <img src="../assets/output.png" width="49%" />
</p>

---

## 🌱 Why we built this
| Baseline limitation | Our upgrade |
| ------------------- | ----------- |
| **Drug representation lacks structural cues** (only SMILES RNN) | **Two interchangeable drug encoders**<br>• *ChemBERTa* — language-style SMILES embedding<br>• *BGD* — graph transformer on molecular graphs |
| **Shallow “context attention”** can’t model complex drug-omics interplay | **Deep, bi-directional cross-attention** (drug ↔ each omics) giving **6 interaction maps** |

---

## 🔬 Data
| Source | Entities | Notes |
| ------ | -------- | ----- |
| **CCLE** | 688 cell lines | GEP (log₂ TPM + 1), MUT (0/1/2), CNV (log₂ discrete) |
| **GDSC2** | 233 drugs | Matched IC-50 ground-truth |
| **MSigDB – 619 KEGG pathways** | – | Used to derive pathway-difference statistics (Mann-Whitney U / χ²-G) |

---

## 🛠 Methodology
1. **Omics pathway features**  
   For every cell line × pathway, compute statistical separation between “in-pathway” and “out-pathway” genes → 3 feature matrices of size 1 × 619 (GEP, MUT, CNV).

2. **Drug embeddings**  
   *Choose one encoder at training time*  
   | Encoder | Key idea | Output shape |
   | ------- | -------- | ------------ |
   | **ChemBERTa** | Tokenise SMILES, pad to 256, take final hidden CLS | 1 × 384 |
   | **BGD** | Graph transformer over atoms/bonds + DeepChem node feats | 1 × 256 |

3. **Cross-attention block**  
   • Drug (Q) ↔ Omics (K,V) for each omics type, **two directions** (drug→omics, omics→drug) → 6 attention layers in total.  
   • Concatenate pooled outputs → stacked MLP → IC-50 regression.

<p align="center">
  <img width="721" alt="Image" src="https://github.com/user-attachments/assets/41ab2228-32ab-4d2f-b0c4-82d408cc3f87" />
</p>

*Implementation diagram above: original (top) vs. modified cross-attention (bottom).*

---

## 📂 Code & Repos

| Repository | Description |
| ---------- | ----------- |
| **[Drug-Sensitivity-Prediction-Pipeline](https://github.com/Omics-based-Drug-sensitivity-Estimation/Drug-Sensitivity-Prediction-Pipeline)** | Main training pipeline, model zoo, experiment scripts |
| **[DGL-Life-sci](https://github.com/Omics-based-Drug-sensitivity-Estimation/DGL-Life-sci)** | Custom extensions for graph-based drug encoders |

<details>
<summary>Model zoo snapshots</summary>

#### ChemBERTa Drug Embedding
<p align="center">
  <img width="333" alt="ChemBERTa" src="https://github.com/user-attachments/assets/9166787e-d33f-40ba-bce8-c465a705064e" />
</p>

#### Graph-Transformer Drug Embedding
<p align="center">
  <img width="305" alt="Graph" src="https://github.com/user-attachments/assets/f474ddbb-45e1-4ad6-bc99-8ab0bfc1fc74" />
</p>

</details>

---

## 📊 Results

<p align="center">
  <img src="https://github.com/user-attachments/assets/62b4dbd0-f510-4b20-95e9-4789627cb7c5" width="425" alt="Figure 1">
  <br><em>Figure 1. Drug embedding comparison (Original vs. Modified attention)</em>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/5f28a37e-4e18-4b83-8b3f-da5945e02404" width="425" alt="Figure 2">
  <br><em>Figure 2. Cross-attention variant performance</em>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/a4b6bc42-3e90-4d4f-80c2-3668d2330e41" width="700" alt="Figure 3">
  <br><em>Figure 3. Pearson r on cell-blinded split (scatter)</em>
</p>

Key takeaway : **+Improvement over the baseline when switching to ChemBERTa/BGD-Model + cross-attention. Full metrics in `/results/`.

---

## 🔗 Reference
* **PASO** – <https://github.com/queryang/PASO>

---

## 👥 Team

| Name | Role | GitHub |
| ---- | ---- | ------ |
| **Yoonjin Cho** | Team lead · Proposal · Multi-omics & ChemBERT modeling · Server ops · Experiments · Visualisation | [@darejinn](https://github.com/darejinn) |
| **Gyungdeok Bae** | Presenter · Model dev lead · PASO & GNN design · Troubleshooting · Attention modules | [@bgduck33](https://github.com/bgduck33) |
| **Junseo Ha** | Graph-based drug rep (GIN, AttFP, MPNN) · PASO analysis · Experiments | [@Carolyn-Ha](https://github.com/Carolyn-Ha) |
| **Yoonju Cho** | Attention improvement · Baseline experiments | [@whdsbwn](https://github.com/whdsbwn) |
| **Daeseong Kim** | Initial idea · Dataset/AWS support · *in vitro* validation | [@lemonardo1](https://github.com/lemonardo1) |

---

