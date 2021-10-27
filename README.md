# DonorChooseOrg
Teachers ask, You choose, Student learn.


Features Engineering and Selection:

Project  Posted  Month  derived  from  Project  Posted Date.

Eliminating  the  dependent  Features by Chi2-test 

A new data frame with text features

Appling Chi2-test for  selected  features  and  made  sure  that  they  are significantly important for the classification of Project Status.


Dimensionality Reduction:

Project Subject Category values reduced to single categories instead of two categories in some observations

![image](https://user-images.githubusercontent.com/93243958/139011250-348036c4-34c5-4fca-a355-d96205fd5dcb.png)


Final Feature Set:

![image](https://user-images.githubusercontent.com/93243958/139011353-cff617d9-40d2-4762-a63b-0c82d495e226.png)

Building the Predictive Models:
Splitting  the  data   into training  and  test  sets
5-fold  Cross  Validation
Hyper-parameter optimization using Random Search
Applying the SMOTE function in train set only.

Classifiers Performance using Train-Test split:
![image](https://user-images.githubusercontent.com/93243958/139011514-4a62ee6c-a935-4cc4-8158-13002f3b3d10.png)

ROC Curve  for Classifiers Performance using Train-Test split:

![image](https://user-images.githubusercontent.com/93243958/139011599-950a8341-020d-4d68-aab1-03a3d2c34da0.png)

Classifiers Performance using 5-fold Cross Validation:

![image](https://user-images.githubusercontent.com/93243958/139011689-ff1e2f42-49a0-47f6-a0cb-fe2572a79692.png)

ROC Curve  for Classifiers Performance using 5-fold Cross Validation:

![image](https://user-images.githubusercontent.com/93243958/139011848-1902fdd2-b1af-41dd-9cf8-e765b41ac341.png)


Conclusion:

In train-test split, Random Forest performs better than the other classifiers with an F1-score of 0.84 
Logistic Regression is the best model with an AUC value of 0.64. 


In 5-fold Cross Validation, XGBoost classifier performance has significantly improved with F1-score of 0.86. 
Logistic Regression outperforms all other models with a stable AUC value  of 0.64. 





