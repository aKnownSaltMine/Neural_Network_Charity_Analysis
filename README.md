# Neural_Network_Charity_Analysis
## Overview 
Alphabet Soup is a non-profit foundations that focuses on funding organizations that fit into their non-profit outlook. Over the course of their existence, they have accepted billions of dollars in donations and allocated these to different corporations in order for them to achieve their goals. The goal of this project is to take the prior data of funded projects and whether or not they were successful as well as other parameters, in order to train a neural network using the `TensorFlow` library and the `Keras` module that would be able to predict whether or not an applicant would be successful so as to better allocate future funds. 

## Results
### Preprocessing
The original [dataset](https://github.com/aKnownSaltMine/Neural_Network_Charity_Analysis/blob/main/Resources/charity_data.csv) given for processing contained the following sections for each applicant: 
* EIN
* Name
* Application_Type
* Affiliation
* Classification
* Use_Case
* Organization
* Status
* Income_Amt
* Special_Considerations
* Ask_Amt
* Is_Successful

Within the original dataset, the target data was held in the `IS_SUCCESSFUL` column. The `EIN` and `NAME` column are both extraneous and were dropped, the other columns in the dataset are considered features in the model.

### Compiling, Training, and Evaluating the Model
For the original model, I set the model up with 2 hidden layers, and 80 neurons for the first layer and 30 for the second. I chose these numbers because in the first layer it is roughly about 2 times the total features that we would be feeding the model, the second layer is a step down to the output. In later optimizations I added a third layer that had 15 neurons with a modest increase in accuracy.

**Model Accuracy Scores**
| Attempt   | Score  |
| :-------- | :----- |
| Original  | 0.7259 |
| Attempt 1 | 0.7273 |
| Attempt 2 | 0.7284 |
| Attempt 3 | 0.7278 |

With the original attempt it was a fairly simple model with 100 epochs. The first attempt at optimization increased the epochs from 100 to 300. The second attempt at optimization changed the activation models in the hidden layers from ReLU to Tanh. Because there was a positive performance increase for with both of these changes, they were retained moving into the third attempt which added an additional hidden layer, which saw a decrease in accuracy. 

## Summary
Overall, each attempt hovered just under 73% and was ultimately unsuccessful in increasing performance to the 75% goal. 
**Model Accuracy Scores**
| Attempt   | Score  |
| :-------- | :----- |
| Original  | 0.7259 |
| Attempt 1 | 0.7273 |
| Attempt 2 | 0.7284 |
| Attempt 3 | 0.7278 |

For future models in order to improve the accuracy score, I would recommend utilizing [KerasTuner](https://keras.io/keras_tuner/) in order to create an algorithm that will tune the parameters throughout the epochs. But also I would recommend binning the `ASK_AMT` column so as to not have a feature that is so varied.