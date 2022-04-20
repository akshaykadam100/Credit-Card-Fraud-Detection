### Problem Statement

The problem statement is to predict fraudulent credit card transactions with the help of machine learning models.

In this project, we will analyse customer-level data that has been collected and analysed during a research collaboration of Worldline and the Machine Learning Group. 

### Business problem overview

For many banks, retaining high profitable customers is the number one business goal. Banking fraud, however, poses a significant threat to this goal for different banks. In terms of substantial financial losses, trust and credibility, this is a concerning issue to both banks and customers alike.

It has been estimated by Nilson Report that by 2020, banking frauds would account for $30 billion worldwide. With the rise in digital payment channels, the number of fraudulent transactions is also increasing in new and different ways. 

In the banking industry, credit card fraud detection using machine learning is not only a trend but a necessity for them to put proactive monitoring and fraud prevention mechanisms in place. Machine learning is helping these institutions to reduce time-consuming manual reviews, costly chargebacks and fees as well as denials of legitimate transactions.

### Understanding and defining fraud

Credit card fraud is any dishonest act or behaviour to obtain information without proper authorisation from the account holder for financial gain. Among different ways of committing frauds, skimming is the most common one, which is a way of duplicating information that is located on the magnetic strip of the card. Apart from this, following are the other ways:

-   Manipulation/alteration of genuine cards
-   Creation of counterfeit cards
-   Stealing/loss of credit cards
-   Fraudulent telemarketing

### Data dictionary

The data set is taken from the [Kaggle](https://www.kaggle.com/mlg-ulb/creditcardfraud) website and has a total of 2,84,807 transactions; out of these, 492 are fraudulent. Since the data set is highly imbalanced, it needs to be handled before model building.

The data set includes credit card transactions made by European cardholders over a period of two days in September 2013. Out of a total of 2,84,807 transactions, 492 were fraudulent. This data set is highly unbalanced, with the positive class (frauds) accounting for 0.172% of the total transactions. The data set has also been modified with principal component analysis (PCA) to maintain confidentiality. Apart from ‘time’ and ‘amount’, all the other features (V1, V2, V3, up to V28) are the principal components obtained using PCA. The feature 'time' contains the seconds elapsed between the first transaction in the data set and the subsequent transactions. The feature 'amount' is the transaction amount. The feature 'class' represents class labelling, and it takes the value of 1 in cases of fraud and 0 in others.

### Project Pipeline

The project pipeline can be briefly summarised in the following four steps:

-   **Data Understanding**: Here, you need to load the data and understand the features present in it. This would help you choose the features that you will need for your final model.
-   **Exploratory Data Analytics (EDA)**: Normally, in this step, you need to perform univariate and bivariate analyses of the data, followed by feature transformations, if necessary. For the current data set, because Gaussian variables are used, you do not need to perform Z-scaling. However, you can check whether there is any skewness in the data and try to mitigate it, as it might cause problems during the model building phase.
-   **Train/Test Split**: Now, you are familiar with the train/test split that you can perform to check the performance of your models with unseen data. Here, for validation, you can use the k-fold cross-validation method. You need to choose an appropriate k value so that the minority class is correctly represented in the test folds.
-   **Model Building / Hyperparameter Tuning**: This is the final step at which you can try different models and fine-tune their hyperparameters until you get the desired level of performance on the given data set. You should try and check if you get a better model by various sampling techniques.
-   **Model Evaluation**: Evaluate the models using appropriate evaluation metrics. Note that since the data is imbalanced, it is more important to identify the fraudulent transactions accurately than the non-fraudulent ones. Choose an appropriate evaluation metric that reflects this business goal.

### Conclusion

Above dataset was validated on various models using oversampling techniques and below are the details:

| Recall Table | Decision Tree    | ANN | Logistics | Gradient Boost | XG Boost | Random Forest 
|-------------------------|----------|-----------|----------------- | --------- | ---------- | ------------ |
| `Imbalanced`        | 84.21 | 99.9  |       93.68 | 78.95 | 81.05 | 61.05 |
| `Random Oversample` | 86.32 | 97.34 |       94.74 | 86.32 | 86.32 | 89.47 |
| `SMOTE`             | 88.42 | 98.11 |       91.58 | 90.53 | 88.42 | 90.53 |
| `ADASYNC`           | 92.63 | 95.99 |       93.68 | 89.47 | 86.32 | 90.53 |

| Precision Table | Decision Tree    | ANN | Logistics | Gradient Boost | XG Boost | Random Forest 
|-------------------------|----------|-----------|----------------- | --------- | ---------- | ------------ |
| `Imbalanced`        | 48.78 | 99.9  |        2.72 | 78.12 | 93.9  | 82.86 |
| `Random Oversample` | 36.44 | 97.34 |        2.9  | 53.95 | 89.13 | 55.92 |
| `SMOTE`             | 11.59 | 98.11 |        3.99 | 27.48 | 75.68 | 34.96 |
| `ADASYNC`           |  5.4  | 95.99 |        2.49 | 12.48 | 75.93 |  7.96 |


1. **Logistic Regression** (logistics) ==> Even though providing a good Recall value, Precision is low which indicates that even though fraud are detected properly, but customer experience will be very bad as many transactions will be blocked.
2. **Artificial Neural Network** (ann) ==> Neural Network show a consistent performance in Precision & Recall Values across all the sampling methods with the best performance observed in unsampled data.
3. **Decision Tree** (dt) ==> Decision Trees even though having a significant Recall value, Precision is a bit of concern here. So this can be kept as backup.
4. **Gradient Boosting** (gb) ==> Gradient Boosting even though having a significant Recall value, Precision is a bit of concern here. So this can be kept as backup.
5. **XG-Boost** (xgb) ==> XG Boost seems to outperform all the models (except ANN) in terms of Precision. Although Recall value is a bit of concern here, but still there is a good trade-off between Precision & Recall.
6. **Random Forest** (rf) ==> Random Forest even though having a significant Recall value, Precision is a bit of concern here. So this can be kept as backup.