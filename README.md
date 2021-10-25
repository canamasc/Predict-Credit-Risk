# Supervised Machine Learning - Predicting Credit Risk

## Background

LendingClub is a peer-to-peer lending services company that allows individual investors to partially fund personal loans as well as buy and sell notes backing the loans on a secondary market. LendingClub offers their previous data through an API.

We are comparing Logistic Regression and Random Forest classifiers to try to predict risk level of given loans.

### The data

* `2019loans.csv`
* `2020Q1loans.csv`

We are using an entire year's worth of data (2019) to predict the credit risk of loans from the first quarter of the next year (2020).

Note: these two CSVs have been undersampled to give an even number of high risk and low risk loans. In the original dataset, only 2.2% of loans are categorized as high risk. To get a truly accurate model, special techniques need to be used on imbalanced data. Undersampling is one of those techniques. Oversampling and SMOTE (Synthetic Minority Over-sampling Technique) are other techniques that are also used.

#### Results

Log Model scores:
    Unscaled data: 
        Training Data Score: 0.6575533661740558
        Testing Data Score: 0.5204168438962143
    Scaled data:
        Training Score: 0.7130541871921182
        Testing Score: 0.7216078264568269

Random Forest scores:
    Unscaled data: 
        Training Score: 0.9999178981937603
        Testing Score: 0.6646108039132285
    Scaled data:
        Training Score: 0.9999178981937603
        Testing Score: 0.6650361548277329
        
Scaling the data had a very good effect on the outcome of the Log model. The scores for both the training and test sets increased, and the scores got closer together (0.13 difference reduced to 0.01), meaning the Log model is now likely to generalize well too.
Scaling the data did not really have much effect on the Random Forest classifier. It still appears to be the case that the model is overfitting on the training data and thus performing poorly on the test data set. 
Overall, I believe the Log Model (with scaled data) is the better choice in this situation, since it seems to be less sensitive to noise in the data or any collinearity between features. I think we would see a drastic improvement in the Random Forest model if we implemented feature selection techniques, but that might be overkill for this use case.

