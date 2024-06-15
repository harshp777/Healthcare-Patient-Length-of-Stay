# Predict Patients length of Stay

Workflow of the project 

![image](https://github.com/harshp777/Healthcare-Patient-Length-of-Stay/assets/58933098/0846d293-c001-48a6-ad56-df6834e086df)


# EDA


## Exploratory Data Analysis Hypotheses

### ---- Univariate Analysis ----
 
### 2. Does patients' length of stay (LOS) change with respect to `HOSPITAL_TYPE_CODE`?

### 3. Does patients' length of stay (LOS) change with respect to `CITY_CODE_HOSPITAL`?

### 4. Does patients' length of stay (LOS) change with respect to `HOSPITAL_REGION_CODE`?

### 5. `DEPARTMENT` of admission and its impact on LOS

### 6. `DEPARTMENT` X `HOSPITAL_REGION_CODE` and its impact on LOS

### 7. Does more `AVAILABLE_EXTRA_ROOMS_IN_HOSPITAL` impact a patients' LOS?

### 8. `TYPE_OF_ADMISSION` and its impact on LOS

### 9. `SEVERITY_OF_ILLNESS` and its impact on LOS

### 10. `AGE` and its impact on LOS

### 11. `ADMISSION_DEPOSIT` and its relation to LOS

### 12. Does more visitors come with patients who have more severe illness?

### 13. Is there any difference in the LOS for different `WARD_TYPE` & `WARD_FACILITY_CODE` in each `DEPARTMENT`?

### 14. Does `BED_GRADE` affect LOS of patients?

### 15. Does more visitors come when younger patients get admitted than the older patients?

### 16. What type of illness & admission does the majority of patients who are less than 30 years of age have, and which department are most of them getting admitted to?

### 17. Are patients below 40 years paying more `ADMISSION_DEPOSIT` when they get admitted to the hospital?


# Feature Engineering

### 1. Target column (LOS)
### 2. Type of Admission + Severity of Illness
### 3. Severity of Illness + Bed grade 
### 4. Department + Severity of Illness
### 5. Handle Null Values using Coalesce
### 6. Admission month & day


# Phase 1: Data Simulation and Prediction

### Feature Selection
- The union of top features was determined by calculating feature importance (>0.01) from various models such as Decision Tree and XGBoost.
- Selected features were then used to train the final models.

### Modeling
- The final dataset was trained using the following models:
  - Random Forest
  - Linear Regression
  - XGBoost (XGB)
- The XGBoost model was selected for further usage based on its performance metrics.

### Simulation
- For simulation, patient data from December 1st to December 31st was used to predict the LOS.
- The prediction notebook is scheduled to run at a specific time each day for 30 days, predicting and storing the scores back to Snowflake.
- For convenience, predictions were also generated in a single run for 30 iterations.
- For each instance whenever the notebook is trigerred and the predictions are stored in the snowflake, an email is sent to the registered email id.

![image](https://github.com/harshp777/Healthcare-Patient-Length-of-Stay/assets/58933098/cc839e59-32f4-4cde-a3fe-88d3b8c045c1)

![image](https://github.com/harshp777/Healthcare-Patient-Length-of-Stay/assets/58933098/0ecb04b7-4117-4819-93d2-97e5eb0ce67a)



### Completion
- Phase 1 is completed by storing the simulated data and predictions in Snowflake for 30 days.

# Phase 2: Data and Concept/Model Drift Monitoring alongwith retraining pipeline


### Data and Model Drift Monitoring
- I developed data drift monitoring using Alibi package which uses KS Test for numberical distribution and Chi-Square for categorical Data
- I developed concept/ model drfit monitoring using manually checking if the current metrics exceeds the previous training metrics(in our project case it is MAE and RMSE with the allowed threshold of 0.1)

  
