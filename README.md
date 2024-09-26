# deep-learning-challenge



## Project Overview
* **Alphabet Soup** is a nonprofit foundation that funds ventures focused on social good, including healthcare, product development, and preservation. The goal is to support the most promising initiatives using data-driven approaches to evaluate applicants.
* **This project aims to create a binary classifier to predict which applicants are most likely to succeed, aiding the foundation in its decision-making process.**
___

## Process and Results

### Target and Independent Variables

* **Target:** 'IS_SUCCESSFUL', indicating if the applicant was successful.
* **Features:** The rest of the columns, including 'ASK_AMT', 'INCOME_AMT', 'ORGANIZATION', 'USE_CASE', 'CLASSIFICATION', 'AFFILIATION', 'APPLICATION_TYPE', 'SPECIAL_CONSIDERATIONS', and 'STATUS'
* 'NAME' and 'EIN' were removed to prevent overfitting and because they are not relevant to the predictions.
* Feature selection using Random Forest helped reduce noise by identifying the most important features correlated with the outcome. The following features were dropped: 'APPLICATION_TYPE_Other', 'APPLICATION_TYPE_T19', 'INCOME_AMT_50M+', and 'SPECIAL_CONSIDERATIONS_Y'

### Data Preparation
* Missing values were checked and addressed.
* Rare values in some categorical features were grouped together to reduce noise.
* **Standard Scaling** was applied to handle the varying scales of numerical data like 'ASK_AMT'.

### Machine Learning Models

* A **Sequential model** with **ReLU-activated 2 hidden layers**, compiled for binary classification, achieving an accuracy of 72%.

* In an attempt to improve accuracy, a **Sequential model** with **LeakyReLU-activated 3 hidden layers** was compiled for binary classification. To explore potential improvements, the **learning rate** was adjusted from its default value of 0.001 to 0.01 and higher during model compilation, and the **batch size** was changed from the default of 32 to 16 during training. Despite multiple runs with these adjustments, the accuracy dropped significantly lower than the previous model's 72% accuracy. The final configuration, using 32 batches and a learning rate of 0.001, still resulted in the 46% accuracy, a notable drop from the initial model's performance.

* **Random Forest** was used as an alternative option for unbalanced data. Initially, after excluding a few features like 'APPLICATION_TYPE_Other', 'APPLICATION_TYPE_T19', 'INCOME_AMT_50M+', and 'SPECIAL_CONSIDERATIONS_Y', it achieved 70% accuracy, similar to the Sequential models. After identifying the 3 most influential features, additional less relevant features were dropped. However, after this refinement, the accuracy dropped to 66%.

* A **Functional API model** with 3 **ReLU**-activated hidden layers, **dropout** for regularization, and a **sigmoid output layer** was also tried, but it showed similar accuracy of 72% as the initial Sequential model.
<p> *Note: Accuracy fluctuations across models on each new run were likely due to random initialization, stochastic training, and overfitting. Setting a random seed and using cross-validation will help improve consistency and reduce overfitting.*

___

## Summary
The **Sequential model** with 2 hidden layers using **ReLU activation** and binary classification achieved the highest accuracy of 72%. While this is decent, further improvements might imptove that. However, it's imprtant to acknoledge that model accuracy can be limited by inherent data properties (e.g., data quality, imbalance, or feature relevance) as well as external factors like project strategy, the specific nature of the problem (e.g., public health), or broader economic and environmental conditions. **Using additional metrics like Precision, Recall, and F1-Score** can help identify potential biases in model predictions, especially in imbalanced datasets where accuracy alone may be misleading. Further improvements might be achievable through more advanced feature engineering, better data collection, hyperparameter tuning, and the use of these metrics to better evaluate model performance and fairness.

### Ethical Considerations
* To ensure fair predictions, sensitive data like company names and EINs should be removed. 
* Maintain transparency in model decision-making, and regularly verify data accuracy to prevent harm to organizations. 
* Address potential biases in the model to ensure equitable outcomes for all applicants.

___

### Resources
IRS: [Tax Exempt Organization Search Bulk Data Downloads](https://www.irs.gov/charities-non-profits/tax-exempt-organization-search-bulk-data-downloads).