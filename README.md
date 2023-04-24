# Credit Risk Analysis
## Project Overview
The purpose of this project is to design and implement several machine learning models in order to predict credit risk.  Fast Lending management believes using machine models to predict credit risk will make the loan process quicker and more reliable, and lead to more reliable identification of good candidates for loans which will lead to lower default rates. 

### Resources
+ Source: LoanStats_2019Q1
+ Software: Python 3.7.15, Jupyter Notebook 6.5.2

## Results
### Oversampling

#### RandomOverSampler model

![image](https://user-images.githubusercontent.com/113741694/234063383-4030e69f-9803-4ec1-8d14-89ee395bd6d9.png)

![image](https://user-images.githubusercontent.com/113741694/234063537-44361f7b-3b07-49de-a318-1213ce5d62a2.png)

![image](https://user-images.githubusercontent.com/113741694/234063692-67e145f4-432a-4dbf-98b5-ec81080e9fdf.png)

+ The balanced accuracy score was 64%
+ The precision for high-risk applicants was very low at 1%, meaning only 1% of applicants designated as high-risk will actually be high-risk; the recall for high-risk applicants was 62%, meaning 62% of high-risk applicants will be classified correctly.  The F1 score for high-risk applicants was 2%.
+ The precision for low-risk applicants was 100%, the sensitivity was 68% and the F1 score was 80%.
+ This model is a reliable predictor of low-risk applicants, but poor at predicting high-risk applicants.

#### SMOTE model

![image](https://user-images.githubusercontent.com/113741694/234073319-f5fe34ae-1dc2-4c7a-b3b6-e7d927d144f6.png)

![image](https://user-images.githubusercontent.com/113741694/234073368-3bdfa80d-6515-422e-90a5-d5de3b469908.png)

![image](https://user-images.githubusercontent.com/113741694/234073439-66cf8dd7-4c2f-4c0f-ac4d-b03321197e29.png)

+ The balanced accuracy score was 65%.
+ The precision for high-risk applicants was very low at 1%.  The recall for high-risk applicants was 63%, and the F1 score was 2%.
+ The precision for low-risk applicants was very high at 100%.  The recall for low-risk applicants was 66%, and the F1 score was 79%.
+ Like the RandomOverSampler model, the SMOTE model is a reliable predictor of low-risk applicants, but poor at predicting high-risk applicants.

### Undersampling

#### ClusterCentroids model 

![image](https://user-images.githubusercontent.com/113741694/234074657-a3ca17fe-7d16-488c-831c-ff786ba5ec99.png)

![image](https://user-images.githubusercontent.com/113741694/234074704-2720ba7c-9ee5-4fc6-b80e-b0e04a6791e7.png)

![image](https://user-images.githubusercontent.com/113741694/234074776-03fd58ce-921c-439e-9bd7-aa7f25e0016f.png)

+ The balanced accuracy score was 65%.
+ The precision for high-risk applicants was very low at 1%.  The recall for high-risk applicants was 63% and the F1 score was 2%.
+ The precision for low-risk applicants was very high at 100%.  The recall for low-risk applicants was 66%, and the F1 score was 79%.
+ Overall, like the previous two models, the ClusterCentroids model is an extremely reliable predictor of low-risk applicants, but extremely poor at predicting high-risk candidates.

### Combination (Over and Under) Sampling

#### SMOTEEN model 

![image](https://user-images.githubusercontent.com/113741694/234085598-34c72d39-accb-4531-b81f-ca28ecc1f405.png)

![image](https://user-images.githubusercontent.com/113741694/234085647-6be505b2-4d5d-4fd8-b843-49a43e58c76b.png)

![image](https://user-images.githubusercontent.com/113741694/234085702-ea946f62-ed40-4c06-9600-8a1294c8f300.png)

+ The balanced accuracy score was 65%.
+ The precision for high-risk applicants was only 2%.  The recall for high-risk applicants was 71%, and the F1 score was 2%.
+ The precision for low-risk applicants was very high at 100%, the recall was 59%, and the F1 score is 74%.
+ Like the previous models, the SMOTEEN model is an extremely reliable predictor of low-risk applicants, but poor at predicting high-risk candidates.  The previous models all had an average F1 score of at least 79%, making the SMOTEEN model (average F1 score is 74%) the least sensitive of the previous models.

### Ensemble Learners

#### BalancedRandomForestClassifier model

![image](https://user-images.githubusercontent.com/113741694/234088498-f5bbdd46-09c6-4e8d-b540-a9d7e665ef76.png)

![image](https://user-images.githubusercontent.com/113741694/234088542-aed688f1-211e-4c31-a035-1d0996a3e7b5.png)

![image](https://user-images.githubusercontent.com/113741694/234088585-e4ffe0d3-41c9-4fc6-866c-9888315d7dd1.png)

+ The balanced accuracy score was 78%.
+ The precision for high-risk applicants was only 3%.  The recall for high-risk applicants was 70% and the F1 score was 6%.
+ The precision for low-risk applicants was 100%, the recall was 87% and the F1 score was 93%.
+ The BalancedRandomForestClassifier model (like the other models) is not a reliable predictor of low-risk applicants.  This model, however, does have the highest average F1 score (93%) as a result of the recall for low-risk applicants being higher than the other models.

#### EasyEnsembleClassifier model

![image](https://user-images.githubusercontent.com/113741694/234090097-034f2b92-93e1-4b67-ba6b-c434c9108d24.png)

![image](https://user-images.githubusercontent.com/113741694/234090244-033a1f4b-04b7-4eb2-8758-703f09bb40a6.png)

![image](https://user-images.githubusercontent.com/113741694/234090297-35a3b5c6-dd15-4e6b-8f4f-4ad49cb16939.png)

+ The balanced accuracy score was 93%.
+ The precision for high-risk applicants was higher than the previous models, but still low at 9%.  The recall for high-risk applicants is 92% (highest of all models) and the F1 score was 16% (highest of all models).
+ The precision for low-risk applicants is still strong at 100%.  The recall for low-risk applicants is 92% (highest of all models) and the F1 score was 97% (highest of all models).
+ The EasyEnsembleClassifier model is not a good predictor of low-risk applicants, but the recall for both high and low-risk applicants was above 90% and the average F1 was 97%.

## Summary 
All the models used performed poorly in their precision rating, which is a measure of the reliability of a positive classification. The models that used a sampling technique (over-sampling, under-sampling, combination sampling) had recall scores for both applicant types between 59%-71%.  The recall for the both ensemble models was between 70%-94%, making the ensemble models a better model because they are more sensitive to the data.  Of the two ensemble models, the EasyEnsembleClassifier model (average F1 score of 97%) outperformed the BalancedRandomForestClassifier model (average F1 score of 93%).
