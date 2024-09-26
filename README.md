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

* In an attempt to improve accuracy, a **Sequential model** with **LeakyReLU-activated 3 hidden layers** was compiled for binary classification. The model's accuracy was initially 72% but dropped after several runs. To explore potential improvements, the **learning rate** was adjusted from its default value of 0.001 to 0.01 and higher during model compilation, and the **batch size** was changed from the default of 32 during training. Despite multiple runs with these adjustments, no improvement in accuracy was observed, so the settings were reverted to their defaults.

* **Random Forest** was used as anternative option, and although initially the model seemed underperforming, the last run showed an accuracy of 72%, similar to the Sequential models. As mentioned above, to make this model perform, some features were dropped to improve accuracy. This model was used as it is well fitted for unbalanced data.

* A **Functional API model** with 3 **ReLU**-activated hidden layers, **dropout** for regularization, and a **sigmoid output layer** was also tried, but it showed lower accuracy than the initial Sequential model.
<p> *Note: Accuracy fluctuations across models on each new run were likely due to random initialization, stochastic training, and overfitting. Setting a random seed and using cross-validation will help improve consistency and reduce overfitting.*

___

## Summary
The **Sequential model** with 2 hidden layers using **ReLU activation** and binary classification achieved the highest accuracy of 72.11%. While this is decent, further improvements might be made by categorizing the highly skewed 'ASK_AMT' feature to prevent overfitting. Additionally, using metrics like **Precision, Recall, F1-Score**, and the **Confusion Matrix** could help identify and address biases in model predictions. Although model accuracy might be limited due to inherent data properties or external factors like the broader economy, exploring feature engineering and further tuning could yield better results.
___

### Ethical Considerations
* To ensure fair predictions, sensitive data like company names and EINs should be removed. 
* Maintain transparency in model decision-making, and regularly verify data accuracy to prevent harm to organizations. 
* Address potential biases in the model to ensure equitable outcomes for all applicants.

___

### Resources
IRS: [Tax Exempt Organization Search Bulk Data Downloads](https://www.irs.gov/charities-non-profits/tax-exempt-organization-search-bulk-data-downloads).