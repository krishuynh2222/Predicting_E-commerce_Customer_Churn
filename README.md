# Predicting E-Commerce Customer Churn with Machine Learning

**Dataset Name:** Ecommerce Customer Churn Analysis and Prediction  

**Source:** Kaggle – Created by Ankit Verma

**Dataset Link:** https://www.kaggle.com/datasets/ankitverma2010/ecommerce-customer-churn-analysis-and-prediction?select=E+Commerce+Dataset.xlsx

## Introduction 
The e-commerce sector has grown exponentially, leading to intense competition. In this
environment, acquiring a new customer is significantly more expensive than retaining an
existing one. The phenomenon where customers cease to do business with a company
is a major source of revenue loss. The ability to forecast customer attrition allows a
business to shift from a reactive to a proactive retention model, engaging at-risk
customers with targeted offers or improved support before they are lost.

## Methodology 
#### **1. Data models**
The dataset consisted of 5630 records and 20 attributes related to customer churn. The
target variable is Churn, a binary flag indicating whether a customer churned (1) and a
customer retained (0).

#### **2. Statistical Summary**
Exploratory Data Analysis was performed to understand data distributions and
inter-variable relationships.
The describe().T function provided a statistical summary, revealing a significant
imbalance in the target variable, with only 16.8% of customers in the 'Churn' class. This
imbalance necessitates special handling during modeling.
<img width="853" height="475" alt="Screenshot 2025-11-18 at 7 44 27 PM" src="https://github.com/user-attachments/assets/aa4e21ce-96bc-4092-8e04-e511dbebd85e" />

#### Model Selection 
The two supervised models proved effective in customer churn. 
#### Principal Component** Analysis (PCA)
The Principal Component Analysis (PCA) model was performed on the scaled training data to analyze the dataset's dimensionality
and potential for visualization.

<img width="534" height="393" alt="image" src="https://github.com/user-attachments/assets/bb528748-f8ac-4f17-8cfc-44bbe5194d86" />

A 2D projection of the data onto its first two principal components shows a
heavy overlap between churned and retained customers. This confirms that the
separation boundary is complex and non-linear, justifying the choice of a robust,
non-linear model.

#### Random Forest
Given the non-linear nature of the data and the class imbalance, a Random Forest
classifier was selected. This model is an ensemble of decision trees, which is robust to
overfitting and can handle complex interactions.

| Metric   | Class 0 (Churn)  | Class 1 (Retain)  | Average 
|--------  |------------------|-------------------|-------------|
| Precision| 0.98             | 0.99              |             | 
| Recall   | 1.00             | 0.91              |             |
| F1-Score | 0.99             | 0.95              |             |
| Accuracy | -                | -                 | 0.98        | 


<img width="507" height="455" alt="image" src="https://github.com/user-attachments/assets/2faed7cc-4c3e-4ab8-9684-0888e040a9d2" />

The confusion matrix provides a clear view of the model's performance. Out
of 190 actual churners in the test set, the model correctly identified 172 (True Positives)
and missed 18 (False Negatives). This low False Negative rate is crucial for a churn
model, as it minimizes the number of at-risk customers who are missed.

## Result and Discussion
<img width="536" height="393" alt="image" src="https://github.com/user-attachments/assets/e5ce212d-7da7-4c5c-ba23-81b4201ec2bb" />

EDA revealed that Tenure, Complain, and SatisfactionScore are primary churn
drivers; several behavioral segments (e.g., Mobile Phone order category, COD
payment mode, Computer login device, Single marital status) exhibit elevated risk. The
PCA analysis confirmed limited linear separability; the Random Forest capitalized on
non-linear patterns to achieve excellent discrimination (ROC-AUC ≈ 0.999).
Business-wise, the high recall on churners means fewer at-risk customers slip
through. With calibrated probabilities, stakeholders can set action thresholds to trigger
offers, service outreach, or UX fixes.

## Conclusion and Future Work
This study successfully developed a high-performance Random Forest model capable
of predicting customer churn in an e-commerce environment with 98% accuracy and an
ROC-AUC of 0.9987. Key drivers identified through EDA, such as Tenure, Complain, and SatisfactionScore, were shown to be critical factors.
The model's high recall for the churn class (92%) makes it an effective tool for business.
By deploying this model, the company can move from a reactive to a proactive
customer retention strategy.

**Future work could involve:**
**1. Model Deployment:** Integrating the model into a live dashboard to provide
real-time risk scores.

**2. Feature Engineering:** Creating more complex features, such as "monetary value"
or "purchase frequency" ratios.

**3. Alternative Models:** Testing other advanced ensemble methods, such as
XGBoost or LightGBM, to potentially achieve further marginal gains in
performance.

