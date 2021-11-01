# DonorChooseOrg
**Teachers ask, You choose, Student learn.**

DonorsChoose.org is a US-based nonprofit foundation that allows individuals to donate directly to public school classroom projects, organizing teacher’s project proposals in a way that likely donors can find and fund projects that best satisfy their preferences. It promotes and facilitates the crowdfunding of classroom projects from schools around the country. Their mission statement according to their website “engages the public in public schools by giving people a simple, accountable and personal way to address educational inequity.

**Data Description** :

The data made publicly available on the DonorsChoose.org website. This  dataset comes in the form of downloadable CSV files. DonorsChoose.org has shared data of all the past projects, the related resources, teachers, schools, donors, and donations. This analysis is limited to the projects posted after Jan 1, 2013. The dataset contains (3.9M) donations by (1.5M) donors to (638k) projects over a total amount of (282M). A project is said to have a class value of 0 if it is not funded within four months from the project post-date. Otherwise, it is said to have a class value of 1 and is considered as a fully funded project.The main contributing tables to our analysis are Projects and
Schools. More information about the features description is detailed in Table (1).
![image](https://user-images.githubusercontent.com/93243958/139680511-2d37f44f-6e8b-4a60-a437-350b2a4dcf18.png)


**Data Preprocessing** :

The cleaning process required eliminating data with missing values since the percentage of missing data is very small compared to the full number of data (1.56%), identifying
outliers, as well as excluding features like IDs, Project Funded and Expired Dates as they are found to be less relevant to this analysis. The dataset showed considerable imbalance as the percentage of fully funded projects is much higher than those that had been expired (75%:25%). This issue had been addressed by applying the SMOTE function which is detailed in building the predictive models section. The main file to be used in solving our classification problem is the Projects.csv file. we started to look at the features and exclude non-contributed features (e.g. Teacher ID, School ID). Then, we explored the categorical columns that have high number of unique values and try to reduce them without losing information. For instance, Project Subject Category Tree column include instances with single categories and other instances with two categories combined as one. In order to have only one category in each row, we did the contingency table for every single category (main categories) with the Project Current Status class so we had frequency of each category for being Fully Funded or Expired. After that, we calculated the probability of each of them as shown in Table (2).
![image](https://user-images.githubusercontent.com/93243958/139572080-11663794-eaef-4a62-a94f-f799368486e8.png)

  

**EDA:**


**Question 1: What kind of project resources category that takes a project to be fully funded
or expired?**

![image](https://user-images.githubusercontent.com/93243958/139573005-9fc6e349-2b1f-4e67-a32f-ba8f63a2e0c9.png)

Findings:
•	The highest success ratio was for "Food, Clothing & Hygiene”, followed by "Sports & Exercise Equipment".
•	The lowest success ratio was for "Technology”, followed by "Visitors" and "Trips".

**Question 2: what is the seasonality pattern for donations?**

![image](https://user-images.githubusercontent.com/93243958/139236561-3c11582e-233b-41c0-83ea-02ea05f1aa50.png)

Findings:
Total donation is the lowest in June, where summer vacation is approaching; and highest in December (as Christmas gift?) and August (when schools are about to open).

**Question3: Does the number of projects varied in a consistent way across the school year in order reach their funding goal?**

![image](https://user-images.githubusercontent.com/93243958/139236794-3265282f-a1d0-48b0-b116-a60caac1f651.png)

Findings:

-From the figure above it appears that there tends to be a surge in the number of projects that get funded at the start of the school year, this number then decrease significantly around the summer time. The overall pattern has steady increase year to year. A few spikes in the number of projects funded. These spikes are due to large donation match partnerships from Ripple and Bill and Melinda Gates.

-The figure below shows that indeed more projects are posted at the beginning of the school year which in turn leads to an increase in the number of live projects. This is also shown by the fact that the rate of funding projects and the rate of posting projects show a small but significant correlation ( r-squared= 0.22, p<0.001).

Q4:

![image](https://user-images.githubusercontent.com/93243958/139237198-60c76969-8a64-472f-be6d-29027f90a942.png)

 
if the increase in project funding is entirely counterbalanced by an increase in the number of projects posted then the fraction of projects that are funded at the start of the year should not be significantly different from the fraction that are ultimately funded at any other point in the school year. To test this we sorted projects into those that were ultimately fully funded and those that expired before reaching their funding goal. The figure below shows that at the beginning of the school year, the number of projects posted that expired increased at what seems like a similar rate as those that were eventually funded.


**Features Engineering and Selection:**

1. Project  Posted  Month  derived  from  Project  Posted Date.

2. Eliminating  the  dependent  Features by Chi2-test 

3. A new data frame with text features

4. Appling Chi2-test for  selected  features  and  made  sure  that  they  are significantly important for the classification of Project Status.


**Dimensionality Reduction:**

Project Subject Category values reduced to single categories instead of two categories in some observations

![image](https://user-images.githubusercontent.com/93243958/139011250-348036c4-34c5-4fca-a355-d96205fd5dcb.png)


**Final Feature Set:**

![image](https://user-images.githubusercontent.com/93243958/139011353-cff617d9-40d2-4762-a63b-0c82d495e226.png)

**Building the Predictive Models:**

1. Splitting  the  data   into training  and  test  sets

2. 5-fold  Cross  Validation

3. Hyper-parameter optimization using Random Search

4. Applying the SMOTE function to solve the imbalanced class problem in train set only.

**Classifiers Performance using Train-Test split:**

![image](https://user-images.githubusercontent.com/93243958/139572983-ae380da7-fb00-4634-8759-308e62d82c5e.png)

**ROC Curve  for Classifiers Performance using Train-Test split:**

![image](https://user-images.githubusercontent.com/93243958/139011599-950a8341-020d-4d68-aab1-03a3d2c34da0.png)

**Classifiers Performance using 5-fold Cross Validation:**

![image](https://user-images.githubusercontent.com/93243958/139011689-ff1e2f42-49a0-47f6-a0cb-fe2572a79692.png)


**ROC Curve  for Classifiers Performance using 5-fold Cross Validation:**

![image](https://user-images.githubusercontent.com/93243958/139011848-1902fdd2-b1af-41dd-9cf8-e765b41ac341.png)


**Conclusion:**

In train-test split, Random Forest performs better than the other classifiers with an F1-score of 0.84 
Logistic Regression is the best model with an AUC value of 0.64. 


In 5-fold Cross Validation, XGBoost classifier performance has significantly improved with F1-score of 0.86. 
Logistic Regression outperforms all other models with a stable AUC value  of 0.64. 





