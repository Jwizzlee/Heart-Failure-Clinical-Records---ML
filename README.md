# Heart Failure Clinical Records 
# Core idea is to take measurements of (datesage,anaemia,creatinine_phosphokinase,diabetes,ejection_fraction,high_blood_pressure,platelets,serum_creatinine,serum_sodium,sex,smoking,time) and to classiy by death event
# I handled missing values by dropping rows with NaN. I used LabelEncoder for the target class and StandardScaler to normalize the numerical features, which is essential for the distance-based KNN algorithm

'# CSCI 3329 — Homework 3 Report
## 1. Dataset
- JOSUE TORRES / UCI Machine Learning Repository  / 299 / 
- Class distribution (table or bar chart)
    - Survival (0): 203 samples
    - Death (1): 96 samples
## 2. Preprocessing
- Missing-value handling
   I chose to drop the 'time' column along with any id data. Since droping time prevents leakage and ensure the models rely only on health markers
- Encoding and scaling decisions, with rationale
    I used `LabelEncoder` to ensure the target and any categorical features were correctly formatted as integers. I applied `StandardScaler` to all features
## 3. Part 2 — Algorithm Comparison
| Algorithm | Mean Accuracy | Std |
|-----------|---------------|-----|
| ... | ... | ... |
## 4. Part 3 — Feature Selection
- Search method and justification
| Algorithm | Best Feature Subset | Mean Accuracy | Std |
|-----------|--------------------|---------------|-----|
## 5. Discussion
- Part 2 vs Part 3 comparison
- Per-algorithm observations
- Limitations and ideas for improvement
Page 9 / 12
CSCI 3329 OOP in Python Spring 2026
## 6. Reproduction
- Python version, key library versions
- Run command (e.g., `python main.py`)'