# EEG Deception Detection Baseline

Simple, reproducible pipeline that distinguishes **spontaneous lies** from **spontaneous truths** in a competitive two‑player card‑game dataset.

| Metric | Value |
|--------|-------|
| Accuracy | **0.63** |
| Macro F1 | **0.62** |
| Lie recall | 0.73 |
| Truth recall | 0.52 |

![Confusion matrix](confmat.png)

## Dataset
* **Title**: *An EEG Dataset of Neural Signatures in a Competitive Two‑Player Game Encouraging Deceptive Behavior*  
* **Authors**: Chen, Fazli & Wallraven (2024)  
* **Link**: <https://figshare.com/articles/dataset/24760827>  
30 EEG channels · 256 Hz · 484 player trials.

## Pipeline
1. Upload a `Player_*.mat` file → extract EEG + labels  
2. 1–40 Hz band‑pass, per‑epoch z‑score  
3. Log band‑power features (δ θ α β γ) + θ/α and β/α ratios  
4. Tuned Random‑Forest (1 000 trees, depth 10)  

Full code in **`EEG_Deception_Final.ipynb`** (8 cells, < 5 min runtime on Colab).

## Quick start
```bash
git clone https://github.com/angelinka19/neurosec-deception-eeg.git
cd neurosec-deception-eeg
pip install -r requirements.txt
jupyter notebook EEG_Deception_Final.ipynb
