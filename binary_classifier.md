Requirements 

Pandas : 1.1.5

Seaborn : 0.11.1

 numpy : 1.18.5

 Matplotlib : 3.2.2

 Scikit-learn : 0.22.2.post1

DESCRIPTION 

1)As the features are quantitative in nature, numerical summaries in the form of descriptive statistics and scatter plots are the preferred methods to get a crisp understanding of the data distribution 

2)The dataset is checked to ensure that no null values are present 

3)The class frequqncy for each of the two classes is checked (cell-9) and since the classes are not heavily imbalanced(1.5:1), we proceed with further analysis and pre-processing. The imbalance is later accomodated by way of penalising in the classification models used 

4)As the range of all the variables is varying widely (in terms of maximum value seen in cell-7), it is necessary to standardise the data set ehcih is done subsequently (function in cell-18).

 5)Scatter plots for the predictors or features are made and it is seen that most features between x1-x24 are moderately correlated with the points noisily distributed around the ideal line of a perfect correlation(slope 45deg). Some features between x25-x48 have a less spread correlation . 

6)However, it is advised to standardise the data only with respect to the training data to ensure that no biasness is introduced into the model due to leakage of information from the validation or test data. 

7)So, the data is first split into training and validation data in the ratio 4:1 as asked. (cell-21)

 8)Thereafter, a scaler object is fitted on the training data and the training data is standardised(data points transformed to a standard normal distribution). 

9)Since, the features of the training data are signifiantly correlated, dimensional reduction(using Principal Component Analysis-PCA) after the standardisation is done to maintain a 95% variance in the data and remove highly correlated features. Here, a PCA object is created and fitted on the standardised training data. This fitted PCA object is used to transform the features into unrelated components(function in cell-19) 

10)The validation data is standardised using the scaler obkect fitted on training data. 

11)Six different classifier models, namely Logistic Regression, K-Nearest Neighbours, Decision Trees, Support Vector Machines, Random Forest and Gradient Boosting are defined and trained on the training data.(cell-21) 

12)The metrics are plotted as blox-plots to get a visual estimate of the quality of the classifiers. Since the SVM, Random Forest and Gradient Boosting are almost at par, these models are taken for further comparison and validation. 

13)Confusion matrix or pivot tables for each of the models is computed along with the precision, recall, accuracy and f1-scores and it is observed that the Gradient Boosting method is the more reliable classifier among the three. This inference is drawn from the observation that the f1-score, which is a consolidated metric for both precision and recall, is the highest for a Gradient Boosting classifier. 

14)The Area Under Receiver-Operating Characteristic Curve (ROC-AUC) is also plotted and it is seen that the AUC has a reasonably high value of 0.92 on the validation set. Since, this validation set is cautiously kept out-of-sample of the training set, there is little room for biasness to have been introduced. However, there is some variance in the model which can be inferred from the ROC_AUC metric of 1 on the training set but value of 0.92 on the validation set. (cell-27) 

15)The model is next used to perform predictions on the test set (cell-31). The test data is standardised with a scaler fitted on training data (cell-30) and also dimensionally reduced with a PCA-object fitted on standardised training data(cell-30).

 16)The predictions on the test set are saved to a file in cell-32.

