# DonorChooseOrg
**Teachers ask, You choose, Student learn.**

DonorsChoose.org is a US-based nonprofit foundation that allows individuals to donate directly to public school classroom projects, organizing teacher’s project proposals in a way that likely donors can find and fund projects that best satisfy their preferences. It promotes and facilitates the crowdfunding of classroom projects from schools around the country. Their mission statement according to their website “engages the public in public schools by giving people a simple, accountable and personal way to address educational inequity.

**Data Description** :

The data made publicly available on the DonorsChoose.org website. DonorsChoose.org has shared data of all the past projects, the related resources, teachers, schools, donors, and donations. This analysis is limited to the projects posted after Jan 1, 2013. The dataset contains (3.9M) donations by (1.5M) donors to (638k) projects and (72k) schools. A project is said to have a class value of 0 if it is not funded within four months from the project post-date. Otherwise, it is said to have a class value of 1 and is considered as a fully funded project. 


**Data Preprocessing** :

The cleaning process required eliminating data with missing values since the percentage of missing data is very small compared to the full number of data and excluding features like IDs, Project Funded and Expired Dates as they are found to be less relevant to this analysis. The dataset showed considerable imbalance as the percentage of fully funded projects is much higher than those that had been expired (75%:25%). This issue had been addressed by applying the SMOTE function. The main file to be used in solving our classification problem is the Projects.csv file. I started to look at the features and exclude non-contributed features (e.g. Teacher ID, School ID). Then, I explored the categorical columns that have high number of unique values and try to reduce them without losing information. For instance, Project Subject Category Tree column include instances with single categories and other instances with two categories combined as one. In order to have only one category in each row, I did the contingency table for every single category (main categories) with the Project Current Status class so I had frequency of each category for being Fully Funded or Expired. After that, I calculated the probability of each of them as shown in Table (1) . For instance, if I  have AppliedLearning, Math and Science as categories of one project and that project was Fully Funded I replace them with AppliedLearning only as it has the higher probability than Math and Science of being Fully Funded. I then merged the projects features file (Projects.csv)with the schools features file (Schools.csv), and drop Live projects rows from the target feature (Project Current Status) as I concerned in Expired and Fully Funded projects only. Then I convert the categorical features into dummies to prepare them for the modeling process. 


**Table 1 : Dimensionality Reduction:**

![image](https://user-images.githubusercontent.com/93243958/139011250-348036c4-34c5-4fca-a355-d96205fd5dcb.png)
  

**EDA:**


**Question 1: What kind of project resources category that takes a project to be fully funded
or expired?**

![image](https://user-images.githubusercontent.com/93243958/139573005-9fc6e349-2b1f-4e67-a32f-ba8f63a2e0c9.png)

**Findings:**

•	The most well funded percentage of project resources was for "Food, Clothing & Hygiene”, followed by "Sports & Exercise Equipment".

•	The least  funded percentage of project resources was for "Technology”, followed by "Visitors" and "Trips".

**Question 2: what is the seasonality pattern for donations?**

![image](https://user-images.githubusercontent.com/93243958/139925696-169a02fc-0bc0-4d45-87a8-b172ec99b757.png)

**Findings:**

• Total donation is the lowest in June, where summer vacation is approaching; and highest in December as Christmas gift and August when schools are about to open.

**Question3: Does the number of projects varied in a consistent way across the school year in order reach their funding goal?**

![image](https://user-images.githubusercontent.com/93243958/139236794-3265282f-a1d0-48b0-b116-a60caac1f651.png)

**Findings:**

• From the figure above it appears that there tends to be a surge in the number of projects that get funded at the start of the school year, this number then decrease significantly around the summer time. The overall pattern has steady increase year to year. A few spikes in the number of projects funded. These spikes are due to large donation match partnerships from Ripple and Bill and Melinda Gates.

• The figure shows that indeed more projects are posted at the beginning of the school year which in turn leads to an increase in the number of live projects. This is also shown by the fact that the rate of funding projects and the rate of posting projects show a small but significant correlation .


**Features Engineering and Selection:**

1. Project  Posted  Month  derived  from  Project  Posted Date.

2. Eliminating  the  dependent  Features by Chi2-test 

3. Appling Chi2-test for  selected  features  and  made  sure  that  they  are significantly important for the classification of Project Status.



**Building the Predictive Models:**

1. Splitting  the  data   into training  and  test  sets
2. Applying the SMOTE function to solve the imbalanced class problem in train set only.

**Classifiers Performance using Train-Test split:**

![image](https://user-images.githubusercontent.com/93243958/139572983-ae380da7-fb00-4634-8759-308e62d82c5e.png)

**ROC Curve  for Classifiers Performance using Train-Test split:**

![image](https://user-images.githubusercontent.com/93243958/139693298-df05b591-ec30-479c-a81a-5c4fc0787fcd.png)



**Conclusion:**

One of the most important motivations of this analysis was to help teachers by exploring the features that made a project succeed in getting funded before the end of the campaign period. Based on the scope of this analysis, Project Posted Month, Project Cost, Project Resource Category and Project Subject Category Tree were the most significant features among others.

• In train-test split, Random Forest performs better than the other classifiers with an F1-score of 0.84 Logistic Regression is the best model with an AUC value of 0.64. 

• Project Posted Month was derived from Project Posted Date and explored. we found that projects posted in the start of the school year have a high probability of being Funded than projects posted during Summer time or the end of the school year.



**The blog link:** https://medium.com/@samaher.fwz/6u-2a350a8077d

