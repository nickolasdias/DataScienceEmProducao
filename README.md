# Data Science in Production

# Introduction

This is a project that shows my progress in Data Science training in production. 

Data Science in Prodution is a course taught by data scientist **Meigarom Lopes**. It teaches how to build a data science project using an easy-to-understand methodology. And in the end, he teaches how to deploy the model in production.

The challange of this project is to make a sales prevision of **Rossmann's Store**. Therefore, it's used the datasets from *Kaggle*.

This project is divided into 10 modules where the necessary steps to make a complete data science project are presented. They are:

- Understanding the Bussiness Problem

- Data Description

- Featuring Engineering

- Exploratory Data Analysis (EDA)

- Data Preparation

- Feature Selection

- Machine Learning Modeling

- Hyperparameter Fine Tuning

- Error Translation and Interpretation 

- Deploy Model to Production

# Module 01 - Understanding the business problem

In this module, I learn how important it is to understand the business problem before starting a data science project.

In the case of Rossmann's Stores the business problem was to make **a sales prevision of all the stores in the next six weeks**.

So, there are four importants points to consider:

- Understand the motivation of the problem - What is the motivation for making this a sales prevision ?

- Understand the root cause of the problem - Why do it ?

- Identify the project sponsor - Who's the stalkerholder ?

- Understand the solution format - Granulality, for example.

Using these points above, it was answered

- The CFO requested this solution during a monthly results meeting.

- The CFO wants to know the bugdet of each store to make reforms.

- The project sponsor is the CFO.

- The format solution is to make the predict of daily sales of each store in the next six weeks using predict methods.

# Module 02 - Data Description

In this module, I start getting familiar with the dataset to understand how complex is the problem that I have to solve.

With this, I analyse some features of the data set as:

- Dataset size

 Do I have the correct resources to work with ? Does the infrastrutucture support the amount of data ?
  
- Variable types

What variables types does the dataset have?
  
- Missing Data

How much missing data from the dataset ? Why are there missing data ?

- Summary Statistics


# Module 03 - Feature Engineering 

In this module, we learn how to create a mindmap. It helps in creating the list of hypotheses to validating the data in the phase Exploratory Data Analyses.

There are three importants points to consider:

- Phenomenal: What the phenomenal are we modeling ? In the case, we are modeling the daily store sales.

- Agents: who are the agents acting on the phenomenon of interest ? Customers, stores, assortments.

- Attributes of Agents: What's the description of the agents ? 

![alt text](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/daily_store.png)

Based on the hypothesis map, we create our hypothesis about the various stores, products and time.

## Creating Hypothesis

*Hypotheses about Stores*

1. Store with more employees should sell more.

2. Store with greater inventory capacity should sell more.

3. Larger stores should sell more.

4. Store with larger assortments should sell more.

5. Store with closer competitors should sell less.

6. Stores with longer competitors can sell more.

*Hyphoteses about Products*

1. Stores that invest more in marketing should sell more.

2. Store with greater product exposure should sell more.

3. Store with low-priced products are expected to sell more.

4. Store with more aggressive promotions (bigger discounts) should sell more.

5. Stores with active promotions for longer should sell more.

6. Stores with more promotion days can sell more.

7. Stores with more consecutive promotions should sell more.

*Hyphoteses about Time*

1. Stores that open on Christmas should sell more.

2. Stores should sell more over the years.

3. Stores should sell more in the second half of the year.

4. Stores should sell more after the 10th of each month.

5. Stores should sell less on weekends.

6. Stores should sell less during school holidays.

And we created a final list of hypotheses by choosing the most important hypotheses.

## Hypothesis Final List

1. Store with larger assortments should sell more.

2. Store with closer competitors should sell less.

3. Stores with longer competitors can sell more.

4. Stores with active promotions for longer should sell more.

5. Stores with more promotion days can sell more.

6. Stores with more consecutive promotions should sell more.

7. Stores that open on Christmas should sell more.

8. Stores should sell more over the years.

9. Stores should sell more in the second half of the year.

10. Stores should sell more after the 10th of each month.

11. Stores should sell less on weekends.

12. Stores should sell less during school holidays.

With the proposed mindmap of hypotheses, we create some variables in the data set to facilitate the exploration of the data set in the EDA phase as can be seen in the notebook.

Also, we make the variable filtering because is necessary for business restrics.

- **Variable Filtering** : it is constrained to the Business. There are variables which values you will only be able to have when a business rule is triggered in the system. So, your model will not always be able to use them at hand to make predictions.

- **Variable Selection**:picking the most relevant variables for the model. Considers the correlations between variables. It does not take into account business rules.

# Module 04 - Exploratory Data Analysis

In this module, we get to learn a lot of awesome stuff about EDA. In summary, the importance of exploratory data analysis is to understand how the variables impact the phenomenon. And from there, measure the strength of that impact.

Therefore, the three objectives of the EDA are:

- Gain business experience.

- Validate business hypotheses.

- Understand which variables are important to the business.

There are three types of Exploratory Data Analysis:

- **Univariate Analysis**

-- How is this variable ?

Get summary statistics (min, max, distribution, range, etc)

- **Bivariate Analysis**

How the explanatory variable impacts the target variable?

Get correlation between them.

Validate / Invalidate hypotheses.

- **Multivariate Analysis**

How is the relation between the explanatory variables ?

Get correlation between them


## 4.1. Univariate Analysis

### 4.1.1. Target Variable (Sales)





