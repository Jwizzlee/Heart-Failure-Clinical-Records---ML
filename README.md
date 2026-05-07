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
    After Completeing Part 2 and 3 the clear difference was that less is more by reducing the feature count from 11 to 5 Logistic regression improved from 73.6% tin 76.61% and Knn going from 68.7% to 73.92% in their accuracy
    By reducing the features from 11 to 5 we perfrmed a 'nosie reduction' as some features did not contribute strongly to the survival prediction (anaemia, high_blood_preassure)
- Per-algorithm observations
    Logistic Regregression : This was the best perfomer with accuracy of 76.6% and STRD of .740 being the most stable and accurate model suggesting corralation of serum_creatinine and ejection_fraction 
    KNN : Knn saw a big jump of 5% in accuracy because it relies on calculating disctance between point and confused by irrelevant features. With the foward selection clearing up the fog making it better
    Gausssian NB :   Improved from 75.07% since this it assumes features are independant dropping features that are redundant
    Main Features: Accros all models ejection_fraction, serum_creatinine, and sex are consistant top predictors.

- Limitations and ideas for improvement
    Sample Size: Increase sample size , more data would help improve reliability
    Class Imbalance :The dataset has a 2:1 ratio of surivvors to deaths 

## 6. Reproduction
- **Python Version:** Python 3.13.12
- **Key Libraries:** pandas: 3.0.2, scikit-learn: 1.8.0 , numpy: 2.4.4, matplotlib: 3.10.9 (for any visualizations)
- **Run Command:**   CSCI3329_HW3.ipynb in VS Code or Jupyter Notebook and select "Run All" 
                    {
                     pip install nbconvert
                     jupyter nbconvert --to notebook --execute CSCI3329_HW3.ipynb
                    }