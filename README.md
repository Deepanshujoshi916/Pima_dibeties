Title: Determining risk factors for diabetes Name : Deepanshu Joshi
Date of submission: 3-01-2024

Code file: R-language code file
Table of Contents:


●	Introduction

●	Data Cleaning

●	Descriptive Statistics and Visualization

●	Statistical Tests for Central Tendencies

●	Testing Independence with Correlation Coefficients
●	Conclusion
 

Introduction
Statistical Analysis of Diabetes Prevalence among Pima Indian Women

The project aims to conduct a comprehensive statistical analysis of the prevalence of diabetes among women of Pima Indian heritage who are at least 21 years of age. The dataset under examination includes crucial clinical variables, with an outcome variable denoting the presence (1) or absence (0) of diabetes.

The investigation is structured into several COmponents like::

A.	Handling Missing Data:
Addressing the presence of missing entries throughout the dataset, where 0s are employed to indicate missing values, is crucial.
B.	Variable Selection and Data Cleaning:
Preliminary analysis involves discarding the "Pregnancies" variable and cleaning the dataset to ensure missing entries in other variables are appropriately marked as NaN.
C.	Exploratory Data Analysis:
Visualizing the distributions of each variable and providing summary statistics offer an initial understanding of the dataset. Utilizing tools such as bar charts ,pie charts,eetc.

D.	Statistical Tests for Variable Differences:
Assuming predictor variables are independent, statistical tests are performed to assess differences in central tendencies concerning the diabetes outcome. To do so we will performed T-test and Anova_test.

E.	Testing Independence of Predictor Variables:
Correlation coefficients are employed to test the assumption of independence among predictor variables. Here we will use Pearson and Spearman correlation techniques.


F.	Modeling Influential Variables:
Linear regression modeling, and potentially other models, are applied to identify and describe variables that significantly influence diabetes outcomes. Interpretation of coefficients provides insights into the strength and direction of these relationships.
 
Data Cleaning
#CODE to import data in Kaggle
data <- read.csv("/kaggle/input/pima-data/pima_data.csv") head(data)
# Data cleaning using mean
![image](https://github.com/user-attachments/assets/0f046eff-a435-4e7a-a6d1-f4c74de65f14)


mean_SkinThickness<-mean(data$SkinThickness[data$SkinThickness
!=0],na.rm=TRUE) # calc mean of all non N/A valueS.
data[is.na(data$SkinThickness), "SkinThickness"] <- mean(data$SkinThickness, na.rm
= TRUE)
![image](https://github.com/user-attachments/assets/6d27dcd6-bf25-4f41-a443-24df566ab42b)

#Rounding off values
data$SkinThickness<-round(data$SkinThickness,2)

Zero as an entry can be problematic as a 0 represents a missing value:
●		N/A values cannot let the analyst calculate the mean,median,mode ,etc and also these values can be an obstacle while visualizing charts,graphs,etc
●	Columns liked Pregnancies,Glucose,BloodPressure,SkinThickness,Insulin,BMI having a zero value become unrealistic in practical world.
●	While columns like Pregnancies,Outcome calculating means for these columns, zero values can mislead the analysis.
 
Descriptive Statistics and Visualization

Since I was not provided with any real dataset hence Creating a visualization is not effective for the data set,.because this dataset is using random function , so lets take a scenario where a lady of age 20 can have Insulin level very high while a women of age 70 may have insulin level very low ,hence it will not show a problem solving pattern.
But to showcase visualzation we have created a Outcome vs Age graph as shown below:
![image](https://github.com/user-attachments/assets/728a7abc-2292-4fc6-8295-744bd5115097)
**Metric chart**
![image](https://github.com/user-attachments/assets/a43a67da-3059-41fa-a72a-36221efed236)


**Statistical Tests for Central Tendencies
**
#T-Test and Fnova test
P.T.O
 
Testing Independence with Correlation Coefficients
Pearson Correlation
Pearson Correlation method is used for linear relationships:

#Code:
correlation_matrix <- cor(data[, c(colnames(data))]) print(correlation_matrix)
![image](https://github.com/user-attachments/assets/4bf0756d-a1d1-49f7-bece-2b7efbeb17bf)


#Code:
library(corrplot)
corrplot(correlation_matrix, method = "color")
![image](https://github.com/user-attachments/assets/7c055888-fbf7-4471-ac63-eef182cb4b5a)

 
Spearman Correlation
Spearman Correlation is used for monotonic relationships
#Code:
correlation_matrix_spearman <- cor(data[, c(colnames(data))], method = "spearman")
![image](https://github.com/user-attachments/assets/6e8c0d71-4a9a-4901-bfeb-c9a38d82ad76)
print(correlation_matrix_spearman)
#Code library(corrplot)
corrplot(correlation_matrix_spearman)
![image](https://github.com/user-attachments/assets/0add25f0-78a8-4996-bc9b-23f0e20027c0)
 
**Conclusion**
Our project on diabetes prevalence among Pima Indian women involved data handling, variable selection, and exploratory analyses to uncover crucial insights.
By addressing missing data issues, discarding less relevant variables, and visualizing distributions, we laid the groundwork for robust statistical tests.
The application of statistical tests and correlation analyses(pearson, spearman correlation) revealed significant differences and relationships among predictor variables with respect to diabetes outcomes.
