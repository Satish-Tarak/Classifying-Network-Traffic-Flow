![Network Traffic Classification](network_traffic_project_banner.png)


# Classifying Network Traffic Flow — DDoS Intrusion Detection

A machine learning project that classifies network traffic flows as **BENIGN** or **DDoS**, helping identify potential Distributed Denial-of-Service attacks through flow-level network characteristics.

## Project Overview

Network intrusion detection is an important part of cybersecurity. This project develops and evaluates machine learning classifiers to distinguish normal network traffic from DDoS attack traffic.

The objective is to detect attacks while minimizing missed attacks (false negatives) and unnecessary alerts (false positives).

## 🔗 Project Links

| Resource | Link |
|---|---|
| Kaggle Notebook | [View Notebook](https://www.kaggle.com/code/season87/classifying-network-flow) |
| Kaggle Dataset | [View Dataset](https://www.kaggle.com/datasets/season87/dd0s-pcap-iscx) |
| GitHub Repository | [View Repository](https://github.com/Satish-Tarak/Classifying-Network-Traffic-Flow) |

## Dataset

- **Dataset:** `DDos.pcap_ISCX.csv`
- **Source:** CIC-IDS2017 dataset
- **Original size:** 225,745 network flows and 79 columns
- **Predictors:** 78 numerical CICFlowMeter features
- **Target:** `Label`
- **Classes:** `BENIGN` and `DDoS`

Each row represents a bidirectional network flow described by packet counts, packet sizes, flow duration, inter-arrival times, TCP flags, and other network statistics.

## Project Workflow

1. Dataset loading and understanding
2. Data-quality assessment
3. Data cleaning and duplicate removal
4. Exploratory Data Analysis (EDA)
5. Outlier detection and investigation
6. Feature relationships and correlation analysis
7. Feature engineering
8. Feature selection
9. Data splitting and leakage prevention
10. Baseline model development
11. Model comparison
12. Class imbalance assessment
13. Cross-validation and hyperparameter tuning
14. Ensemble learning
15. Final model evaluation
16. False-positive and false-negative analysis
17. Feature importance and model interpretability
18. Reusable prediction function and model saving

## Machine Learning Models

The notebook evaluates:

- Logistic Regression
- Decision Tree
- Random Forest
- Extra Trees
- XGBoost
- Soft Voting Classifier
- Stacking Classifier

**Final selected model:** XGBoost

## Final Model Results

The final model was evaluated on an untouched test set containing 44,623 flows.

| Metric | Result |
|---|---:|
| Accuracy | 99.987% |
| Macro F1-score | 99.986% |
| ROC-AUC | 99.998% |
| PR-AUC | 99.999% |
| False Positives | 0 |
| False Negatives | 6 |

The model correctly identified 25,598 out of 25,604 DDoS flows and produced no false alarms among 19,019 benign flows in this test set.

**Important:** These results represent unseen flows from the same dataset capture, not independent real-world network traffic.

## Feature Importance

The notebook uses native feature importance, permutation importance, grouped permutation importance, and SHAP analysis where applicable.

Important features identified include:

- `Fwd Packet Length Max`
- `Init_Win_bytes_forward`
- `Total Length of Fwd Packets`
- `Init_Win_bytes_backward`

These features describe packet sizes and TCP window characteristics that help distinguish the traffic patterns in this dataset.

## Technologies Used

- Python
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost
- SHAP
- Imbalanced-learn
- Jupyter Notebook

## Repository Structure

```text
Classifying-Network-Traffic-Flow/
│
├── Classifying_Network_Traffic_Flow(3).ipynb
├── README.md
├── requirements.txt
├── .gitignore
└── assets/
    └── project_banner.png
```

## Limitations

- The dataset represents a specific CIC-IDS2017 capture and attack scenario.
- The test set comes from the same capture as the training data.
- Very high test performance does not establish generalization to different networks, attack tools, or traffic distributions.
- Independent-dataset and real-world validation are necessary before deployment.

## Conclusion

This project demonstrates an end-to-end machine learning workflow for binary network traffic classification, from data-quality investigation and exploratory analysis to model selection, evaluation, interpretability, and reusable predictions.

The results provide a promising experimental baseline for DDoS traffic classification, with independent validation remaining an important next step.
