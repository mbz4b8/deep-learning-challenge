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
- Layer 1: relu activation / 90 neurons (increased from 80 to optimize accuracy)
- Layer 2: relu activation / 40 neurons (increased from 30 to optimize for accuracy)
- Output Layer: sigmoid activation / 1 neuron

<img src="https://github.com/mbz4b8/deep-learning-challenge/blob/main/Model_Results/AlpahbetSoupCharity_o1_Accuracy.png" alt="Opt Model 1 Results" style="float:left; margin-right:10px;" />

## Optimized Model #2 Design & Results   
- Optimized Model #1 imrpoved slightly versus Original Model (72.73% accuracy versus 72.67%), but did not reach goal of 75% accuracy.
- Optimized Model #2 revised the categorizations of the Application Types (11x unique types, up from 6x) and Classifications (30x unique types, up from 6x) in order to determine if more diverse data would improve model accuracy. 
- Layer 1: relu activation / 90 neurons
- Layer 2: relu activation / 40 neurons
- Output Layer: sigmoid activation / 1 neuron

<img src="https://github.com/mbz4b8/deep-learning-challenge/blob/main/Model_Results/AlpahbetSoupCharity_o2_Accuracy.png" alt="Opt Model 2 Results" style="float:left; margin-right:10px;" /> 

## Optimized Model #3 Design & Results   
- Optimized MOdel #2 did not outperform Optimized Model #1 (resulted in 72.63$ versus 72.73%).
- Optimized Model #3 utilized the same data features as Optimized Model #2, but instead new activation methods were applied to determine if accuracy could be improved. 
- Layer 1: LeakyReLU activation / 90 neurons
- Layer 2: PReLU activation / 40 neurons
- Output Layer: sigmoid activation / 1 neuron

<img src="https://github.com/mbz4b8/deep-learning-challenge/blob/main/Model_Results/AlpahbetSoupCharity_o3_Accuracy.png" alt="Opt Model 3 Results" style="float:left; margin-right:10px;" /> 


# Conclusion: 
- Optimized Model #1 was developed and could be applied to Alphabet Soup Charity's application process to predict the success rate of each new venture, but it only acheived a 72.73% success rate. Additional review of each application predicted to be "not successful" should recevie a second review in order to ensure a venture is less likely to be successful.
- We'd recommend additonal optimizations be applied to the Model design in order to acheive the desired 75% accuracy rate, which is an industry standard threshold for predictive models. This exploration applied small tweaks to the model that did not result in major improvements. Additional optimization methods should be explored, particulary hyparameter methods that automoate the process by programmatically selecting the right paramaeters to apply to maximize success rates.
- If optimizatons do not result in desired accuracy, the team could consider exploring a Logistic Regression Model Analysis, which is a more simplified appraoch to a binary classification problem. The predication process may not require the complexity of neural network in order to acheive a higher accuracy rate, as the model may be overfitting itself via the complex algorithms and computing power. 
