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

## Original Model Design
- Data was analyzed via 6x unique application types and 6x unique classifications
- Layer 1:  relu activation / 80 neurons
- Layer 2: relu activation / 30 neurons
- Output Layer: sigmoid activation / 1 neuron
  


The original model design resulted in 72.7% accuracy with 56.6% loss. The Charit The first round of the model design included the use of the below neurons, layers and activation functions to test the accuracy of the intial set up. 
- Round 1 of Model Design:
  - Hidden Layer 1 / 80 neurons / "relu" activation
  - Hiddent Layer 2 / 30 neurons / "relu" activation
  - Output Layer / 1 neuron / "sigmoid" activation
- Round 1 Model Result:  215/215 - 0s - loss: 0.5756 - accuracy: 0.7268 - 402ms/epoch - 2ms/step
Loss: 0.5756490230560303, Accuracy: 0.7268221378326416

# Various steps were taken to attempt to improve the model to a minimum of 75% accuracy. 

- Round 2 of Model Design:
    - Hidden Layer 1 / 90 neurons / "relu" activation
  - Hiddent Layer 2 / 40 neurons / "relu" activation
  - Output Layer / 1 neuron / "sigmoid" activation
- Round 1 Model Result:  215/215 - 0s - loss: 0.5691 - accuracy: 0.7245 - 463ms/epoch - 2ms/step
Loss: 0.5691210031509399, Accuracy: 0.7244898080825806
- Round 2 Implications: increasing the number of Neurons did not result in an improvement in accuracy, instead it declined. Next step will test adjusting the binning strategy of the "Classification" data in order to increase diversity fo results for model to consider.

- Round 3 of Model Design:
- Increased number of Application types to 11 (up from 6, but still less than total 17 unique types in raw data).
- Increased number of Classification types to 30 (up from 6, but still less than total 71 unique types in raw data).
- Result: 215/215 - 0s - loss: 0.5737 - accuracy: 0.7280 - 390ms/epoch - 2ms/step
Loss: 0.573708176612854, Accuracy: 0.7279883623123169
- Round 3 Implications: increasing Application Types and Classification diversity slightly improved the accurance, but still did not reach 75% minimum threshold. 


# Summary: Summarize the overall results of the deep learning model. Include a recommendation for how a different model could solve this classification problem, and then explain your recommendation.
