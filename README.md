# deep-learning-challenge

Overview of the analysis: Explain the purpose of this analysis.

Results: Using bulleted lists and images to support your answers, address the following questions:

Data Preprocessing

- Data utilized in the exercise was first preprocessed to prepare the data for the model. 
- Target of the model = "IS_SUCCESSFUL" column, which indicates if the application was selected to be funded by Alphabet Soup. 
- Features of the model = included the essential details from each funding application, including: 
  - EIN and NAME—Identification columns
  - APPLICATION_TYPE—Alphabet Soup application type
  - AFFILIATION—Affiliated sector of industry
  - CLASSIFICATION—Government organization classification
  - USE_CASE—Use case for funding
  - ORGANIZATION—Organization type
  - STATUS—Active status
  - INCOME_AMT—Income classification
  - SPECIAL_CONSIDERATIONS—Special considerations for application
  - ASK_AMT—Funding amount requested
- As a last step, the variables of "EIN" and "NAME" were removed from the input data, as they are identifiers that are not useful for modeling purposes (and are not considered "feature" or "target"). 

Compiling, Training, and Evaluating the Model

A deep neural network was selected (utilizing the sequential method) to predict the probability of the application receiving funding. Deep neural networks are specifically designed for binary classification tasks, making them ideal for providing the probability of an applicaiton receiving funding via a large volume of data points pulled from the application.

How many neurons, layers, and activation functions did you select for your neural network model, and why?

Were you able to achieve the target model performance?

What steps did you take in your attempts to increase model performance?


Summary: Summarize the overall results of the deep learning model. Include a recommendation for how a different model could solve this classification problem, and then explain your recommendation.
