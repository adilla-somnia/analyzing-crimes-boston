# analyzing-crimes-boston

## Dataset

The dataset used in both studies is the Boston Crime Dataset, available on Kaggle:
https://www.kaggle.com/datasets/ankkur13/boston-crime-data

It contains crime incident records provided by the Boston Police Department, covering the period from February 2015 to January 2018. The dataset includes approximately 328,000 rows and 17 columns, with information related to:

Type of crime (e.g., offense code group, UCR part)
Time (date and hour)
Location (coordinates and street names)

## Article 1

Machine Learning Algorithms for Visualization and Prediction Modeling of Boston Crime Data

### Objective

This article focuses on:

- Exploring crime patterns through data visualization
- Predicting crime types (UCR categories) using machine learning models

### Methodology

#### Data Pre-processing and Exploration
- The dataset structure was examined using ``info()``
- Variables were analyzed and categorized into three subsets:
    1. Location-related features (latitude, longitude, street)
    2. Time-related features (date, hour)
    3. Crime description features (UCR part, offense group)

### Data Visualization

Visualization was performed using R packages such as ggplot2 and bigvis.

Key analyses included:

- Crime frequency over time
    - Monthly trends across different years
- Crime distribution by district
- Peak crime periods
    - Months: August and September
    - Hours: 12:00 and 17:00
- Normalized crime trends
    - Adjusted for incomplete data in 2015 and 2018
    - Findings:
        - UCR Part 1 and 2 crimes decreased
        - UCR Part 3 crimes increased
- Geographical distribution
    - Crimes mapped by UCR category
    - Heatmaps showed higher crime density in densely populated areas
- Special case analysis
    - Shooting incidents had a different spatial distribution compared to overall crimes

### Key Insight

The study suggests that crime type is strongly related to location and time, particularly:

- Latitude and longitude
- Hour of the day

### Models Used

#### 1. Decision Tree
- Implemented using the R package rpart
- Dataset split:
    - 75% training
    - 25% testing
- Best-performing features:
    - Latitude
    - Longitude
    - Hour
- Parameter:
    - ``minsplit = 3``

*Evaluation:*
- Confusion matrix (accuracy)
- Computational time

#### 2. Random Forest
- Implemented using the randomForest package
- Parameters:
    - ``ntree = 100``
    - ``nodesize = 3``

**Findings:**

- Increasing the number of trees slightly improved accuracy
- Smaller node sizes had minimal impact on accuracy but increased computation time

### Results

- Random Forest achieved slightly higher accuracy
- However, it required approximately 4× more computational resources
- Decision Trees offered a better balance between speed and performance

## Article 2

Title: A Crime Data Analysis of Prediction Based on Classification Approaches

### Research Questions

This study addresses:

- How can crime type be predicted from available data?
- What theoretical models are most effective for crime prediction?

### Methodology

#### Data Pre-processing

- Missing values were replaced using the mean of each attribute
- Data normalization was applied using min-max scaling:

´´´
​x1 = (x1 - minx) / (maxx - minxx)
´´´

- x1 = raw value of the chosen sample in the corresponding data series x

- maxx = raw data value with the highest value in the respective data series x

- minx = raw data value with the smallest value in the respective data series x


- Feature scaling ensured values ranged between 0 and 1

#### Dataset Splitting
- 80% training
- 20% testing

### Models Used

#### 1. Logistic Regression

- Supervised learning algorithm
- Used for classification via probability estimation

##### Advantages:

- Easy implementation
- Computational efficiency
- Effective with large datasets

#### 2. Naïve Bayes

- Probabilistic classifier based on feature independence
- Uses frequency and probability distributions

#### 3. Decision Tree

- Supervised classification model
- Splits data recursively based on feature importance

##### Key concepts:

- Gini Impurity: measures classification error probability
- Entropy: measures information gain

### Evaluation Metrics

> TP: true positive
> FP: false positive
> FN: false negative

- *Precision* = TP / (TP + FP)
- *Recall* = TP / (TP + FN)
- *F1-score* = harmonic mean of precision and recall

*Model	Precision	Recall	F1-score*
Decision Tree	1.00	1.00	1.00
Naïve Bayes	0.95	0.94	0.95
Logistic Regression	0.93	0.89	0.90

### Results and Interpretation

- *Decision Tree* achieved the best performance across all metrics
- The model’s effectiveness is likely due to its ability to:
    - Capture spatial patterns (latitude and longitude)
    - Split data based on highly informative features

### Final Insight

Both articles suggest that **location** is the most **significant factor** in *crime prediction*.
This indicates that:

- Geographic data alone may be sufficient to build highly accurate models
- Time variables further improve predictive performance

## Overall Conclusion

Across both studies:

- Decision Trees consistently perform well, balancing interpretability and accuracy
- Random Forest improves accuracy slightly, but at a higher computational cost
- Location-based features (latitude and longitude) are the strongest predictors of crime type
- Visualization plays a key role in understanding crime patterns before modeling
