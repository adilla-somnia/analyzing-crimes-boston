**IA atividade 1 - analyzing crime in boston**



**article 2**

A Crime Data Analysis of Prediction Based on Classification Approaches

*https://bsj.uobaghdad.edu.iq/cgi/viewcontent.cgi?article=3922\&context=home*



## **article 1**

Machine Learning Algorithms for Visualization and Prediction Modeling of Boston Crime Data

*https://www.preprints.org/frontend/manuscript/74692c17571f927973d1781966341144/download\_pub*



**dataset(kaggle)**

*https://www.kaggle.com/datasets/ankkur13/boston-crime-data*



## **article 2**



### **models**

random forest and decision tree

### **pre-processing method**

the dataset contains records from recent crimes incidents, 2015.2 to 2018.1

it classifies the type of incident and provides info about the time and geographical location of it

it was provided by the boston department of police

it contains the 17 columns and 328k rows

info() was generated

the columns were explained

used the R package ggplot2 to visualize the data

different plots were implemented to analyze the data from different perspectives

bigvis package was used to plot a heat map, to accelerate processing speed

the data was categorized into 3 subsets

1st subset was the place of crime \[ex.: street name and coordinates]

2nd subset was about the time of the incident \[ex.: date and hour]

3rd subset was about the description of the crime \[ex.: UCR part and offense code group

a plot was created to represent the count of crime for each month as a function of years

a plot was created to show the number of crimes in different districts by years

a plot was created to observe the peaks in number of crimes in months

: August and September

a plot was created to observe the peaks in number of crimes in hour of the day

: 17h and 12h

a plot was created to compensate the influence of different total number of crimes in different years and lack of data for 2015 and 2018

convert crime numbers into percentage using the UCR parts as categories to see the tendency during the years

part one and part two categories decreased

part three increased

a plot was created to show the top 3 crimes categorized by UCR parts

there are more than 10 kinds of crimes in each UCR part

not possible to show all the info in one graph

:1st show the geographical distribution of the crimes in different UCR parts, for the part one two and three separatedly

:2nd show the part one UCR, the most severe ones, and the color of the dots indicates the type of the crime

a plot was created to show the distribution of all crimes categorized by their UCR part

part three crimes(minor ones) are more evenly distributed than the other two

a plot was created to show the coordinates where crimes occur the most (heatmap)

the result was a heavily populated city, which makes sense to have more occurrencies

a plot was created to show where shootings take place more often

the result was very different from the distribution of crimes as a whole

proposed specific question on how the crime type(UCR part) can be predict from the available data

it was concluded that crime type is related to location, which is linked to the coordinates and also possibly influenced by the time of the day.

### *decision tree*

used a R package called "rpart".

the data was cleaned and prepared for the modeling

split the data set for training and testing, 75% train 25% test

used rpart() to implement decision tree model

tried on different combinations of independent variables

best option used longitude, latitude and hour

it makes sense with the earlier conclusion

minsplit option was set to 3, based on the dispersive distribution of UCR part one and two data

Minsplit: minimum number of observations that must exist in a node in order for a split ot be attempted

model was used to make predictions with the test dataset

original data and predictions were analyzed to compare results

### *random forest*

used a R package called randomForest

the same train and test dataset from the previous model were used

used randomForest() to build the model on the train dataset

1st trail: ntree was set to 100 and nodesize to 3

ntree: number of trees to grow in the random forest model (shouldn't be set to a very small number to ensure every input gets predicted at least a few times)

nodesize: minimum size of terminal nodes (setting a larger number generates smaller trees)

used the model to predict with the test dataset, then analyzed it

### **evaluation metrics**



*for decision tree:*

two metrics, correctness of the predection and computacional speed of the model

correct of the prediction: confusion matrix, errorMatrix() from "rattle" package

computacional speed: system.time(), caluclate time elapsed during processing



*for random forest:*

same metrics, correctness and computacional speed

it was observed that a larger number of trees improved accuracy slighty though took a lot more time to process

smaller node sizes doesn't make much difference in accuracy and takes more time to process



outcome: random forest had a slightly better performance, though it took 4x more processing power


# **article 2**

this articles answers the following questions:

how the crime type can be predicted from the available data?

what are the theoretical concepts of modeling methods that applied in the field of crime prediction?

### models used

this article used the following machine learning algorithms: Decision Tree, Naïve Bayes and Logistic Regression

apparently, Decision Tree was the best the highest result

## methodology

### pre-processing method

the data was pre-processed from the missing data by using the mean of all values of that attribute and then converted into a dimensionless shape using the normalization technique in the proposed solution

the feature scaling was used to normalize raw data to a scale of 0 to 1

equation

x1 = (x1 - minx) / (maxx - minxx)

x1 = raw value of the chosen sample in the corresponding data series x

maxx = raw data value with the highest value in the respective data series x

minx = raw data value with the smallest value in the respective data series x

#### splitting dataset

the dataset was split with a percentage split method.

80% was used for training and 20% for testing

### model 1: Logistic Regression

it's a supervised leaning method

it's used to model and forecast continuos variables

it's good for classification problems.

it generates a binomial result by measuring the likelihood of something happening or not based on input variables

benefits: ease of implementation, computational efficiency, training efficiency, regularization ease.

inputs do not need to be scaled.

### model 2: Naive Bayes

it's a simplistic probabilistic classifier that constructs a set of possibilities by counting the frequency and combinations of data values

### model 3: Decision Tree

it's a supervised learning method of classification

the dataset is split into smaller parts, and the classificaiton model creates a tree from it

each left is an outcome in a tree

each node symbolizes a features

each branch denotes a decision

low-importance features are found in the lower levels of trees

each stage the DT selects a feature to best split the data using two functions: Gini impurity(the likelihood of incorrectly classifying a random sample) and Entropy(to know the value of information)

### evaluation metrics

the evaluation measures used here are: precision, recall and fl-measure

Model, Precision, Recall, Fl score
Decision Tree, 1.00, 1.00, 1.00
Naïve Bayes, 0.95, 0.94, 0.95
Logistic Regression. 0.93, 0.89, 0.90

TP: true positive
FP: false positive
FN: false negative

Precision= TP/(TP+FP)

Recall = R = TP/(TP+FN)

F1 score = 2 * Recall * Precision/(Recall + Precision)

it makes sense for the tree be more efficient since it gets as far as the longitude and latitude, and the location are strongly linked to the location

this implies only the crime scene's location can be used to create an ideal model

