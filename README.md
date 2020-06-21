# Data Science in Production

# Introduction

This is a project that shows the progress in Data Science training in production. 

Data Science in Prodution is a course taught by data scientist **Meigarom Lopes**. It teaches how to build a data science project using an easy-to-understand methodology. And in the end, he teaches how to deploy the model in production.

The challange of this project is to make a sales prevision of **Rossmann's Store**. Therefore, it's used the datasets from [kaggle](https://www.kaggle.com/c/rossmann-store-sales).

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

In this module, we learn how important it is to understand the business problem before starting a data science project.

In the case of Rossmann's Stores the business problem was to make **a sales prevision of all the stores in the next six weeks**.

So, there are four importants points to consider:

- Understand the motivation of the problem - What is the motivation for making this a sales prevision ?

    * The CFO requested this solution during a monthly results meeting.

- Understand the root cause of the problem - Why do it ?

    * The CFO wants to know the bugdet of each store to make reforms.

- Identify the project sponsor - Who's the stalkerholder ?

    * The project sponsor is the CFO.

- Understand the solution format - Granulality, for example.

    * The format solution is to make the predict of daily sales of each store in the next six weeks using predict methods.

# Module 02 - Data Description

In this module,  we start getting familiar with the dataset to understand how complex is the problem that we have to solve.

With this, we analyse some features of the data set as:

- Dataset size

    * Do we have the correct resources to work with ? 
    
    * Does the infrastrutucture support the amount of data ?
  
- Variable types

    * What variables types does the dataset have?
  
- Missing Data

    * How much missing data from the dataset ? 
    
    * Why are there missing data ?

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

- *Hypotheses about Stores*

1. Store with more employees should sell more.

2. Store with greater inventory capacity should sell more.

3. Larger stores should sell more.

4. Store with larger assortments should sell more.

5. Store with closer competitors should sell less.

6. Stores with longer competitors can sell more.

- *Hyphoteses about Products*

1. Stores that invest more in marketing should sell more.

2. Store with greater product exposure should sell more.

3. Store with low-priced products are expected to sell more.

4. Store with more aggressive promotions (bigger discounts) should sell more.

5. Stores with active promotions for longer should sell more.

6. Stores with more promotion days can sell more.

7. Stores with more consecutive promotions should sell more.

- *Hyphoteses about Time*

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

    * How is this variable ?

    * Get summary statistics (min, max, distribution, range, etc)

- **Bivariate Analysis**

    * How the explanatory variable impacts the target variable?

    * Get correlation between them.

Validate / Invalidate hypotheses.

- **Multivariate Analysis**

    * How is the relation between the explanatory variables ?

    * Get correlation between them

## 4.1. Univariate Analysis

### 4.1.1. Target Variable (Sales)

![01](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/01.png)

How we can analyse, the sales distribution is an asymmetric curve, that is,it's a curve that not follow a normal distribution.

The Machine Learning algorithms require that data follow a normal distribution because their constructions are based on a continuous probability distribution. When the data not follow a normal distribution, we can apply techniques. 

### 4.1.2. Numerical Variables

![03](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/03.png)

Analyzing the histograms, we have:

**Competition Distance:** We can see that competitiors meet in a range of 0 to 50000.

**Competition Open Since Month:** We can see that there is an increase in competition in the first months. Then in the months of May to August there is a drop / stability. And finally, in the months of September to December there is an increase and a decrease. This generates seasonality.

**Competition Open Since Year**: we can see that the competitions of open stores had an increasing increase since the 2000s. But in 2015 the number of competitions was very high.

**Customers**: We can see that the number of customers per day for the first 1000 days is higher. But then, the number of customers drops considerably.

**Day of Week**: We can see that the histogram have a uniform distribution, is that, the stores open every day of the week. 

**Is Promo**: We can see that many stores are not in promotion (promo=0) than in promotion (promo=1).

**Open**: We can see that there many stores open (open=1) than closed (open=0). This result may be influenced by stores that open on holidays.

**Promo**: we can see that there are many more stores that weren't in regular promotion (promo=0) than those who were (promo=1).

**Promo2**: we can see that there is a tie between stores that participated in promo2 and stores that did not participate in promo2.

**Promo2 Since Week**: we can observe that the graph does not present an immediate conclusion. We have that analise more.

**Promo2 Since Year**: We can observe that many stores participed of the promotion in the years 2013 and 2014.

**Sales**: we can see that there were many more sales ranging from 0 to nearly 10,000.

**School Holiday**: we can see that there many more stores that were not affected by the closure of publics schools.

**Stores**: The stores variable describe a unique Id for each store. Therefore, in this graph there is nothing to extract. 

### 4.1.3. Categorical Variable

![04](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/04.png)

Analyzing the plots, we can see that:

- Although there are many more open stores on Easter holiday, the volume of sales is larger on Christmas. This might be due to Christmas promotion sales that stores have by the end of the year

- For the stores of type a, c and d there is a high concentration of sales. In addition, for the stores of type b the volume of sales is lower and its value range is much more distributed. As the provided dataset does not clearly describe the difference between the store types, it is not possible to knows whats could be generating these differences.

- For the assortment type extended, basic there is a high concentration of sales. In addition, for the assortment extra the volume of sales is lower and its value range is much more distributed. This might be due the assortment of products each store have in stock and on sale which impacts the volume of sales.

## 4.2. Bivariate Analysys

We make the bivariate analysis of the hyphoteses final list. Therefore, follow that

### **H1. Stores with higher assortment should have higher sales.**

*FALSE Store larger assortment sells less*.

![05](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/05.png)

Assuming that largest assortments are of the extra type and analyzing the barplot, we find that sales of extra assortments are small compared to the basic and extended types. Therefore, we can conclude that **stores with larger assortments sell less**.

However, we can ask ourselves if there has been any change in sales behavior over time. For this, we will check the **sales** for each assortment during the **weeks of the years**.

![06](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/06.png)

Looking at the graph above, we can conclude that the sales of the basic and extended assortment types are practically the same over time. But, we need verify the line that describe teh sales behavior of the extra type assortment. Therefore,

![07](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/07.png)

Looking at the line graphs, we can see if the stores with the largest (extra) assortment have the least sales.

Therefore, the hyphotesis is **FALSE**

### **H2. Store with closer competitors should sell less**

*FALSE Store with closer competitors sell more*

![08](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/08.png)

Observing the results, stores with closer competitors sell more. Therefore, the hyphotese is **FALSE**.

We can also plot a scatter plot to verify this result. 

![09](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/09.png)

On the scatter plot, the concentration of the points of sale occurs in stores with closer competitors. This also confirms the hypothesis is **FALSE**.

![10](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/10.png)

Reggarding Pearson's correlation, we can see that the result of **-0,23** is a **weak negative correlation**. This explains that the further away the competitions are, the lower the store sales will be.

### **H3. Stores with longer competitions can sell more**

*FALSE Stores with longer competitions sell less*

![11](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/11.png)

Analyzing the barplot, we can see that the more negative values approach 0, the sales are higher. What does that mean ?
Means that stores with recent competitions sell more. On the other hand, stores with longer competitions sell less.
Therefore, the hypothesis is **FALSE**.

Let's plots the Pearson's correlation according to the code.

![12](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/12.png)

The Pearson's correlation is weak negative because your result is **-0,10**. But, this result is important because it influences the variable response which is sales. On the other hand, is necessary to use another type of correlation to measure the dispersion of the points and error. 

### **H4. Stores with active promotions for longer should sell more**

*FALSE Stores with active promotions for longer sell less*

### Reading of the table above

1) promo_time_week > 0: sales made inside the **extended** promotion time.

2) promo_time_week < 0: sales made inside the **regular** promotion time.

![13](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/13.png)

As we can see in the total sales x weeks in extended promotion, there is a period when the extended promotion results in more sales. After a period of time, total sales begin to decline.

From the total sales x weeks in regular promotion, we can see that, as compensation gets closer to zero, sales start to increase.

Therefore, stores with a longer promotion period do not have higher sales. The hypothesis is **FALSE**.

In relation the correlation heat map, we obtained a coeficient of **-0,029** which is very close to zero. Therefore, we have a super weak correlation. This is result makes sense because it has sales that are often constant over time.

So, maybe we won't include promo_time_week in the model. Of course, this variable might work if we combine it with another variable, but we'll leave it for the time being.

### <s>**H5. Stores with more promotion days can sell more**</s>

As this hypothesis similar to H4. We will leave to validate it in the next CRISP cycle.

###  **H6. Stores with more consecutive promotions should sell more**

*FALSE Stores with more consecutive promotions sell less*

![14](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/14.png)

Looking at the results it seems that stores with more consecutive promotions sell less. Therefore, the hypothesis is **FALSE**.

Regarding the relevance of the promo2 variable to the ML model, we can say that its relevance is low.

### **H7. Stores that open on Christmas should sell more**

*FALSE Stores that open on Christmas sell less*

![15](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/15.png)

![16](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/16.png)

As noted in the previous results, stores that open on Cristmas sell less. Therefore, the hypothesis is **FALSE**.

One observation we need to make here is that, in 2015, we still don't have Christmas sales data, because the data ends on July 31, 2015.

Maybe we can consider this relevant variables for the Machine Learning model beause we have changes in sales depending on the type of holiday state and in what year.

### **H8. Stores should sell more over the years**

*FALSE Stores sell less over the years.*

![17](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/17.png)

As noted in the previous results, stores sell less over the years. In addition, looking at the Pearson correlation coefficient of -0.92, we can see that there is a strong negative correlation between year and sales. So, the hypothesis is FALSE.

### H9. Stores should sell more in the second half of the year

*FALSE Stores sell less in the second half of the year.*

![18](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/18.png)

As noted in the previous results, stores sell less in the second half of the year. In addition, by looking at Pearson's correlation coefficient of -0.75, we can see if there is a strong negative correlation between month and sales, which means that the sales fall over time.

### H10. Stores should sell more after the 10th of each month

*TRUE Stores sell more after the 10th of each month*

![19](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/19.png)

As observed in the previous results, stores sell more after the 10th day of the month. Therefore, the hypothesis is **TRUE**.

In addition, checking the Pearson's correlation coefficient, we got a value of -0.35 which tells us that is a no so strong correlation between day and sales. However, as we have different values for total sales before and after the 10th day of the month, this variable can be relevant for our ML Model.

### H11. Stores should sell less on weekends

*TRUE Stores sell less on weekends.*

![20](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/20.png)

As noted in previous results, stores sell less on weekends. In addition, looking at Pearson's correlation coefficient of -0.76, we can see that there is a strong negative correlation between day of the week and sales.

There, the hypothesis is **TRUE**

### H12. Stores should sell less during school holidays

*TRUE Stores sell less during school holidays*

![21](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/21.png)

As noted in the previous results, stores sell less during school holidays, except in July (7) and August (8). Therefore, this hypothesis is **TRUE**.


## 4.3. Multivariate Analysis

In this section we'll check the correlations between the explanatory variables, separating the analysis for numerical attributes and categorical attributes.

### 4.3.1. Numerical Attributes

![22](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/22.png)

### 4.3.2. Categorical Attributes

To make the correlation between two categorical variables, we'll use the Cramér V method.

Please, refer to the notebook to check the calculations.

![23](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/23.png)

According to the heat map, we can conclude that the larger correlation occurs between *assortment* and *store type*. The result of 0.54 is a medium correlation. This means that the bigger the store, the higher is assortment of its products. With respect to the correlations of the other variables close to zero, we can conclude that they are weak and independent.

# Module 05 - Data Preparation

In this step, we will do the data preparation, which is the data modelation for Machine Learning training. The reason for this is that learning most machine learning algorithms is made easy with numerical data on the same scale.

#### How to prepare data ?

There are basically three process of data preparation that we can use: **Normalization**, **Rescaling** and **Transformation**.

## 5.1. Normalization

The normalization process works for those variables that have a normal distribution. Thus, normalization takes variables with these characteristics and transforms them into standardized normal distributions, that is, normal distributions with mean 0 and standard deviation 1.

We need to check the variables distributions. So, we check the distributions from section 4.1.2 Numerical variable.

![03](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/03.png)


## 5.2. Rescaling

The rescaling process works for those variables that do not have a normal distribution, that is, the variables have non-Gaussian distributions. Therefore, their intervals are rescalled containing mean 0 and standard deviation 1.

There are two methods of rescaling that we can to use in the variables. They are: **Min-Max-Scaler** and **Robuster-Scaler**

#### Min-Max-Scaler

The Min-Max-Scaler application does not change the nature of the variables, maintaining the distributions. What will change is only the interval. But, the Min-Max-Scaler application presents a problem that is related to the outliers of the variables because considering these values in the equation can bring the transformed data results very close to zero of the new scale generating a cluster.  And that takes the format out of the distribution.

Therefore, we can use the Robuster-Scaler method that uses quartiles instead of the maximum and minimum value.

#### Robuster-Scaler

Robust-Scaler is a method that can solve the outliers problem faced in Min-Max-Scale, because it uses Q1 and Q3. Thus, to apply one of the presented methods, we need to analyze the boxplot of each variable. So, if the assigned variable has many outliers we use Robust-Scaler. Otherwise, we use Min-Max-Scaler. 

Therefore, we will analyze the boxplots of each variable chosen and apply the methods.

**OBS**: This methods make part of the **sklearn.preprocessing** library.

### 5.2.1 Rescaling competition_distance

![24](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/24.png)

As observed in the results, there is a clear presence of outliers.

### 5.2.2 Rescaling competition_time_month

![25](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/25.png)

As observed in the results, there is a clear presence of outliers.

### 5.2.3 Rescaling promo_time_week

![25](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/25.png)

As observed in the results, there is a clear presence of outliers. However, they are not that far from the superior whisker. So we can take a chance to use the Min-Max Scaler.

## 5.3. Transformation

In the data preparation process of transformation, we learn to use three techniques: **Encoding**, **Response Variation Transformation** and **Nature Transformation**

### 5.3.1. Encoding

In the Encoding tecnique, we convert the categorical variable into 
numerical variable maintaining information content. So, we use **One Hot Encoding**, **Label Encoding** and **Ordinal Encoding**.

#### 5.3.1.1. One hot Encoding

One-hot encoding is used in machine learning as a tecnique to quantify categorical data. In short, this tecnique produces a vector with length equal to the number of categories in the data set.  

**OBS**: The application is in the notebook.

#### 5.3.1.2. Label Encoding

Label Encoding is a popular encoding technique handling categorical variables. In the tecnique, each label is assigned a unique integer based on alphabetical ordering.

**OBS**: The application is in the notebook.

#### 5.3.1.3. Ordinal Encoding

Ordinal Encoding is used to transform non-numerical labels into numerical labels (or nominal categorical variables). Numerical labels are always between 1 and the number of classes.

The labels chosen for the categories have no relationship. So categories that have some ties or are close to each other lose such information after encoding. The first unique values in your column becomes 1, the second becomes 2, the third becomes 3, and so on.

### 5.3.2. Response Variable Transformation

In the response variable transformation, we have that to approximate the distribution response variable to a normal distribution. This is necessary because machine learning algorithms are built on certain assumptions, and one such assumptions is that data are normally distributed. 

![02](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/02.png)


### 5.3.3. Nature Transformation

In the transformation of nature, we have to bring the true nature of the data into the data set. For example, we have the variable month that needs to be transformed because it is a cyclical variable, that is, the months are repeated each year that closes. But for that we don't just list the months 1 to 12, because if we leave the months listed, we lose the sense of the cycle because of the different distances. For example, we take the month of January 2018, we verify that it is a long distance until December 2018, but not necessarily, December 2018 is far from the month of January 2019. What happens is that December 2018 has the same distance from January 2019 as March 2018 has from April 2018. And the same distances keep the cycle.

Therefore, we use the trigonometric circle by placing the months as arcs and separating them at equal distances.

**OBS**: The application is in the notebook.

# Module 06 - Feature Selection

In this module 06, we learn to make the feature selection. This is important to facilitate the understanding of the machine learning algorithms. 

The feature selection will verify which variables of the data set are collinear, that is, variables that explain the same information, to remove them because variables of this type are not necessary to use.

There are some types of feature selection as: Filter Methods, Embedded Methods, Wrapper Methods and Boruta.

The method that will be used, in this project, is Boruta. Thus, we will to make a copy of the dataset to continue the project.

By running Boruta for our dataset, the algorithm considers the following features as relevant:

#colocar figura

Comparing the columns between the ones that we outlined in the conclusion from our hypothesis and the ones that Boruta suggested, we can see some differences.

However, this is not a problem, since we are working in an iterative process (CRISP-DS). We can first test the model using only the features that Boruta suggested, then include the one by one from our hypothesis and test to see what happens.

# Module 07 - Machine Learning Modelling

In this module, we learn that there are different types of Machine Learning (Supervised, Unsupervised and Semi-Supervised) and also how we use each one. For the our problem, we apply different supervised learning models (Average, Linear Regression, Lasso Regression, Random Forest Regression and XGBoost Regression) to compare their performances and apply Cross validation to help us decide which model we're going to use for our predictions.

we can associate important points to start using the machine learning models as:

- Set Average model as your baseline

- Start by the simplest models which are Linear Regression and Lasso Regression

- Then, go for the next level of complexity: Random Forest and XGBoost Regression)

- Avoid overfitting by applying Cross Validation training and tests.

## 7.1. Comparing Model's Performance

In the first comparison, before Cross Validation, we divided our dataset in two: training and test datsets. 

- For training, we separated all the records before the last 6 weeks of the dataset

- For test, we separated the records the last 6 weeks of the dataset.

These were the results:

![28](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/28.png)

As observed in the results, the Random Forest Regressor had the least (1011.19). However, this doesn't mean that the Random Forest is the final model that we are going to pick for our predictions, because we need to make **Cross Validation** tests for each model to check their behavior in different data and then pick the right model. 

## 7.2. Cross Validation and Comparing Model's Performance

As the model we are developing is a Time Series model, we need to divide our dataset respecting the time. So for each iteration of the **Cross Validation** , we are getting a diferent parts of our dataset based on the records dates.

These were the results:

![29](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/29.png)

As observed in the results, the Random Forest had the least RMSE. However, in this project, we're going to go with fine tuning the **XGBoost Regressor** to check the results.

# Module 08 - Hyperparameter Fine Tuning 

In this module, we learn what is the hyperparameter fine tuning. The motivation to do it is find the parameter set that maximizes the model's performance. Therefore, there are three strategies that we can to use:

- Random Search: Defines values for each of the hyperparameters randomly.

      * Advantage: Easy to implement and has low cost

      * Disadvantage: You may never be able to find the best set of values that maximizes model's performance.

- Grid Search: Defines all possible combinations of values that hyperparameters can assume.

     * Advantage: It finds the right values (or something very near) that maximizes model's performance.

     * Disadvantage: Tt can take an eternity to calculate and it has a high cost.

- Bayesian Search: Defines the values for the hyperparameters following Bayes's Theory.

     * Advantage: Define the values for the hiperparameters based on past learning.

     * Disadvantage: High complexity to learn how to implement it

For the project, we use the the **Random Search** because it is easy to implement.

## 8.1. Random Search

We have chosen the following parameters according to the code to use in Random Search

![36](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/36.png)

Depending on the parameters chosen, random Search takes time to make the choices. 

Therefore, Random Search has granted us the following performance metrics for the model.

![37](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/37.png)

For the final model, we use the metrics of line 2.

## 8.2. Final Model

![30](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/30.png)

As we can see, the final model (XGBoost) is maximized. 

# 9.0 - Error Translation and Interpretation 

In the module of Error Translation and Interpretation, we analyse the Business Performance and Total Performance of Model. This is important to understand the model's performance and to tell the CEO how much money this model will bring to the company.

Therefore, we get to learn how to translate the MAE and MAPE to business language. And the RMSE to performance model.

### Characteristics of each Error Metric

- MAE:

    * Assigns equal weight to all errors.
    * Robust in the presence of outliers, that is, invariable to outliers,
    * Easy understanding by the business team

- MAPE: 
    
    * Show how far the prediction is from the actual value, on average, as a percentage.
    * Widely used to report the results.
    * It cannot be used if response variable contains zero. If you have to predict zero, then you have to use other metrics.
    
- RMSE:

    * It gives a lot of weight to large errors.
    * Sensitive in the presence of outliers.
    * Ideal for measuring the machine learning model's performance.
    
    
## 9.1. Business Performance

![31](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/31.png)

As we can see in the results, we have the MAE and MAP metrics present. But what do these numbers mean for business performance?

In a very simple way, let's take, as an example, store 02, the MAE is R$421.41 and the MAPE is approximately 0.09. The value R$ 421.41 is the error of the average daily sale. And the percentage value over this metric is 0.09 (9%). This means that the ASM is the percentage of the MAE. Therefore, we can conclude that store 02 will have a sales forecast of R$ 170870.98 and that the average error over daily sales is R$ 421.41 for more or less, and this represents 9%.

As an interpretation, for the business team this error is relatively low in relation to the expected number of sales. This method helps the business team to make a decision.


![33](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/33.png)


In the scatterplot, we can observing the relation between the stores and your MAPE. 
There are some stores that have a MAPE above of 30%.

## 9.2. Total Performance

![34](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/34.png)

In this Table, we can see what will be the best scenario and the worst scenario predicted.

## 9.3. Machine Learning Performance

![35](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/35.png)

Observing the results, we can see that:

- By observing the first and second line plots, we can see that the predictions or our model is pretty close to the real value for sales. On the other hand, the error rate has some variance.

- By observing the histogram, the error distribution almost follows a normal distribution.

- By observing the scatterplot for the errors, the points seems well fit in a horizontal tube which means that there's a few variation in the error. If the points formed any other shape (e.g opening/closing cone or an arch), this would mean that the errors follows a trend and we would need to review our model.

# 10.0 - Deploying The Model to Production

In this module, the latter, we learn how to deploy the model in production. 

The motivation for this step is to make the predictions of the model accessible to any consumer.

Therefore, we have that to create a production architecture

![39](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/39.png)


### Task List

- Create a class with the cleaning, transformation and encoding. (Rossmann.py)

- Create an API (Handler.py)

- Create a Script to test the API

**OBS**: These files are created in the notebook

OBS: The codes of the list are in the notebook

## The Cloud Plataform

In our project, we used [Heroku](https://dashboard.heroku.com/apps)

