# Adaptive Hybrid Network Security Framework Using ML and Quantum-Assisted Key Distribution

An ML-guided network security framework that detects attacks in IoT/network traffic and activates a simulated BB84 Quantum Key Distribution (QKD) session only for high-risk flows, reducing QKD overhead.

## Overview
Future quantum computers may break RSA and elliptic-curve cryptography, but applying QKD to all network traffic is costly. This project combines machine-learning-based intrusion detection with a three-level adaptive risk engine (LOW, MEDIUM, HIGH). Only HIGH-risk flows trigger the simulated secure session.

## Datasets
- **X-IIoTID** (Australia, 2021)
- **HQC-2026** (Bangladesh, 2026)
- **CIC-UNSW-NB15** (Canada, 2024)

Datasets are not included in this repository. Please download them from their original sources.

## Methods
- **ML models:** 12 supervised models trained and evaluated on each dataset
- **Adaptive Risk Engine:** classifies each flow as LOW, MEDIUM, or HIGH using the predicted attack probability (thresholds 0.35 and 0.70)
- **BB84 QKD simulation:** tested under clean, low-eavesdrop, and high-eavesdrop channel conditions
- **Attack-type identification:** a multiclass model labels each HIGH-risk flow, and a response engine recommends a security action
- **Explainability:** SHAP feature importance

## Results
| Dataset | Best Model | F1-score |
|---|---|---|
| X-IIoTID | LightGBM | 0.9971 |
| HQC-2026 | LightGBM | 0.8082 |
| CIC-UNSW-NB15 | LightGBM | 0.9580 |

- QKD overhead reduced by **51.6% to 81.5%** across the three datasets, compared to applying QKD to all traffic
- In the BB84 simulation, QBER stayed near zero on a clean channel and above the 11% security threshold under eavesdropping
- SHAP analysis ranked `Fwd Seg Size Min` as the top feature on HQC-2026 and CIC-UNSW-NB15

## Note
QKD is **simulated** in this project (BB84 protocol simulation), not run on real quantum hardware.




