#### 1. Introduction :

A modern phone comes with variety of sensors which record data for every second of their active life. The aim of Human Activity Recognition research project which built this database from the recordings of 30 subjects performing activities of daily living (ADL) while carrying a waist-mounted smartphone with embedded inertial sensors.
The complete data & related papers can be accessed at : [UCI ML Repository](https://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones)

#### 2. Attribute Information (as it is):

For each record in the dataset it is provided:
- Triaxial acceleration from the accelerometer (total acceleration) and the estimated body acceleration.
- Triaxial Angular velocity from the gyroscope.
- A 561-feature vector with time and frequency domain variables.
- Its activity label.
- An identifier of the subject who carried out the experiment.

#### 3. Goal:

- Algorithmic feature selection
- Build a classifier for identifying user activity from the given data
- Report our results for a non-academic audience

#### 4. Our Approach:

 - ##### Exploratory analysis:

  - We started with analyzing individual variables and were quickly overwhelmed by the sheer number of possible variations for combinations of these variables to look individually and actually make sense of it all

  - So, we did basic variance checks for each variable : if the variance of a given variable is very low, that variable is likely to have low impact on the output class. This is not a hard rule & we intend to use it in conjunction with other results if needed.

 - #### Variable Importance

  - We used variable importance from random forest model creation phase as an indicator of whether we should keep a particular variable in our model or remove it.

  - More about feature importance in random forest using scikit-learn [here](http://scikit-learn.org/stable/modules/ensemble.html#feature-importance-evaluation)

#### 5. Code description

  - [Exploratory analysis notebook](code/000.ExploratoryAnalysis.ipynb):

     - Correlation matrix
     - Variance check
     - Distribution plots
     - Detailed statistics for each variable


  - [Classification model notebook](code/001.RandomForest.ipynb):

    - We start with our raw dataset (*samsungData.Rda*)
    - Split this dataset into train & test (70/30)
    - Build our base model using all 561 variables
    - Select variables using variable importance scores
    - Iterate over this process till final model
    - During each iteration, we use [oob score](http://scikit-learn.org/stable/auto_examples/ensemble/plot_ensemble_oob.html) to gauge generalizability of our model


  - [PCA notebook](code/002.PCA.ipynb)

   - An attempt at looking all 561 variables using principle components


Read more about Random Forests, Bootstrap Aggregating & Variable importance scores [here](https://www.stat.berkeley.edu/~breiman/RandomForests/cc_home.htm).
