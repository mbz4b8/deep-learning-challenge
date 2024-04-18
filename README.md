# deep-learning-challenge

Overview of the analysis: Explain the purpose of this analysis.

Results: Using bulleted lists and images to support your answers, address the following questions:

Data Preprocessing

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

Compiling, Training, and Evaluating the Model

A deep neural network was selected (utilizing the sequential method) to predict the probability of the application receiving funding. Deep neural networks are specifically designed for binary classification tasks, making them ideal for providing the probability of an applicaiton receiving funding via a large volume of data points pulled from the application.

How many neurons, layers, and activation functions did you select for your neural network model, and why?
The first round of the model design included the use of the below neurons, layers and activation functions to test the accuracy of the intial set up. 
- Round 1 of Model Design:
  - Hidden Layer 1 / 80 neurons / "relu" activation
  - Hiddent Layer 2 / 30 neurons / "relu" activation
  - Output Layer / 1 neuron / "sigmoid" activation
- Round 1 Model Result:  215/215 - 0s - loss: 0.5756 - accuracy: 0.7268 - 402ms/epoch - 2ms/step
Loss: 0.5756490230560303, Accuracy: 0.7268221378326416

What steps did you take in your attempts to increase model performance?
Various steps were taken to attempt to improve the model to a minimum of 75% accuracy. 

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
- Result:


Summary: Summarize the overall results of the deep learning model. Include a recommendation for how a different model could solve this classification problem, and then explain your recommendation.
