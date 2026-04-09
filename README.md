#### CRISP-DM Framework



#### BUSINESS UNDERSTANDING

The goal of this project is to predict whether a client will subscribe to a term deposit.


From a marketing perspective, improving targeting is critical. 

* Contacting unlikely customers wastes resources

* Missing likely customers reduces conversions


The business question becomes:

Which clients are most likely to subscribe, and how can that information improve campaign effectiveness?


Reframed as a data problem: 

* Use classification models to predict subscription outcomes

* Evaluate how model choice impacts performance

* Identify which features provide meaningful predictive signal

* Provide insights to guide marketing strategy


The objective is not just prediction, but understanding what drives successful outcomes. 



#### DATA UNDERSTANDING

The dataset contains client information, campaign details, and prior marketing outcomes. 


Initial exploration focused on:

* Distribution of the target variable

* Behavior of key categorical features

* Relationship between prior outcomes and subscription

* Identification of potential leakage variables


Key findings:

* The dataset is imbalanced, with more non-subscriptions than subscriptions

* The previous campaign outcome is strongly predictive, especially prior success

* The `duration` feature is highly predictive but not usable in practice


These observations informed preprocessing and modeling decisions.



#### DATA PREPARATION

The dataset was prepared prior to modeling.


Key steps included:

* Removing the `duration` feature due to data leakage

* Encoding categorical variables using one-hot encoding

* Standardizing numeric features

* Splitting the data into training and test sets using stratified sampling


The preprocessing pipeline was applied consistently across all models.



#### MODELING

Four classification models were evaluated:

* Logistic Regression

* Decision Tree

* K-Nearest Neighbors (KNN)

* Support Vector Machines (SVM)


Each model was trained using a shared preprocessing pipeline.


Hyperparameter tuning was performed to evaluate model sensitivity:

* Logistic Regression: regularization strength (C) and polynomial features

* Decision Tree: max_depth and min_samples_leaf

* KNN: n_neighbors

* SVM: C and gamma



#### EVALUATION

Models were compared using:

* Train and Test Accuracy

* Cross-validation accuracy and variability

* Precision-recall analysis


Key observations:

* Improvements over baseline models are modest

* Model choice has limited impact given the available features

* Logistic Regression and Decision Trees provide strong performance with lower computational cost

* SVM achieves similar accuracy but requires more computation


Precision-recall analysis shows:

* Similar trade-offs across models

* Threshold selection significantly impacts performance

* SVM exhibits slightly different behavior due to probability estimation



#### DEPLOYMENT

The results suggest that simpler models are sufficient for this problem.


Logistic Regression provides:

* Stable performance

* Interpretability

* Low computational cost


The final model uses:

* C = 0.1

* No polynomial feature expansion



#### Important Limitation

The `duration` feature is highly predictive but cannot be used in a real-world setting.

It is only known after the call is completed and therefore introduces data leakage.



#### FINAL SUMMARY

Subscription prediction is possible, but gains from increasing model complexity are limited.

* Feature quality is more important than model choice

* Previous campaign success provides strong predictive signal

* More complex models do not significantly outperform simpler ones


Logistic Regression offers the best balance of performance, simplicity, and interpretability.


This project demonstrates that effective feature selection and evaluation are more impactful than increasing model complexity. 




