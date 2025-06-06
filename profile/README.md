## 💊 MultiOmics based Drug Sensitivity Estimation - 6th Yaicon
### 🏆 2025 Spring 6th YAICON SECOND PRIZE


## Task Explanation
<p align="center">
  <img src="../assets/input.png" width="49%" />
  <img src="../assets/output.png" width="49%" />
</p>

# Repositories 👀

## [Drug-Sensitivity-Prediction-Pipeline](https://github.com/Omics-based-Drug-sensitivity-Estimation/Drug-Sensitivity-Prediction-Pipeline)
#### ChemBERT based Drug embedding
  <p align="center">
  <img width="333" alt="Image" src="https://github.com/user-attachments/assets/9166787e-d33f-40ba-bce8-c465a705064e" />
  </p>
  
  > implemented by [Yoonjin Cho](https://github.com/darejinn)
  
#### Graph-Transformer based Drug embedding
  <p align="center">
  <img width="305" alt="Image" src="https://github.com/user-attachments/assets/f474ddbb-45e1-4ad6-bc99-8ab0bfc1fc74" />
  </p>
  
  > implemented by [GyungDeok Bae](https://github.com/bgduck33)
    
#### Original Attention, Modified Cross attention
  <p align="center">
  <img width="721" alt="Image" src="https://github.com/user-attachments/assets/41ab2228-32ab-4d2f-b0c4-82d408cc3f87" />
  </p>
  
  > implemented by [GyungDeok Bae](https://github.com/bgduck33),[Yoonju Cho](https://github.com/whdsbwn), [Yoonjin Cho](https://github.com/darejinn)

## [DGL-Life-sci](https://github.com/Omics-based-Drug-sensitivity-Estimation/DGL-Life-sci)
- DGL-Life-Sci based Drug embedding
  > implemented by [Junseo Ha](https://github.com/Carolyn-Ha) 

## Evaluation
SMILES = PASO
<p align="center">
  <img src="https://github.com/user-attachments/assets/62b4dbd0-f510-4b20-95e9-4789627cb7c5" width="425" alt="Figure 1 – …">
  <br><em>Figure 1. Comparison of drug embedding models (above-original attenton, below-modified attention</em>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/5f28a37e-4e18-4b83-8b3f-da5945e02404" width="425" alt="Figure 2 – …">
  <br><em>Figure 2. Performance of our modified cross attention</em>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/a4b6bc42-3e90-4d4f-80c2-3668d2330e41" width="700" alt="Figure 3 – …">
  <br><em>Figure 3. Pearson Correlation Score and scatter plot for cell-blinded dataset</em>
</p>

  </p>

## Reference
### [PASO: Drug Response Prediction Model](https://github.com/queryang/PASO)

## Members
### [Yoonjin Cho](https://github.com/darejinn) (Team Lead)
Project proposal & overall leading, multi-omics & ChemBERT-based modeling, server management, model experiments, and result visualizations

### [GyungDeok Bae](https://github.com/bgduck33) (Presenter)
Model development lead, PASO proposal, GNN-based embedding design, server troubleshooting, attention mechanism development, model experiments

### [Junseo Ha](https://github.com/Carolyn-Ha) 
Graph-based drug representation (DGLlife GIN, AttFP, MPNN), PASO architecture analysis, model experiments

### [Yoonju Cho](https://github.com/whdsbwn)
Attention mechanism enhancement, PASO baseline model experiments, model experiments

### [Daeseong Kim](https://github.com/lemonardo1)
Initial ideation, dataset/server (AWS) support, in vitro validation
