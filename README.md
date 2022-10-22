# Neural_Network_Charity_Analysis

## Overview

The client, Alphabet Soup, is a philanthropic organization that provides funding to non-profits that are geared towards environmentalism.  The client is requesting a binary classifier capable of predicting whether applicants will be successful if they are funded by Alphabet Soup.

## Results

* Data Preprocessing
	* Target variable for model: 

As the client is asking for data modeling on charities receiving donations that are considered successful, the target variable chosen was 'IS_SUCCESSFUL', which is a boolean value indicating if the money was used effectively or not.

	* What variable(s) are considered to be the features for your model?

Though there are a high number of application types ('APPLICATION_TYPE'), for 43,000+ lines of data, that's a relatively low number of categories to use as a feature for the model.  Likewise, the classification field ('CLASSIFICATION') shows that the vast majority of rows fall into one of 5 classifications and the rest are of much lesser consequence and can be bundled together for simplification that won't confuse the model.  I believe both the amount of funds requested by the non-profit ('ASK_AMT') and if special consideration ('SPECIAL_CONSIDERATIONS') was taken to approve the application are worth being listed as important features for the model.

	* Variables that are neither targets nor features, and should be removed from the input data:

'EIN' and 'NAME' are identification columns and as such don't provide any data that would influence the training model.  There are no duplicate EIN and therefore Names listed in the dataset, so there is no trend to trace.  In the third optimization attempt, the other string columns 'AFFILIATION','USE_CASE', and 'ORGANIZATION' were also removed, but as the loss and accuracy scores were one of the lowest of the various evaluations, it appears that one or more of these should be tested further as a valuable feature for the model.

* Compiling, Training, and Evaluating the Model
	* How many neurons, layers, and activation functions did you select for your neural network model, and why?

The first model was provided as a template with two hidden layers (with 80 and 30 neurons respectively), using the relu activation.  Subsequent optimization models reflected a deviation, but not in all ways in the same optimization in order to attempt to pinpoint how the model could be best optimized to bring the accuracy level up to at least 75%.  The details of the three optimized models will be covered in more detail further below.

	* Were you able to achieve the target model performance?

Unfortunately, all attempts were unsuccessful.  The results were as follows:

First Model:


First Optimization Attempt:


Second  Optimization Attempt:


Third  Optimization Attempt:


	* What steps did you take to try and increase model performance?

		* First Optimization Attempt: This model added an additional hidden layer with a higher number of neurons.  The activation type remained the same, no data columns were removed, and since the first model showed no significant improvement through the 100 epochs, I lowered the training model down to 60 to provide enough training without too much redundancy.


		* Second  Optimization Attempt: This model used different activation functions. As relu returns a value from 0 to infinity, the dataset may be too simple for this to be useful.  I used sigmoid for the three hidden layers in case in case the data wasn't as linear as expected and possibly create a better understanding and accuracy.


		* Third  Optimization Attempt: In this instance I dropped three additional columns and left the rest of the model untouched from the first in order to determine if they were truly beneficial or not.

## Summary

As seen by the results, adding layers and neurons didn't change the loss and accuracy, but by not using the relu activation and dropping columns led to a significant loss.  Further testing is needed to isolate which three columns or up to all three are a significant feature to improve the data model.  The relu activation was determined to be the most useful (both tanh and Leaky ReLu are more beneficial for datasets with negative values, which are absent in this case).  If the client requires the classifier to be at least 75% accurate before deployment, this model isn't sufficient for use at this time.  However, I think these four models can be used to help further narrow down what determining factors are required to better predict which applicants are worth investing with.
