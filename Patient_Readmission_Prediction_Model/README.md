# Patient Readmission Prediction Model

## **Project Overview**
This project aims to develop a machine learning model to predict patient readmissions, an essential task for improving healthcare quality, optimizing resource allocation, and reducing hospital penalties associated with high readmission rates. Predicting patient readmission risk allows healthcare providers to implement early interventions, ultimately reducing readmission rates and associated costs.

## **Problem Statement**
Hospitals and healthcare facilities face significant challenges when it comes to patient readmissions. Unplanned readmissions contribute to higher healthcare costs, reduced patient satisfaction, and can signal poor healthcare quality. The goal of this project is to predict whether a patient will be readmitted after discharge based on various medical and demographic factors.

### **Key Benefits:**
1. **Improved Patient Care**: By identifying high-risk patients, healthcare providers can implement targeted interventions to improve patient outcomes.
2. **Cost Reduction**: Hospitals can avoid penalties imposed by Medicare or other payers for high readmission rates.
3. **Resource Optimization**: Allocating healthcare resources more efficiently by focusing on high-risk patients.

## **Dataset Overview**
The dataset used in this project contains several features related to patient demographics, medical history, and treatment. These features were used to predict the binary target variable: **readmission (0 or 1)**.

### **Key Columns in the Dataset:**
- **`time_in_hospital`**: The number of days the patient stayed in the hospital.
- **`num_lab_procedures`**: Number of lab procedures performed.
- **`num_medications`**: Number of medications the patient was prescribed.
- **`number_diagnoses`**: Number of diagnoses made during the patient's hospital stay.
- **`number_inpatient`**: Number of inpatient visits.
- **`number_outpatient`**: Number of outpatient visits.
- **`number_emergency`**: Number of emergency visits.
- **`diabetesMed_Yes`**: Whether the patient is taking diabetes medication.
- **`race_Caucasian`**, **`race_AfricanAmerican`**, etc.: Encoded race of the patient.
- **`gender_Female`**: Gender of the patient.
- **`readmitted`**: The target variable indicating whether the patient was readmitted (1 for yes, 0 for no).

The dataset also contains several boolean columns encoding medication usage (e.g., metformin, insulin), and diagnoses (e.g., diagnosis codes like `diag_1_428` and `diag_1_414`).

## **Modeling Approach**

### **1. Data Preprocessing**
- The dataset underwent preprocessing to handle missing values, convert categorical variables to numerical representations, and ensure consistency in the feature types.
- **Boolean Feature Conversion**: The dataset contains several boolean columns (e.g., `race_Caucasian`, `diabetesMed_Yes`), which were converted to numerical form (`0` or `1`).
- **Handling Missing Values**: The missing values in the dataset were imputed or removed to ensure the quality of the data.

### **2. Feature Engineering**
- **Numerical Features**: These include patient-related metrics like the number of inpatient visits, outpatient visits, lab procedures, and medications.
- **Categorical Features**: These include patient demographics (race, gender) and medical information (diagnosis codes, medications).
- **Target Variable**: The target variable (`readmitted`) is binary, where `1` indicates that the patient was readmitted, and `0` indicates no readmission.

### **3. Model Selection**
The primary model used for this prediction task was **XGBoost**, a powerful gradient-boosting algorithm known for its efficiency and accuracy in structured/tabular data. XGBoost was chosen due to its ability to handle imbalanced data and its strong performance in classification tasks.

### **4. Model Evaluation**
- The dataset was split into training and testing sets using an 80-20 ratio. 
- The model was evaluated using the following metrics:
  - **Accuracy**: Proportion of correctly classified instances.
  - **Precision**: Proportion of positive predictions that were correct.
  - **Recall**: Proportion of actual positives that were correctly identified.
  - **F1 Score**: Harmonic mean of precision and recall.
  - **ROC AUC**: Measures the model's ability to distinguish between the two classes (readmitted and not readmitted).

### **5. SHAP (SHapley Additive exPlanations) for Model Interpretability**
To explain the model’s predictions and understand the contribution of each feature to the predictions, **SHAP** was used.

- **SHAP Summary Plot**: This plot visualizes the impact of each feature on the model’s predictions across the entire dataset. Features like `number_inpatient`, `num_medications`, and `number_diagnoses` showed significant influence on the model’s decision-making process.
  
- **SHAP Dependence Plot**: A dependence plot for key features (e.g., `number_inpatient`) reveals how SHAP values change with the feature values. This helped us explore the interaction effects between features like `num_medications` and `number_inpatient`.
  
- **SHAP Waterfall Plot**: Waterfall plots were used to break down individual predictions, showing how each feature contributed positively or negatively to a given prediction.

### **Model Results**

The model demonstrated strong predictive performance across several key metrics. Notably:
- **Accuracy**: [insert value]
- **Precision**: [insert value]
- **Recall**: [insert value]
- **F1 Score**: [insert value]
- **ROC AUC**: [insert value]

These results indicate that the model is well-suited for predicting patient readmissions, offering a valuable tool for healthcare providers aiming to improve patient care and reduce costs.

## **Conclusion and Next Steps**

### **Conclusion**
The Patient Readmission Prediction Model offers a valuable approach to tackling hospital readmission challenges. By accurately identifying high-risk patients, healthcare providers can target interventions that improve outcomes and reduce costs. The integration of SHAP values provides crucial interpretability, ensuring the model's decisions are transparent and understandable for clinical use.
