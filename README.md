# Autism Diagnosis Classification – Machine Learning Project

This project focuses on analyzing a medical dataset related to early autism diagnosis in toddlers using the Q-Chat-10 test. Multiple machine learning approaches were applied, including feature selection, dimensionality reduction, hypothesis testing, parametric and non-parametric classification, and neural networks. The goal was to determine which classifier provides the best performance for this type of medical decision-support problem.

---

## Dataset Overview

https://www.kaggle.com/datasets/fabdelja/autism-screening-for-toddlers
The dataset contains **1054 samples**, each describing:
- Answers to the **Q-Chat-10 Toddler test** (variables A1–A10)
- Age in months  
- Sex  
- Ethnicity  
- Family history of autism  
- Whether the child was born with jaundice  
- Who completed the test (family member / clinician / self-reported)

Several preprocessing steps were performed:
- Cleaning inconsistent categorical values  
- Grouping low-frequency ethnic classes  
- One-hot encoding categorical features  


## Feature Selection

Two approaches were applied:

### **1. Information Gain**
Top informative features:
- A9, A5, A6, A7, A4, A1, A2, A8, A3  
- Age in months  

### **2. Correlation Analysis**
Pearson correlation identified A9 and A6 as most correlated with the target class.

Both methods confirmed that **test-related attributes** are more relevant than demographic ones.

---

## 📉 Dimensionality Reduction (LDA)

Linear Discriminant Analysis (LDA) was applied to reduce dimensionality while preserving class separability.

Key findings:
- Only **one component** is required (because the problem is binary classification).
- The first eigenvalue captures almost all discriminative information.

---

## Classification Methods

### **1. Hypothesis Testing (Bayes Minimum Error Rule)**
- **Accuracy:** 92.45%  
- Performs well but produces more false positives (acceptable in medical use cases).

### **2. Parametric Linear Classifier**
- Accuracy without weighting: 92.92%  
- With adjusted class weights (favoring positive diagnoses): **93.87%**  
- Useful when decision thresholds must be manually controlled.

### **3. K-Nearest Neighbors (KNN)**
- Optimal k determined via K-fold cross-validation: **k = 41**
- **Accuracy:** 96.31%  
- **Best overall performance**  
- Simple intuitive model, but memory-heavy.

### **4. Neural Networks**
Three architectures tested:

| Model | Accuracy | Notes |
|-------|----------|-------|
| Small NN (10–5 neurons) | 94.31% | Good balance |
| Underfitted NN (2 neurons) | 80.57% | Low complexity → poor performance |
| Large NN (80–40 neurons) | 93.36% | Overfits without regularization |

Regularization and early stopping improved stability.

---

## Final Conclusion

Among all tested models, **KNN achieved the best performance** with:
- **96.31% accuracy**
- High precision, sensitivity, and balanced accuracy  
- Simple implementation and strong results on this dataset  

Given the medical context, KNN is recommended for this dataset due to its strong classification power and low false-negative rate.
