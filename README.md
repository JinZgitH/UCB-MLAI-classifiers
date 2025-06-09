# UCB-MLAI-classifiers
In this practical application assignment, the goal is to compare the performance of the classifiers (k-nearest neighbors, logistic regression, decision trees, and support vector machines) 

## Assignment Summary: Bank Marketing Classifier Comparison

### Business Objective

To predict whether a customer will subscribe to a term deposit, enabling the bank to optimize future marketing campaigns, reduce outreach costs, and improve conversion rates.

### Jupiter file
[bank_marketing_classifier_cmp.ipynb](bank_marketing_classifier_cmp.ipynb)

### Dataset Overview

Source: UCI Bank Marketing Dataset

Total samples: ~41,000

Features: 20 (client info, contact data, previous campaign outcomes, economic indicators)

Target: y – whether the client subscribed to a term deposit (yes or no)

Class imbalance: ~88% “no”, ~12% “yes”

### Models Compared

We trained and evaluated the following classifiers with default settings:

| Model                  | Train Accuracy | Test Accuracy | Notes                                        |
| ---------------------- | -------------- | ------------- | -------------------------------------------- |
| Logistic Regression    | \~55%          | \~46%         | Underfitting, needs better features          |
| K-Nearest Neighbors    | \~69%          | \~42%         | Overfitting, sensitive to scaling            |
| Decision Tree          | 100%           | \~47.5%       | Severely overfit without pruning             |
| Support Vector Machine | \~73%          | \~52%         | Best test performance, benefits from scaling |

### Key Findings

1. Baseline Performance
A dummy classifier predicting only the majority class achieves ~88% accuracy.

Thus, accuracy alone is misleading — we focused on precision, recall, and F1.

2. Performance Metrics Adjusted
ROC AUC and F1-score were used to handle class imbalance.

SVM showed the best test performance based on these adjusted metrics.

3. Feature Engineering
We created new features like was_previously_contacted (from pdays).

Categorical variables were encoded; duration was excluded due to data leakage.

4. Hyperparameter Tuning
Grid search improved models:

KNN: best performance at k=7

Decision Tree: pruning (max_depth=5) reduced overfitting

Results showed tuning can meaningfully improve generalization.

### Recommendations
Prioritize recall or F1 in evaluating models due to business need to identify interested customers.

Avoid using features like gender (if present) to ensure ethical and unbiased predictions.

Deploy a tuned SVM or pruned Decision Tree, or consider advanced models (e.g., XGBoost, ensemble methods).

Consider integrating model interpretability tools like SHAP for business transparency.