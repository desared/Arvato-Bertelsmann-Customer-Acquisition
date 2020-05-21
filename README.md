# Arvato-Bertelsmann-Customer-Acquisition

### Table of Contents

1. [Installation](#installation)
2. [Project Overview](#motivation)
3. [Data Description](#files)
4. [Results](#results)
5. [Acknowledgements](#licensing)

## Installation <a name="installation"></a>

The following libraries are expected to be installed in this project:
- `NumPy`: large collection of high-level mathematical functions
- `pandas`: data manipulation and analysis
- `Sklearn / scikit-learn`: supports various classification, regression and clustering algorithms 
- `xgboost`: gradient boosting framework in python
- `Matplotlib`:  plotting library for the Python programming language and its numerical mathematics extension NumPy
- `Seaborn`: high-level interface for drawing attractive and informative statistical graphics
The code should run using Python 3.

## Project Overview

In this report, supervised and unsupervised learning techniques are used to analyze demographics data of customers of a mail-order company in Germany against demographics information of the existing clients. Therefore, the research question that arises is:

What are the potential customers and how can the company acquire them efficiently?

The project is designed in four main sections. 

1. `Data Preprocessing`:
Data preparation, cleaning, and transformation occurs in this section. Feature engineering is further required. These are very important steps which help building an efficient machine learning model. 

2. `Customer Segmentation`:
In this part, unsupervised learning techniques will be used to perform customer segmentation.
Principal component analysis (PCA) will be used for dimensionality reduction. Then, the elbow curve will be used to identify the most optimal number of clusters fitting the KMeans algorithm. Finally, KMeans will help the segmentation of population and will determine which of these segments is more similar to the real customers. 

3. `Supervised Learning Model`:
A machine learning model will be trained using historical responses of marketing campaigns. This model will be further used to predict which individuals are most likely to convert into becoming customers for the company.
Several machine learning algorithms will be used to build the model, while Grid Search will be used to tune the hyper-parameters. ROC-AUC curve will be used to assess the model performance. 

4. `Kaggle Competition`:
Last step is to use the most efficient model to make predictions in a test set. The results will be submitted in the Kaggle competition. 

## Data Description

The data is provided by Bertelsmann Arvato Analytics, and it includes the general population dataset, the customer segment dataset, the mailout campaign dataset and a test dataset. 

- `Udacity_AZDIAS_052018.csv`: Demographics data for the general population of Germany; 891 211 persons (rows) x 366 features (columns).
- `Udacity_CUSTOMERS_052018.csv`: Demographics data for customers of a mail-order company; 191 652 persons (rows) x 369 features (columns).
- `Udacity_MAILOUT_052018_TRAIN.csv`: Demographics data for individuals who were targets of a marketing campaign; 42 982 persons (rows) x 367 (columns).
- `Udacity_MAILOUT_052018_TEST.csv`: Demographics data for individuals who were targets of a marketing campaign; 42 833 persons (rows) x 366 (columns).

The features are described by two excel sheets:

- `DIAS Information Levels.xlsx`: Attributes name, the description, the values and the meaning of the features.
- `DIAS Attributes.xlsx`: More detailed information on the features.

I am not allowed to publish the data provided by Arvato Financial Services due to the terms and conditions.

## Results<a name="results"></a>

After performing Dimensionality Reduction using PCA, it is noticed that 200 components explain 95 percent of the variance. Therefore, 200 dimensions are kept in the data. 

Using the elbow method, it is concluded that the most optimal number of clusters is 6. The results of running KMeans in 6 clusters are as following: 99.9 percent of the customers' data can be represented by cluster 2 (1 of 6 clusters), which contains 31 percent of the general population. Therefore, people belonging to cluster 2 have a higher probability being future customers of the company.

Using the learning curves to evaluate different supervised models, Gradient Boosting results to be the most efficient model. The training score of Gradient Boosting decreases to 0.935, while the validation score increases up to 0.78. After tuning the model, the model achieved a ROC-AUC score of 0.79068 on the test data. 

## Acknowledgements<a name="licensing"></a>

I would like to thank Arvato Financial Solutions and Udacity for providing this challenging task to work with real-world data.

## Author

-   **Desared Osmanllari**   [linkedin](https://www.linkedin.com/in/desared/)
