# deep-learning-challenge

# Project Background
- Alphabet Soup Charity offers financial support to eligible applicants aiming to launch a successful new venture.
- To streamline the application review process, the Charity seeks to develop a method to preliminarily assess applications and gauge their potential for success.
- With a database comprising data from 34,000+ successful organizations previously funded by Alphabet Soup Charity, we aim to construct a predictive model to evaluate and categorize incoming applications based on their probability of success.

# Data Preprocessing

- Data utilized in the exercise was first preprocessed to prepare the data for the model. 
- Target of the model = "IS_SUCCESSFUL" column, which indicates if the application was selected to be funded by Alphabet Soup. 
- Features of the model = included the essential details from each funding application, including: 
  - APPLICATION_TYPE—Alphabet Soup application type
  - AFFILIATION—Affiliated sector of industry
  - CLASSIFICATION—Government organization classification
  - USE_CASE—Use case for funding
  - ORGANIZATION—Organization type
  - STATUS—Active status
  - INCOME_AMT—Income classification
  - SPECIAL_CONSIDERATIONS—Special considerations for application
  - ASK_AMT—Funding amount requested
  - Data not included as a "Feature" in model:  "EIN" and "NAME" were removed from the input data, as they are identifiers that are not useful for modeling purposes (and are not considered "feature" or "target").
- Before training the model, an attempt was made to simplify the data by reducing the number of specific Application Types and Classifications as too many different factors may overtrain the model and reduce accuracy.
  - Application Types were simplified by only included Application Types that received 950 or more applications. This resulted in 6 different Application Types for the model (down from 17 different types in the raw data). 
  - Classifications were simplified by only including Classifications taht received 1,880 or more applications. This resulted in 6 different Classifcation types for the model (down from the 71 different types in the raw data).

# Compiling, Training, and Evaluating the Model

A deep neural network utilizing the sequential method was selected to predict the probability of the application receiving funding. Deep neural networks are specifically designed for binary classification tasks, making them ideal for providing the probability of success for the new applicant. 

The goal of the Charity was to apply a model that had a minimum of 75% accuracy in predicting the success of applicants. The first iteration of the model acheived an accurate of 72.7% with 56.8% loss, so an additional three model designs were explored to optimize the outcome and achieve the goal of 75% accuracy. Below is a summary of each model design and its outcome. 

## Original Model Design & Results
- Data was analyzed via 6x unique application types and 6x unique classifications
- Layer 1: relu activation / 80 neurons
- Layer 2: relu activation / 30 neurons
- Output Layer: sigmoid activation / 1 neuron

<img src="https://github.com/mbz4b8/deep-learning-challenge/blob/main/Model_Results/AlpahbetSoupCharity_Original_Accuracy.png" alt="Original Model Results" style="float:left; margin-right:10px;" />

## Optimized Model #1 Design & Results   
- Data was analyzed via 6x unique application types and 6x unique classifications
- Layer 1: relu activation / 90 neurons
- Layer 2: relu activation / 40 neurons
- Output Layer: sigmoid activation / 1 neuron

<img src="https://github.com/mbz4b8/deep-learning-challenge/blob/main/Model_Results/AlpahbetSoupCharity_o1_Accuracy.png" alt="Opt Model 1 Results" style="float:left; margin-right:10px;" />

## Optimized Model #2 Design & Results   
- Data was analyzed via 11x unique application types and 30x unique classifications
- Layer 1: relu activation / 90 neurons
- Layer 2: relu activation / 40 neurons
- Output Layer: sigmoid activation / 1 neuron

<img src="https://github.com/mbz4b8/deep-learning-challenge/blob/main/Model_Results/AlpahbetSoupCharity_o2_Accuracy.png" alt="Opt Model 2 Results" style="float:left; margin-right:10px;" /> 

## Optimized Model #3 Design & Results   
- Data was analyzed via 11x unique application types and 30x unique classifications
- Layer 1: LeakyReLU activation / 90 neurons
- Layer 2: PReLU activation / 40 neurons
- Output Layer: sigmoid activation / 1 neuron

<img src="https://github.com/mbz4b8/deep-learning-challenge/blob/main/Model_Results/AlpahbetSoupCharity_o3_Accuracy.png" alt="Opt Model 3 Results" style="float:left; margin-right:10px;" /> 


# Summary: Summarize the overall results of the deep learning model. Include a recommendation for how a different model could solve this classification problem, and then explain your recommendation.
