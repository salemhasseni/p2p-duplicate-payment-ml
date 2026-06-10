# Duplicate Payment Risk Predictor
**BPI P2P OCEL 2.0 — Process Mining Portfolio · Project 2**

## Overview
This project is the direct continuation of [Project 1 — OCPM Audit](https://salemhasseni.github.io/ocpm-p2p-process-mining/ocpm_p2p_report.html).

The audit identified 188 payment objects executed 2–5×, exposing €2.39M in duplicate
payments over 30 months with no automated detection. This model operationalizes that
finding — predicting which purchase orders are at risk of generating a duplicate payment
before execution.

## Approach
- Label derivation from the OCEL 2.0 object graph, consistent with Project 1 methodology
- Two rounds of leakage detection and removal
- Feature engineering from pre-payment process timing and payment object attributes
- Random Forest binary classifier with stratified evaluation

## Results
| Metric | Value |
|---|---|
| ROC-AUC | 0.60 |
| Recall — Duplicate class | 46% |
| Precision — Duplicate class | 28% |

Performance ceiling is explained by anonymisation — vendor ID, AP user ID, and document
type are absent from the log. In a live SAP extraction, AUC is expected to exceed 0.80.

## Stack
Python 3 · pandas · scikit-learn · OCEL 2.0  
Dataset: [BPI P2P OCEL 2.0](https://zenodo.org/record/8412919) (Zenodo)

## View the notebook
[Open in nbviewer](https://nbviewer.org/github/salemhasseni/p2p-duplicate-payment-ml/blob/main/duplicate_payment_predictor.ipynb)
