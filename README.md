# Home-Credit-ADS-Audit
Thorough analysis of an automated decision-making system, with heavy consideration for fairness.
## Background
The automated decision system we anmalyzed is predicting Home Credit Default Risk. Loans are a
method of borrowing money, helping people pay for immediate expenses when they don’t
currently have the money to do so. However, loans are typically given to people with good
credit scores, meaning that being well-off financially is often a prerequisite. To obtain a good
credit score, you have to make use of borrowing money often and always repay the money on
time. However, the people who need loans the most are
those who end up struggling the most financially. If you don’t have any spare money to pay for
emergencies now, it will still be very difficult to pay back the borrowed amount in the future. As
such, trusted loan lenders typically require a high credit score in order to offer people loans so
they can be certain that most of the loans will end up repaid. However, there are a multitude of
possible reasons as to why a person may have a low credit score. This ADS is
focused on finding alternative measures to credit score that will help predict the risk of a loan
borrower defaulting, allowing people with low credit scores to find a reputable business to
obtain their loans from. The only alternative people with low credit scores have is to borrow
money from untrustworthy lenders and thus they may end up being taken advantage of. Home Credit
seeks to find a viable alternative to help clients get approved for loans from reputable sources
instead.

## Analysis
We obtain a deep understanding of the input data, analyze the implemented code for data cleaning and pre-processing techniques, and check for fairness on the output results.
<br><br>Data cleaning and preprocessing techniques consist of: 
- Missing-value inputation
- Anomalous values (55,374 impossible values) were changed to NaN
- Label encoding for categorical values and one-hot encoding for numerical values
- Data alignment (inner join)
- Implementation of features combining columns via domain knowledge
  
<br>The implemented models consist of
- Logistic Regression
- Random Forest Classifier
- Light Gradient Boosting Machine (main model)

<br>Analysis techniques consist of
- Gender-based AUROC score comparison (accuracy)
- Variance in performance of model (stability)
- Equalized odds ratio and equalized odds difference (fairness)
- SHAP values of features (explainability)

## Results
The data provided as input for this ADS is appropiate and the model has relatively good performance (AUC of .79). However, we do not believe the ADS to be fair.
While the AUC scores for both
genders are similar, the equalized odds ratio is subpar. The model scored an EO ratio
score of 0.57, which is very far from the ideal of 1.0. There are differing true positive and false
positive rates between the genders, and the SHAP explanation plot illustrates that gender plays
an important role into the decision making of the system, which is harmful to the people whom
the model is used upon. No one wants to be treated differently solely because of their gender. As
such, we would not be comfortable in deploying this ADS into the public sector. A model needs
to be both accurate and fair to be worth deploying and using publicly. 
<br> <br>
Suggestions
- The model does not have any consideration for fairness measures and even uses gender to consider default risk. Changing model implementation methodology to not be influenced by such factors may be appropiate.
- Significant historical data is used for default risk consideration. However, the purpose of this model is to find alternative credit-risk measuring metrics for people with low amounts of history. The model heavily relies upon historical features, thus making it not a viable solution for the original problem. Reducing the use of such features may be appropiate.
  
