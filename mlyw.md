# Machine Learning Your Welcome



## Navigation

- [Terminology](#terminology)
- [Supervised Learning](#supervised)
- [Unsupervised Learning](#unsupervised)


## Terminology

___________________________________________________________________________________________________________

**Data Types:**

            Numerical: Numbers
            Categorical: Categories ie. (Plants, Customer A, Customer B, Dangerous, Safe, Something Binary)

-----------------------------------------------------------------------------------------------------------

**Feature(s):**

            Column(s) with the data in the column(s) including the column(s) name(s)

-----------------------------------------------------------------------------------------------------------

**An Observation:**

            Just a row in a data set.
-----------------------------------------------------------------------------------------------------------

**Independent Variable:**

                    A feature
                    (AKA) -> Predictor, Input Variable, Vector

**Dependent Variable:**

                    The thing that gets created or is influenced by the independent variables.
                    (AKA) -> Response / Outcome / Target Variables, The Target, Output, Supervisory Signal,
                    The Label.

**(Y) Actual Value:**

                When the value of a dependent variable is already known from a data set.

**Y Hat (Predicted Value):**

                        When the value of a dependent variable is predicted based on
                        Features/Independent Variables in a data set.

-----------------------------------------------------------------------------------------------------------


<a id="supervised"></a>

## Supervised Learning:

                        Is a machine learning approach for working with data that
                        already shares some relationship with an output which is
                        labeled, or that we have put a label on, in order to make
                        predictions.

                        The Bias-Variance Tradeoff is relevant for supervised 
                        machine learning – specifically for predictive modeling.
                        It’s a way to diagnose the performance of an algorithm by
                        breaking down its prediction error.

                        Ex.
                        Suppose we want to predict daily screen time usage for cell phone owners.
                                 _                      ____________
                                |_  Screen Time         ____________|<- Label (Dependent Variable)

                        In order to take the supervised learning approach to
                        be able to predict this we would likely need some of the following data
                        or features:
                                 _                      ____________
                                |   age                             |
                                |   weight                          |
                                |   sex                             |<- Features (Independent Variables)
                                |   income                          |
                                |   education                       |
                                |_  marital status      ____________|

                        In Supervised Learning we need a data set that already has all of the
                        Label outputs to start training a model. What does this look like?

                    Ex.(->                  INDEPENDENT VARIABLES               <-) | LABEL |
                        ________________________________________________________________________
                       | Age | Weight | Sex | Income | Education | Marital Status |{Screen Time}| <-DEPENDENT 
                        ------------------------------------------------------------------------
                    1  | 21  | 180lbs | M   |   25k  | HighSchool|   Not Married  | 6hrs 22mins | 
                        ------------------------------------------------------------------------
                                                                                    | ^TARGET^ |
                                                                                    THING WE WANT
                                                                                     TO PREDICT
                    Pretend we have a hundred rows of data like this.
                    This means we already know how long all of these people are looking at their
                    phones daily. So screen time is dependent on all of these independent variables.
                    Now we can train a supervised machine learning model with this data in order
                    to predict how much daily screen time someone might have who is
                    45 years old 160lbs Female, makes 60k a year, has Some college and is married.
                    This is supervised learning. 
                    Its supervised because we are teaching the machine learning model by holding
                    its hand, in the sense that, like a baby it doesnt already know how to connect
                    the dots so its our job to show it how based on related things.
    
    Supervised Learning Techniques: (There are two)
                                Classification:
                                Regression:



<a id="unsupervised"></a>



## Unsupervised Learning:

                        A kind of machine learning where a model must look for patterns in a dataset
                        with no labels and with minimal human supervision. This is in contrast
                        with supervised learning because an unsupervised learning model
                        wont necessarily know that the data shares any kind of similarities
                        and its going to have to look for things in the data that are similar
                        in order to group similar data together.
                        With unsupervised learning its more that we are trying to predict
                        what things are similar and with supervised learning its more
                        that we are trying to predict things based on the output
                        of known data which we already have.
                        Basically unsupervised machine learning tries to bring order
                        to a dataset and make sense of it.

                        Unsupervised process >
                        1.  Explore the structure of the information and detect distinct patterns;
                        2.  Extract valuable insights;
                        3.  Implement this into its operation in order to increase the efficiency
                            of the decision-making process

                        A practical example of unsupervised learning is
                        Social Network Analysis:
                            Which is conducted to make clusters of friends depending
                            on the frequency of a connection between them.

                        Applicable in:
                            Clustering Problems and association problems
                            such as pattern recognition.
                    
                        Accuracy:
                            May provide less accurate results because many
                            times its kind of a shot in the dark since
                            you might not even know ballpark what your
                            trying to find or what you want to find.

                        Algorithms:
                            K-Means
                            Gaussian Models
                            Frequent patterns (FP) Growth
                            Principal Component Analysis

                        Use Cases:
                            Recommender Systems
                            Anomaly Detection
                            Customer Segmentation
                            Preparing data for supervised learning.



    ----------------------------------------------------------------------------------------------------------
Deeper underlying understanding of algorithms and machine learning models.
    Bias and Variance Trade Off:
                                Similar to the concept of overfitting and underfitting.

## Low variance (high bias):

                                algorithms tend to be less complex,
                                with simple or rigid underlying 
                                structure.
                                They train models that are consistent,
                                but inaccurate on average.
                                These include: 
#   <-                          linear or parametric algorithms such
#     <-                        as regression and naive Bayes.

#<-                             On the other hand 
#                               Low bias (high variance):
                                algorithms tend to be more complex, 
                                with flexible underlying structure.
                                They train models that are accurate
                                on average, but inconsistent.
                                These include:
#   <-                          non-linear or non-parametric 
#    <-                         algorithms such as decision trees 
#     <-                        and nearest neighbors.
                
                This tradeoff in complexity is why there’s a tradeoff in bias and variance – 
                an algorithm cannot simultaneously be more complex and less complex.

                                Bias:
                                        Is the difference
                                        between your
                                        models expected
                                        prediciton and
                                        the true values.
                                Low Bias:
                                        A low bias model will closely match
                                        the training data set.



                                High Bias:
                                        A model with a higher bias 
                                        would not match the data set closely.

                                    Characteristics of a high bias model include:
                                            Failure to capture proper data trends
                                            Potential towards underfitting
                                            More generalized/overly simplified
                                            High error rate


                                Variance:
                                        Refers to an algos
                                        sensitivity to 
                                        specific sets of
                                        training data

#                                       Break Down:
                                        Variance is really
                                        how well the
                                        algorithm your using
                                        is learning from the data.
                                        Maybe certain data sets
                                        for whatever reason
                                        are just not good or
                                        effective at teaching
                                        the algorithm how to
                                        make predictions.
                                        So low variance 

                                    Characteristics of a high variance model include:
                                            Noise in the data set
                                            Potential towards overfitting
                                            Complex models
                                            Trying to put all data points as close as possible
                                            
                                    Models with high bias will have low variance.
                                    Models with high variance will have a low bias.
#Linear Regression
*Theta is also called the parameters or weight vector of the regression equation*
##The key point in the linear regression is that or dependent value should be continuous and not be a discrete value'
'' The Independent variable can be measured on either a categorical or continuous measurement scale''
There are two types of linear regression:(when there is only one independent variable present)
    Simple linear regression:
        Predict co2emission vs EngineSize of all cars
            -Independent Variable (x): Engine Size
            -Dependent variable (y): co2emission

Multiple linear regression:(when there are more then one independent variable present)
    Predict co2emissions vs EngineSize and Cylinders of all cars
        -Independent variable (x): Enginesize, cylinders, etc..
        -Dependent variable (y): co2emission

>NOTE:
*In the line equation (y = mx + c), m is a slope and c is the y-intercept of the line*
|_*In the given equation, theta-0 is the y-intercept and theta-1 is the slope of the regression line.*


##  Formula of a line aka how to draw a straight line through a sample
    Formula = a + bx1
    a = The intercept (Y intercept)
    b = The slope of the line
    x = The independent variable(s)
    y = The dependent variable
    Σ = The sum of multiple items

    How do we get (a) the damn Intercept? 
    How do we get (b) the damn slope of the line?

    Ex. ________________________
##      | X | Y | X^2 | (X)(Y) |  <- Column Names
        ------------------------
        | 2 | 3 |  4  |   6    |  0
        ------------------------
        | 4 | 7 | 16  |   28   |  1
        ------------------------
        | 6 | 5 | 36  |   30   |  2
        ------------------------
        | 8 |10 | 64  |   80   |  3
        ------------------------
##      |20 |25 | 120 |   144  |  Σ <- SUM OF COLUMN
        ------------------------

##Ex.<- a = (((ΣY)*(ΣX^2))-((ΣX)*(ΣXY))) / n(rows)*(ΣX^2)-(ΣX)^2 -> The Intercept

OR ->   a = ((25*120) - (20*144)) / (4*120-(20)^2)  <- For the table above

##Ex.<- b = ((n*(ΣXY))-((ΣX)*(ΣY))) / (n*(ΣX^2))-(ΣX)^2

OR ->   b = ((4*144)-(20*25)) / (4*120 - (20)^2) <- For the table above

##Model evaluation approaches:
    Train and test on the same data set:
        This is taking the entire data set and building a training model based on it and then
        to test the accuracy of the model you take a small sample size from the data set without
        the labels and build a test training set. The labels are called actual values of the test set. Finally after
        we run our test model we check the new predicted values with the actual values to get an idea
        of our models accuracy. The error of the model is calculated by the average difference between the predicted and
        actual values for all of the rows.
    -Training accuracy: is the percentage of correct predictions that the model
                        makes when using the dataset.
                        -However a high training accuracy is not always a good thing.

        -Over-fit:  Occurs when the model is not good at making prediction
                    on data that is has not been trained with.
                    The model can recognize things that are very
                    closely similar to the stuff its been trained with
                    but as soon as you give it something that is
                    outside of that scope it cant make accurate predictions
                    on what its taget value should be.
                    The model is overly trained to the dataset, 
                    which may capture noise and produce a non 
                    generalized model.

        Under-fit:  Occurs when the model is unable to match the input data to
                    the target data.

    Out of sample accuracy:
        is the percentage of correct predictions that the model makes on data that model has not been trained on.
        Doing a train and test on the same data set will likely have a low out of sample accuracy due to the liklihood
        of being over-fit.
        Its important that our models have high out of sample accuracy because we want the model to be able to
        make predictions on unknown data.
        How can we improve out of sample accuracy??? 
    Tran/Test Split:
        Training the model on only a portion of the data and omitting a portion of the data to be used in a second
        test model. This results in a higher level of out of sample accuracy because the original training
        set has no record of the data in the test set which means we can get a better idea
        if the model is actully doing its job by comparing the values produced in both training models.
        So in essence this is truly out of sample testing.
    K-Fold cross validation:
        Is another evaluation model which resolves alot of the issues which are left behind in the train/test split evaluation method.
        Basic concept: You take the entire dataset and split it into 4 portions or 4 folds. You use the first 25% of the data for testing
        and the rest for training. Then you take the next 25% of the data and do the same thing untill you are at the last 25% of the data.
        Finally the results of all 4 evaluations are averaged that is the average of each fold is averaged. Keeping the data distinct
        where no training data is used in another.
        K-Fold cross validation in its simplest form performs multiple train/test splits.
Regression Evaluation Metrics

Best approach for most accurate results in a training model.
    
#Evaluation Metrics
(In the context of regression the error of the model is the difference between data points and the trend line generated
by the algorithm and with multiple data points an error can be determined in multiple ways.)

    Mean absolute error - The mean of the absolute value of the errors.
        --The easiest of the metrics to understand since its just the avg error.

    Mean squared error -The mean of the squared error.

    Root mean squared error -  The square root of the mean squared error. -- Popular because it is interpretable in the same units
    as the responde vector or Y units.

    *Relative squared error - is used for calculating R-squared -- a popular metric used for calculating the accuracy of a model.
    It represents  how close the data values are to the fitted regression line. The higher the r squared the better the 
    model fits the data.

#Multiple Linear Regression (Where Y(dependent variable) is a linear combination of independent variables(X,X...))
(is a method of predicting a continuous variable. It uses multiple variables called independent variables or predictors
that best predict the value of the target variable, 'the dependent variable'.)
    
Note: Theta transpose X in a one dimensional space is the equation of a line. Its what is used in simple linear regression.
in higher dimensions when we have more than one input or X the line is called a plane or a hyper-plane,
and this is what is used for multiple linear regression.
The whole idea is to find the best fit hyper-plane for our data.
    Examples -
        Independent variables effectiveness on prediction
            -Does revision time, test anxiety, lecture attendance and gender
            have any effect on the exam performance of a student.
            --What is the dependent and what are the independent variables here.
            The dependent variable or label is is (performance of a student) - *also called the outcome variable*
            The independent variables or features are (anxiety, lecture attendance and gender)


        Predicting impacts of changes
            Ex. How much does blood pressure go up (or down) for every unit increase
            or (decrease) in the BMI of a patient?
#Estimating multiple linear regression parameters
-We want to be able to find the best parameters(theta, independent variables) to feed into our multiple
linear regression model so we can generate the most accurate predictions in our outcome variable.
So in essence we want to try and use the features which will result in the lowest mean squared error.

Question: How do we find the parameter or coefficients for multiple linear regression?
    Ordinary least squares - (used on data sets with less than 10,000 lines or smaller data sets)
        Attempts to estimate the values of the coefficients by minimizing the mean squar error MSE.
        This approach uses the data as a matrix and uses #Linear Algebra# operations to estimate the
        optimal values for the theta(independent variable).

    Optimization approach - (used on larger data sets)
        -Some kind of optimization algorithm
            -Gradient Descent
Note: After we found the parameters of the linear equation we can move on to the prediction phase.

#Making predictions with multiple linear regression
#Model evaluation in regression models:
*(The goal of regression is to accurately predict an unknown case to this end 
we have to perform regression evaluation aftetr building the mode)*
 Two types of evaluation appraoches to achieve this goal are.
##Train and test on the same data set
Basically training on the entire data set and building a model using the training set.
Then we select a sample portion of the data set and create a test model with it. The test set 
does not contain the labels and instead we simply use the labels to check against the test models predictions.
In the test model the labels are called actual values.

We compare the actual values Y with the predicted values Y hat.

*This is the simplest evaluation approach*
results:
Has a high training accuracy and low out of sample accuracy.
Since the model knows all of the testing data from the trainings

  Training accuracy - is the percentage of correct predicitons that the model makes when using the test data set.
  caveats: High training accuracy is not necessarily a good thing as it can result in over fitting
    -Over Fit: The model is overly trained to the dataset, which may capture noise and 
    produce a non-generalized model.

  Out of sample accuracy - The percentage of accurate predcitions that the model makes on data that it has not been trained on.
    -Its important to obtain high out of sample accuracy because the purpose of our model is to make correct predictions
    on unknown data.
##Train/test split
Involves splitting the data set into training and testing sets respectively, which are mutuall exclusive. After which
you train with the training set and test with the testing set.
This will provide a more accurate evaluation on out of sample accuracy because the testing data set is not part of 
the data set that has been used to train the model.

    -caveats: Highly dependent on the data sets by which the data was trained and tested.

##K fold cross validation
Resolves most of the issues with train/test split model evaluation method.
How to fix a high variation which results from a dependency?..You avg it.
--Split the data up into 4 folds:
    1st fold: Use the first 25% of the data for testing and the rest for training.The model is built using the training
    set and is evaluated using the test set.
    2nd fold: use the second 25% of the dataset for testing and the rest for training the model.
    3rd fold: use the third 25% of the dataset........
    4th fold: etc......
  Finally: The result of all 4 evaluations are averaged.
##Regression evaluation methods

#Accuracy metrics for model evaluation(Evaluation metrics in regression models)
Regression accuracy: Evaluation metrics are used to explain the performance of a model.
Basically we can compare the actual values and predicted values to calculate the accuracy of a regression model. 
##What is an error in the context of regression.
    -The difference between the data points and the trend line generated by the algorithm.
    Measure of how far the data is from the fitted regression line.
    Since multiple data points exist an error can be determined in multiple ways.
##MAE(Mean absolute error) -Easiest to understand since its just the avg error.
    -The mean of the absolute evaluated of the errors
##MSE(Mean squared error) -More popular than MAE cause focuse is geared more towards large errors.
    -The mean of the squared error

##RMSE(Root mean squared error)-Most popular
Interpretable in the same units as the response vector or y units.
    -The square root of the mean squared error
##RAE(Relative absolute error/ residual sum of square)-Highly adopted in the datascience community because
##it is used to calculate R^2
    -takes the total absolute error and normalizes it by divind by the total absolute error of the simple predictor.
##R squared (not an error persay)
    -It represents how close the data values are to the fitted regression line. The higher the R squared the better the
    model fits your data.

#Types pf regression models:

##Simple Linear regression
    -When one independent variable is used to estimate a dependent variable.
    Ex. Predict CO2 emission vs enginesize of all cars.
      Independent Variable: (x) Engine Size
      Dependent Variable:(y) CO2emissions

##Multiple linear regression
    -When more than one independent variable is used / when multiple independent variables are present.

#Multiple linear regression:
  Independent variables effectiveness on prediction
    -Ex. Does revision time, test anxiety , lecture attendance and gender have any effect on the exam performance 
    of the student.

  Predicting impacts of changes:
    -Understanding how the dependent variable changes when we change the independent variables.


______________________________________________________________________________________________________________________________
#Classification
*(A supervised learning approach, categorizing some unknown items into a discrete set of categories or "classes"
classification attempts to learn the relationship between a set of featured variables and a target variable of interest.)*
    -The target attribute in classification is a categorical variable with discrete values.

##How classification and classifiers work?
Given a set of training data points along with the target labels classification
determines the class label for an unlabeled test case.

    Ex.
    Loan default prediction:
    Previous loan default data can be used to predict which customers are likely to have problems paying loans.
    High risk customers can either be turned down or offered other products.

    The goal of a loan default predictor is to use existing loan default data, which is, info about the customers
    such as age, income and education to build a classifier, pass a new customer or a potential future defaulter to the model and 
    then label it ie. the data points as defaulter or not defaulter or 0 or 1. This example is about a binary classifier
    with two values. 

    We can also build classifier models for both binary and multi class classification.
    
##Multiclass classification
    ex.
    Data collected on a group of patients that had the same illness and responded to one of three different types of medications
    they took during the course of their treatment.
    This labeled dataset can be used with a classification algorithm to build a classification model.
    Then you can use it to find out which drug might be effective for future patients with the same illness.
__________________________________________________________________________________________________________________________________________
#K-Nearest Neighbors algorithm (a specific type of classification)
*The K-Nearest Neighbors algorithm is a classification algorithm that takes a bunch of 
labeled points and uses them to learn how to label other points. 
This algorithm classifies cases based on their similarity to other cases. 
In K-Nearest Neighbors, data points that are near each other are said to be neighbors. 
K-Nearest Neighbors is based on this paradigm.*

_______Breaking down this transcript_________:
###Definition:::::::::::::::::::::::::::::::::::::::::::::::::
The definition of K nearest neighbors is explained well enough.
Its an algorithm that helps classify data so its a (classification algorithm).


## How does it classify data
   It classifies data based on that data's similarity to other data.
   Data that is closely similar to each other, are called neighbors.
   K represents, (some number), how ever many neighbors that are close to a specific data point.

   In the tutorials definition its explained that the algorithm takes a bunch of
   "labeled" points and uses them to learn how to label other points.
   Labeled points in this case ,based on the example, are different kinds of
   customer groups or categories that a telecommunications provider created
   to classify their customers.
   These groups/categories/classes or "labeled points' are:
   Basic Service, E Service, Plus Service and Total Service.

   Lets pretend:
    (A) Basic Service - A moderate user. Doesnt text alot, doesnt make tons of calls etc..
    (B) E Service - Uses their data more than average, above the amount of a Basic Service user/customer.
    (C) Plus Service - A customer/user that uses all services above the amount of a Basic Service user/customer.
    (D) Total Service - A customer/user that uses any service above the amount of a Plus Service user/customer.

   Predicting:
    Now lets say we have a new customer on the phone and we want to know what class/category
    this customer may fall into. In order to find out we might first want to
    look at some data/information from customers in all of the service categories
    so lets start with age and income.
    
   Lets pretend:
    (A) Basic Service - customers tend to be either over the age of 45 or have an income under 25k or over 125k
    (B) E Service - customers tend to be under 30 years old with an income of under 40k
    (C) Plus Service - customers tend to be over 30 years old and under 45 years old with an income above 40k
    (D) Total Service - customers tend to be between the ages of 20 - 36 years old with an income above 60k
    
    We find out our new customer is under 30 and makes 33k a year.
    With this data can we make a guess as to which service group they may fall into?
    Yes.

#Evaluation Metrics (used for Classification)::::::::::
    -Evaluation metrics provide insight into areas that might require improvement.
        -Help us determine how accurate a given model is by comparing the actual values
        in a test set with the values predicted by the model.

##  |Different kinds of model evaluation metrics::::::::::::::

###     Jaccard Index (Jaccard similarity coefficient)
            Compares members of two data sets to see which members are shared and which are distinct.
            It’s a measure of similarity for the two sets of data, with a range from 0% to 100%.
            The higher the percentage, the more similar the two data sets are.

##          Steps:: ( J(X,Y) = |X∩Y| / |X∪Y| ) <- Formula
                (1). Count the number of members which are shared between both sets.
                (2). Count the total number of members in both sets (shared and un-shared).
                (3). Divide the number of shared members (1) by the total number of members (2).
                (4). Multiply the number you found in (3) by 100.
                __This percentage tells you how similar the two sets are.__

##          Caveat::
                Although it’s easy to interpret, it is extremely sensitive to small samples
                sizes and may give erroneous results,especially with very small samples or 
                data sets with missing observations.

###     F1 Score
            An evaluation metric that measures a models accuracy. 
            It combines the precision and recall scores of a model.
            The accuracy metric computes how many times a model made a correct
            prediction across the entire dataset.

##          How to calculate F1 score?
            To understand the calculation of the F1 score, we first need to look at a
            -> Confusion Matrix. (A matrix of numbers that tell us where a model gets confused)
                -a class-wise distribution of the predictive performance of a classification model
                the confusion matrix is an organized way of mapping the predictions to the original 
                classes to which the data belong.

            For a binary class dataset (which consists of, suppose, “positive” and “negative” classes),
            a confusion matrix has four essential components:

                1. True Positives (TP): Number of samples correctly predicted as “positive.”
                2. False Positives (FP): Number of samples wrongly predicted as “positive.”
                3. True Negatives (TN): Number of samples correctly predicted as “negative.”
                4. False Negatives (FN): Number of samples wrongly predicted as “negative.”

            The F1 score is defined based on the precision and recall scores,
            which are mathematically defined as follows:
                Precision = TP / TP + FP
                Recall = TP / TP + FN
            The F1 score is calculated as the harmonic mean of the precision and recall scores.
                F1 Score = TP / TP + 1/2(FP + FN)

##          Caveat::
            This can be a reliable metric only if the dataset is class-balanced, meaning each class
            of the dataset has the same number of samples.

##          Cross Entropy:
                The difference between two probability distributions.
###     Log Loss (cross entropy loss)
            Log-loss is indicative of how close the prediction probability (Y hat) is to the corresponding
            actual/true value (Y), (0 or 1 in case of binary classification).  The more the predicted 
            probability diverges from the actual value, the higher is the log-loss value.
#Decision Trees::::::::: <'How is one built based on the data' -> ?
        Decision Trees are classification algorithms
    Built using recursive partitioning (breaking up the data further and furter down the line)
##        Ex.                <'Age'>
##                     /        |         \
##               <'Young'>  <'Mid-Aged'>  <'Senior'>
    Decision trees are built by splitting the training set into distinct nodes.
##          Realistic example:
                Patients with a illness that have all recieved two types of medication
                    Drug (A)
                    Drug (B)
                Feature sets or categories we can start looking at:
                    Age (Young, Middle Aged, Senior)
                     Sex (M, F)
                      Blood Pressure (Normal, High, Low)
                       Cholesterol (Normal, High, Low)

                Basically all patients will have all of these attributes
                and our target is the drug that they responded to meaning
                since all of the patients were given both drugs we have
                a list of which patients responded to either drug and we want
                to group these patients to find out how likely someone not
                in the sample set will respond to either of the medications.

                Some examples of things we might find:
                                    
                    Patient Age	Sex	BP	Cholesterol	Drug(Response)
                        1	23	F	HIGH	HIGH	drug(A)
                        2	47	M	LOW	    HIGH	drug(B)
                        3	47	M	LOW	    HIGH	drug(B)
                        4	28	F	NORMAL	HIGH	drug(A)
                        5	61	F	LOW	    HIGH	drug(A)
                        6	22	F	NORMAL	HIGH	drug(A)
                        7	49	F	NORMAL	HIGH	drug(B)
                        8	41	M	LOW	    HIGH	drug(B)
                        9	60	M	NORMAL	HIGH	drug(B)
#-----------------------------------------------------------------------------------------------------------
#                                           Regression Trees
Concept:    A regression tree is a decision tree that can take continuous values
            as the target variable instead of a discrete value.
            The basic idea behind regression trees is to split our data into groups
            based on features, like in classification, and return a prediction that
            is the average across the data we have already seen.

Use Cases:  It seems like regression trees are good to use in situations where you
            want to be able to predict the range of something or for problems
            that deal with categorical sequences.
            Truly though, regression trees are used for dependent varaibles with
            continuous values and classification trees are used for dependent 
            variables with discrete values.
            Categorical Sequence: A sequence of something that has
            categories like Dogs and dog breeds

        In a regression tree each leaf represents a numeric value.
        In contrast classification trees have true or false in thier leaves
        or some other discrete category.

        Ex.
            Drug effectivness based on a few different categories

                                [Age > 50 ]
                                /               \
                        [4.2% effective]    [Dosage >= 29]
                                            /           \
                                    [29% Effective]     [sex = Female]
                                                        /            \
                                            [100% Effective]    [50% Effective]

                                    

#-----------------------------------------------------------------------------------
#Intro to Logistic Regression
        More often used in binary classification problems.
        Can be more effective for these cases than linear regression.
        
        Sigmoid Function - Main part of Logistic Regression

        What is logistic regression?
            -Logistic Regression is a statistical and machine learning technique for classifying
            records of a dataset based on the values of the input fields.
            -Logistic Regression is analogous to linear regression but tries to predict
            a categorical or discrete target field instead of a numeric one.
            ie. Something binary: (Yes, No), (True, False), (Success, Failure), (Pregnant, Not Pregnant),
            (probability of heart attack: Yes, No), (chance of mortality in an injured patient),(Liklihood of a customer purchsing a product),
            (liklihood of a customer cancelling a subscription based service)
            Note: Notice that in all these examples not only do we predict the class of each case,
            we also measure the probability of a case belonging to a specific class.

        What kind of problems can be solved using it?
        -Could be used in binary classification or
        multi-class classification.

        In which situations should we use it?
        First: When the target field is binary .
        Second: When you need the probability of your prediction.
        (Logistic Regression predicts the probability score between zero and one for a given sample of data)
        
        Y is the labels vector also called the actual values.
        Y(hat) is the vector of the predicted values of our model.


    Parameters of Logistic Regression ( Things it needs to work)
        -Independent variables need to be continuous or
        if categorical they should be dummy or indicator coded.
        ie. Transformed into continous data if not otherwise.
## The training process

1. Initialize  Θ Theta
2. Calculate ŷ = σ(ΘT X) for a customer
3. Compare the output of ŷ with actual output of customer, Y, and record it as error.
4. Calculate the error for all customers.
5. Change the theta to reduce the cost.
6. Go back to step 2.

##  How can we change the value of theta so that the cost is reduced across iterations?
There are different ways to change the value of theta but one of the most popular ways is gradient descent.
##  When should we stop the iterations?
By calculating the accuracy of your model and stop it when  its satisfactory

##      Training a logistic regression model and how to change the parameters of the model to better estimate the outcome.
##      (The cost function: <- is the difference between the actual values of Y and our model output or predicted values Y-hat
            -A general rule for most cost functions in machine learning: The cost function is basically the error.

        The main objective of training in logistic regression is to change the parameters of the model
        so as to be the best estimation of the labels of the samples in the dataset.

        First: We look at the cost function and see what the relation is between the cost function and the parameters theta.

        How do we find the best weights or parameters that minimize the cost function?
        -Answer: We should calculate the minimum point of this cost function and it will show us the best parameters for our model.
        Although we can find the minimum point of a function using the derivative of a function it may be too complicated or
        too much of a process to do so. Which means we should find another cost function instead.
        One that has the same behavior but is easier to find its min point.

        Basically we are going to use the minus log function -log.
        So the idea behind this is that suppose we want a value of 1 which is our desired output
        this means we want need a cost function that wiil return us 0. -log(ŷ)
        What this means is if our predicted output is 1 and our actual value is 1
        than our cost function is 0 meaning there is no error basically. 
        If our predicted value is less than 1 and our actual value is 1
        than our cost function is going to give us a value greater than 0.
        
        If desirable y = 1 then -log(ŷ)
        If desirable y = 0 then -log(1 - ŷ)
        This concept is part of the Logistic Regression cost function.

        Remember that ŷ does not return a class but rather a value of either 0 or 1 which should be assumed as a probability.

##      Minimizing the cost function of the model (recap)
        How to find the best parameters for our model?
        -Minimize the cost function

        How to minimize the cost function?
        -Use gradient descent.

        What is gradient descent?
        -An iterative approach to finding the minimum of a function.
        -A technique to use the deriviative of a cost function to change the parameter values,
        -in order to minimize the cost.
        
        Using Gradient descent to minimize the cost.
        How can gradient descent to this?

##      Training algorithm recap

        1. Initialize the parameters randomly.
        2. Feed the cost function with training set, and calculate the error.
        3. Calculate the gradient of the cost function.
        4. Update weights with new values.
        5. Go to step 2 until the cost is small enough.
#<-NOTE:   We continue this loop until we reach a short value of cost or some limited number of iterations.
        6. Predict the new customer X. The parameter should be roughly found after some iterations.



#   Support Vector Machines





#   Multi Class Prediction




#   Clustering (Intro to clustering)

##      <- ( Definition ) ->
            Clustering is an unsupervied machine learning method of identifying and
            grouping similar data points in large data sets without concern for the specific
            outcome.
            In other words clustering takes on the task of finding similarities between
            groups of features and then based on those similarities it creates new groups.
            Clustering (sometimes called cluster analysis) is usually used to
            classify data into structures that are more easily understood and manipulated.

##     <- (    Caveat   ) ->
            The biggest issue that comes up with most cluster analysis methods is that 
            while they're great at intially seperating data into subsets, the strategies
            used are sometimes not necessarily related to the data itself, but to its
            positioning in relation to other data points.

#       Applications of Clustering in different fields  

            Marketing: It can be used to characterize & discover customer 
            segments for marketing purposes.

            Biology: It can be used for classification among different species 
            of plants and animals.

            Libraries: It is used in clustering different books on the basis of
            topics and information.

            Insurance: It is used to acknowledge the customers, their policies 
            and identifying the frauds.

            City Planning: It is used to make groups of houses and to study 
            their values based on their geographical locations and other 
            factors present. 

            Earthquake studies: By learning the earthquake-affected areas we can determine
            the dangerous zones.

            Image Recognition: It us used to train a model into recognizing or
            distinguishing object from one another.

            Cross selling strategies:

            Customer Segmentation: ie. Splitting up customer groups or finding them
            and labeling them.


        Why Clustering? 
        Clustering is very important as it determines the intrinsic grouping among 
        the unlabelled data present. There are no criteria for good clustering. It depends 
        on the user, what is the criteria they may use which satisfy their need. 
        For instance, we could be interested in finding representatives for homogeneous 
        groups (data reduction), in finding “natural clusters” and describe their unknown 
        properties (“natural” data types), in finding useful and suitable groupings 
        (“useful” data classes) or in finding unusual data objects (outlier detection). 
        This algorithm must make some assumptions that constitute the similarity of 
        points and each assumption make different and equally valid clusters. 

        Customer Segmentation:
            The practice of grouping customers based on similar attributes.
                                            <- Caveat ->
            A general segmentation process is not usually feasible for large volumes
            of varied data, therefore you need an analytical approach to deriving 
            segments and groups from large datasets.


#       A Practical Example:
            
            Suppose we have a customer data base and we want to find some
            similarites between these customers.
            Now suppose we create a machine learning model and apply
            a clustering algorithm to the data we input into our model.

            The clustering algorithm might return three groups of customers
            that we see have been grouped by demographic data.
                Groups:
                        (A). Affluent Middle Aged People
                        (B). Young Educated, Mid Ranged Income People
                        (C). Young and Low Income People

            Clustering is often used to make recommendations to users
            based on similars users taste or based on similar habits.
            A clustering algorithm might recognize that you interacted 
            with a particular add for 2 minutes and then based on other
            people who exhibited the same behaviour from its records
            it might also recommend you a shampoo or something because
            people that fall into the category of interacting with that
            specific add for that length of time typically bought this
            one shampoo shortly after.

            So basically clustering algorithm be like:
                    Hey bro I see you did like these other peeps,
                    that like this one thing, who then after also like
                    this other thing. Maybe you like this other thing
                    too?


##      Generally clustering can be used for one of the following purposes:

            Exploratory data analysis 
            Summary Generation or Reducing The Scale
            Outlier detection - especially to be used for fraud detection or noise removal
            Finding Duplicates and Datasets 
            As a pre-processing step for either prediction, other data mining tasks or
            as part of a complex system

#       Different Clustering Algorithms:
            Partition Based Clustering:
                Group of clustering algorithms that produce sphere-like clusters.
                These algorithms are relatively efficient and are used for medium 
                and large sized databases.
        ↓←←←←←←←←←←←←←←←←←←
#   ↓   ↓  < < <  K-Means <
        ↓←←←←←←←←←←←←←←←←←←
        ↓         K-Medians (Fuzzy c-Means)
        ↓   
        ↓       Heirarchical Clustering Algorithms:
        ↓       Produce Trees of Clusters.
        ↓       This group of algorithms are very intuitive and are generally good
        ↓       for use with small size datasets.
        ↓           
        ↓          Agglomerative
        ↓          Divisive
        ↓    
        ↓       Density Based Algorithms:
        ↓       Produce arbitrary shaped clusters.
        ↓       Especially good when dealing with spatial clusters or when there is
        ↓      noise in your data set.
        ↓
        ↓
        ↓          DBSCAN: 
        ↓               Density-based Spatial Clustering of Applications with Noise 
        ↓               These data points are clustered by using the basic concept that the data
        ↓               point lies within the given constraint from the cluster center. 
        ↓               Various distance methods and techniques are used for the calculation of the outliers. 
        ↓
#       →>> → → Intro to K-Means: (Is an iterative algorithm)

                    K-means clustering algorithm – It is the simplest unsupervised learning algorithm
                    that solves clustering problems. K-means algorithm partitions n observations into k 
                    clusters where each observation belongs to the cluster with the nearest mean serving 
                    as a prototype of the cluster. 

                    K-means divides the data into non-overlapping subsets
                    (clusters) without any cluster internal structure.'
                    Examples within a cluster are very similar.
                    Objects across different clusters are very diffferent
                    or dissimilar.
                    Note:> This make sense since there are non-overlapping subsets.

            Questions:
                How can we fid similarity of samples in clustering?
                How do we measure how similar two customers are with regard
                to their demographics?

            Answers:
                Sometimes in order to do this we can, instead of measuring
                how similar samples are. We can instead measure how different
                they are or how dissimilar they are.

           K-Means tries to minimize the amount of differences inside of a cluster
           and maxamize the amount of differences for clusters outside of a cluster.
           ie.  Intra cluster distances are minimized
                Inter-cluster distances are maximized

            In order to calculate the distance we use the Euclidean Distance or
            the Minkowski distance
            We can use this dame distance matrix for multidimensional vectors
            after we normalize our feature set to get an accurate dissimilarity
            measurement.

            Other Dissimilarity measurements that can be used
                Euclidean
                Cosine Similarity
                Average Distance
#       The K-Means clustering process
                (An iterative process for an iterative algorithm)
            1. Initialize K (Decide the cluster size you want to set for K)
                (Define the centroid of each cluster):

                Centroids should be of same size as our feature set.
                ie. How many clusters of groups the algorithm is going to group data into
                    or how many groups you want it to group data into.
                Centroids are really just central points within certain cluster groups
                that are going to serve as a kind of model of what similar data needs
                to be in order to be grouped in the same cluster as a specific centroid.

                Two approaches to choose a centroid:
                    1. Randomly choose observations out of the dataset
                        then use these observations as the initial means (averages).
                    2. Create random points as centroids of the clusters.

            2. Distance Calculation:
                Calculate the distance of each datapoint from the centroid points.
                Ultimately this process is going to produce a matrix in where
                each point will represent the distance of a data point from
                each centroid aka (Distance Matrix).

            3. Assign each point to the its closest centroid.
            
            K-Means Error is the total distance of each point from its centroid.
            Sum of Squares error.

            4. Compute the new centroids for each cluster. (To improve the error)
               In this step each centroid gets updated to the mean for data points
               in its cluster. Each centroid is going to move according to their
               cluster members.

               To break this down a little:
                    based on all of the points within a cluster the algorithm is going
                    to get an average of them and say ok this is the middle of all
                    of those points in this neighborhood so actually this is
                    a better centroid to use for this specific cluster.
                    This process continues until the centroids stop
                    moving or until the algorithm decides it has found'
                    a solid enough central point on this graph between
                    all these data points that live in this cluster.
                    KEEEP IN MIND:
                    Every time the centroid moves each point in relation
                    to the centroid needs to be measured again.
            5. Repeat the process untill there are no more changes. (Iteratively)
                Steps 2-4 until the algorithm converges.

            Caveat:
                There is no guarantee that the algorithm is going to converge
                to the global optimum and the results may depend on the initial
                clusters. Which means the result of this algorithm
                may not produce the best possible outcome.

            Solution:
                It is common to run the whole process multiple times with
                different starting conditions. This means with randomized
                starting centroids it may produce a better outcome.
                Since this algorithm is usually very fast it should
                not be a problem to run it multiple times.

#       K-Means accuracy and characteristics
            1. Works by randomly placing k centroids, one for each cluster.
               The farther apart the clusters a placed the better.
            2. Calculate the disance of each point from each centroid.
            3. Assign each data point (object) to its closest centroid, creating
               cluster or group.
            4. Recalculate the position of the K centroid.

        How can we evaluate the goodness of the clusters formed by K-means?

            External Approach -
                Compre the clusters with the ground truth if it is available.
                However this is usually not the case since K-Means is an 
                unsupervised algorithm.

            Internal Approach -
                Average distance between data points within a cluster.
                Also average of the distance of data points from their
                cluster centroids can be used as a metric of error
                for the clustering algorithm.
        Determing the value of K in K-Means clustering is a common problem in data clustering.
        
#<-     Choosing K:
            The value of K is ambigous because it is dependent on the shape and scale
            of the distributions of points in a dataset.
            There are some solutions to this problem
            One of them is creating different values for K and then getting an average
            of all of the models ran with different values for K to see which value for
            K fits the best. 
            This metric can be mean, distance between data points and their clusters centroid.
            So basically everytime you run a model with a different value for K
            you then measure the distance between the different clusters centroids
            and the points inside of the cluster. This is going to be the error.
            Ultimately after having done this for different values of K you can
            sort out which value for K had the least amount of error and then
            go with that K value.

            The problem is that with increasing the number of clusters the distance
            of data points to centroids will always reduce.
            This means that increasing the value of K will always decrease the error.
            So, the value of the metric as a function of K is plotted and the elbow point
            is determined where the rate of decrease sharply shifts.
            In other words we repeat this process on a graph untill we see the margin
            of error decrease drastically. We then choose the value of K based on this.
            This method is called the elbow method.

            Drawback is that we need to pre specify the number of clusters
            which is ultimately not an easy task.


#       More on:
#   <-      Clustering Methods : 

##          Density-Based Methods: 
                These methods consider the clusters as the dense 
                region having some similarities and differences from the lower dense 
                region of the space. These methods have good accuracy and the ability 
                to merge two clusters. 
                Example DBSCAN (Density-Based Spatial Clustering of Applications with Noise),
                OPTICS (Ordering Points to Identify Clustering Structure), etc.
##          Hierarchical Based Methods:
                The clusters formed in this method form a 
                tree-type structure based on the hierarchy. New clusters are formed using 
                the previously formed one. It is divided into two category 
                Agglomerative (bottom-up approach)
                Divisive (top-down approach)
                examples CURE (Clustering Using Representatives), 
                BIRCH (Balanced Iterative Reducing Clustering and using Hierarchies), etc.

##          Partitioning Methods:
                These methods partition the objects into k clusters
                and each partition forms one cluster. This method is used to optimize an 
                objective criterion similarity function such as when the distance is a 
                major parameter example K-means,
                CLARANS (Clustering Large Applications based upon Randomized Search), etc.
##          Grid-based Methods:
                In this method, the data space is formulated into a 
                finite number of cells that form a grid-like structure. 
                All the clustering operations done on these grids are fast and independent
                of the number of data objects example
                STING (Statistical Information Grid), wave cluster, CLIQUE (CLustering In Quest), etc.
