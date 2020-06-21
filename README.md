# Machine Learning - Exoplanet Exploration

![exoplanets.jpg](Images/exoplanets.jpg)

## Background

Over a period of nine years in deep space, the NASA Kepler space telescope has been out on a planet-hunting mission to discover hidden planets outside of our solar system.
This exercise was based on the data collected from observations gathered from this telescope.

## Source information

Data source: https://www.kaggle.com/nasa/kepler-exoplanet-search-results
Content: This dataset is a cumulative record of all observed Kepler "objects of interest" — basically, all of the approximately 10,000 exoplanet candidates Kepler has taken observations on.
Column Information: https://exoplanetarchive.ipac.caltech.edu/docs/API_kepcandidate_columns.html

## Model Creation Process

1. Preprocessing the data
2. Tuning the models
3. Comparing the models

## Relevant information
- Cleaning data: In all cases the columns related to the name, id or the "classification" status of the KOI (Kepler Object of Interest) were removed, with the exception of "koi_disposition" which was the one to be used as the Outcome to be evaluated.
- Scaling data: The "MinMaxScaler" estimator was used to scale the features or input data in all models. The "LabelEncoder" estimator was used to scale the target or output data in all models.
- Tunning model: The hyper parameter tunning of the models was done with "GridSearch", by comparing and changing the values of two different parameters.


## Model Comparison

I tried 3 different escenarios to prove the accuracy of my first model, and finally compared the best one with a 4th escenario that used a different algorithm to compare such models.
These 3 escenarios differ from each other in the data set included to work with.

Escenario1: Contains 7,803 observations (explain below)

Escenario2: Contains 2,269 observations (all rows with some null values were deleted)

Escenario3: Contains 7,994 observations (columns associated to an error value were eliminated at first)


The raw database contain 9,564 records of potential exoplanets (rows) and included 50 differents caracteristics (columns).

### Model 1 - SVM
<!-- - Data used for features (X):  -->
- There were 41 different variables used to create the model. Only the variables related to a the name or id of the KOI were eliminated.  
- After cleaning the data, only 7,803 were incluided in the analysis.
- This information was assigned into the input (X) and output variables (y), and then split into the training and testing subsets.
- The model was created with the Support Vector Classification (SCV) algorithm, including a "lineal" kernel.
- After training and testing the model, it report a Training Accuracy of 0.841 and a Testing Accuracy of 0.850, which represents a good fit of the model. 
- To validate if the model could improve its performance, 4 different values of C and gamma parameters were tested within the GridSearchCV “fit” and a “score” method.
- The model accuracy after this procees improve its prediction performance, with the best combination of parameters being: {'C': 50, 'gamma': 0.0001}
- Finally comparing the accuracy score of the initial model vs its tuned model would be:

		Initial vs Tuned Model Training Accuracy: 0.841 vs 0.879

		Initial vs Tuned Model Testing Accuracy: 0.850 vs 0.884

### Model 4 - Logistic Regression

- There were 41 different variables used to create the model. Again only the variables related to a the name or id of the KOI were eliminated.  
- After cleaning the data, only 7,803 were incluided in the analysis.
- This information was assigned into the input (X) and output variables (y), and then split into the training and testing subsets.
- The model was created with the Logistic Regression algorithm.
- After training and testing the model, it report a Training Accuracy of 0.840 and a Testing Accuracy of 0.852, which represents a good fit of the model again. 
- To validate if the model could improve its performance, 4 different values of C and max_iter parameters were tested within the GridSearchCV “fit” and a “score” method.
- The model accuracy after this procees improve its prediction performance, with the best combination of parameters being: {'C': 50, 'gamma': 200}
- Finally comparing the accuracy score of the initial model vs its tuned model would be:

		Initial vs Tuned Model Training Accuracy: 0.840 vs 0.867

		Initial vs Tuned Model Testing Accuracy: 0.852 vs 0.877


## Conclusion
Although in both models its accuracy is fairly significant, the first model proves that is the one that performs better and produced the best results, specially after changing the parameters values and the model was tuned.