# Heart Failure Clinical Records 
# Core idea is to take measurements of (datesage,anaemia,creatinine_phosphokinase,diabetes,ejection_fraction,high_blood_pressure,platelets,serum_creatinine,serum_sodium,sex,smoking,time) and to classiy by death event

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
Algorithm            | Mean Accuracy   | Std Deviation  
-------------------------------------------------------
Linear Classifier    | 0.6644         | 0.0943
Logistic Regression  | 0.7356         | 0.0777
KNN                  | 0.6865         | 0.0825
Gaussian NB          | 0.7033         | 0.0795

## 4. Part 3 — Feature Selection
Algorithm            | Size  | Mean Acc   | Std Dev   
-----------------------------------------------------------------
Linear Classifier    | 5     | 0.6643   | 0.1096
Logistic Regression  | 5     | 0.7661   | 0.0740
KNN                  | 5     | 0.7392   | 0.0780
Gaussian NB          | 5     | 0.7507   | 0.0806
Neural Network       | 5     | 0.7454   | 0.0752

--- FINAL OPTIMIZED TABLE ---
Linear Classifier:      [np.str_('age'), np.str_('ejection_fraction'), np.str_('serum_creatinine'), np.str_('serum_sodium'), np.str_('sex')]
Logistic Regression:    [np.str_('age'), np.str_('creatinine_phosphokinase'), np.str_('ejection_fraction'), np.str_('serum_creatinine'), np.str_('sex')]
KNN:                    [np.str_('ejection_fraction'), np.str_('platelets'), np.str_('serum_creatinine'), np.str_('serum_sodium'), np.str_('sex')]
Gaussian NB:            [np.str_('age'), np.str_('diabetes'), np.str_('ejection_fraction'), np.str_('platelets'), np.str_('sex')]
Neural Network:         [np.str_('ejection_fraction'), np.str_('high_blood_pressure'), np.str_('serum_creatinine'), np.str_('sex'), np.str_('smoking')]

## 5. Discussion
- Part 2 vs Part 3 comparison
- Per-algorithm observations
- Limitations and ideas for improvement
Page 9 / 12
CSCI 3329 OOP in Python Spring 2026
## 6. Reproduction
- Python version, key library versions
- Run command (e.g., `python main.py`)' 