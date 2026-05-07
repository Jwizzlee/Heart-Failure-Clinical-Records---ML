# Heart Failure Clinical Records 
# Core idea is to take measurements of (datesage,anaemia,creatinine_phosphokinase,diabetes,ejection_fraction,high_blood_pressure,platelets,serum_creatinine,serum_sodium,sex,smoking,time) and to classiy by death event

'# CSCI 3329 — Homework 3 Report
## 1. Dataset
- JOSUE TORRES / UCI Machine Learning Repository  / 299 / 
- Class distribution (table or bar chart)
    - Survival (0): 203 samples
    - Death (1): 96 samples 

## 2. Preprocessing
- **Missing-value handling:** I chose to drop the `time` column along with any ID data. Dropping `time` prevents data leakage (as it is often recorded after the event) and ensures models rely only on health markers.
- **Encoding and scaling:** I used `LabelEncoder` for target formatting and applied `StandardScaler` to all features to ensure consistency across different measurement units (e.g., age vs. platelets).

## 3. Part 2 — Algorithm Comparison

| Algorithm | Mean Accuracy | Std Deviation |
| :--- | :---: | :---: |
| Linear Classifier | 0.6644 | 0.0943 |
| Logistic Regression | 0.7356 | 0.0777 |
| KNN | 0.6865 | 0.0825 |
| Gaussian NB | 0.7033 | 0.0795 |

## 4. Part 3 — Feature Selection

| Algorithm | Size | Mean Acc | Std Dev |
| :--- | :---: | :---: | :---: |
| Linear Classifier | 5 | 0.6643 | 0.1096 |
| Logistic Regression | 5 | 0.7661 | 0.0740 |
| KNN | 5 | 0.7392 | 0.0780 |
| Gaussian NB | 5 | 0.7507 | 0.0806 |
| Neural Network | 5 | 0.7454 | 0.0752 |

### Optimized Feature Subsets:
* **Linear Classifier:** age, ejection_fraction, serum_creatinine, serum_sodium, sex
* **Logistic Regression:** age, creatinine_phosphokinase, ejection_fraction, serum_creatinine, sex
* **KNN:** ejection_fraction, platelets, serum_creatinine, serum_sodium, sex
* **Gaussian NB:** age, diabetes, ejection_fraction, platelets, sex
* **Neural Network:** ejection_fraction, high_blood_pressure, serum_creatinine, sex, smoking

## 5. Discussion
- **Part 2 vs Part 3 Comparison:** The clear takeaway was that "less is more." By reducing the feature count from 11 to 5, Logistic Regression improved from 73.6% to 76.61% and KNN jumped from 68.7% to 73.92%. This "noise reduction" proved that some features (like anaemia) did not contribute strongly to survival prediction.
- **Per-algorithm Observations:** - **Logistic Regression:** The best performer (76.6% accuracy, 0.0740 STD). It was the most stable model, suggesting a strong correlation between `serum_creatinine`, `ejection_fraction`, and mortality.
    - **KNN:** Saw a 5% accuracy jump because distance-based calculations are easily confused by irrelevant features; forward selection cleared this "fog."
    - **Gaussian NB:** Improved to 75.07% as dropping redundant features helped satisfy its independence assumption.
    - **Main Features:** Across all models, `ejection_fraction`, `serum_creatinine`, and `sex` were consistent top predictors.
- **Limitations and Improvement:**
    - **Sample Size:** 299 samples is small; more data would help improve reliability.
    - **Class Imbalance:** The 2:1 ratio of survivors to deaths could be addressed in the future with oversampling techniques like SMOTE.

## 6. Reproduction
- **Python Version:** 3.12+
- **Key Libraries:** pandas (3.0.2), scikit-learn (1.8.0), numpy (2.4.4), matplotlib (3.10.9)
- **Run Command:** Open `CSCI3329_HW3.ipynb` in VS Code and select **"Run All"**.
- **Alternative Terminal Execution:**
  ```bash
  pip install nbconvert
  jupyter nbconvert --to notebook --execute CSCI3329_HW3.ipynb