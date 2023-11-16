# Module 21 Report

## Overview
The purpose of this analysis is to create a deep neural network model capable of classifying the success of a charity. Additionally, this analysis helps hone and display knowledge and ability using TensorFlow to create such networks.

## Results


### Data Processing
Our target variable in this case is "IS_SUCCESFUL", a simple true/false variable on whether a given charity, requesting funds, succeeds in acquiring these funds from an unspecified source, or fails.

The following variables are used in computing the model:
"APPLICATION_TYPE" is a categorical variable, detailing the ultimate ends of the Charity.
"AFFILIATION" is a categorical variable detailing the affiliation with any larger entities than the charity itself, such as sponsors, owners or others.
"CLASSIFICATION" details the type of charity the charity is.
"USE_CASE" is a categorical variable detailing the objective of the charity, such as preservation, product development, etc.
"ORGANIZATION" is a categorical variable listing the overall setup of the entity.
"STATUS" displays if a charity is still currently operational.
"INCOME_AMT" is a categorical bin variable detailing the bracket of funding a charity receives.
"SPECIAL_CONSIDERATIONS" is a categorical variable detailing if a given charity has received special consideration, however it is unclear what this represents.
"ASK_AMT" is the requested funds as an integer.

Two variables are irrelevant for our analysis:
"EIN" is the ID for a given row and can be safely dropped as it has no effect on our analyses.
"NAME" similarly has no effect, being the name of the charity being reviwed.


### Data Processing
#### Configuration - Manual
For our manually designed neural network, Layer one with 5 neurons, relu activation and 43 inputs was selected to be able to take all of our inputs in, with neurons and activation arbitrarily selected from prior code.

The second layer with 2 neurons, relu activation and 43 input_dimensions is simply a duplicate of layer 1, with fewer neurons.

The output layer of one unit with sigmoid activation is a simple output, likewise taken from earlier code.

#### Performance - Manual
Surprisingly, both models performed comparatively similarly - The Manual input gave a 69.8% accuracy. I believe with a more varied number of neurons and perhaps a cleaner input, this may be solved.

#### Configuration - Optimised
For our optimized variant, Keras_tuner was utilised to automatically improve upon a model, taking the best possible options. An initial layer of 1-10 neurons on the first, followed by 1-45 on the 2nd-7th layers, and a simple single neuron sigmoid output layer was utilised.

Activation functions on both layers were likewise left to keras_tuner.

Ultimately, the final configuration featured these properties:
'activation': 'tanh',
'first_units': 9,
'num_layers': 4,
'units_0': 41,
'units_1': 29,
'units_2': 41,
'units_3': 17,
'units_4': 7,
'units_5': 21,
'tuner/epochs': 7,
'tuner/initial_epoch': 0,
'tuner/bracket': 1,
'tuner/round': 0

#### Performance - Optimised
Despite spending five minutes calculating 50 trials with 20 epochs, keras_tuner did not prove a substantial upgrade, managing an accuracy of 73.2% for a marginal improvement of 3.4 percentage points.

I believe that, with so many varied inputs, this is as close as this model may get. A cleaner input may be necessary to further improve.

## Summary
This model clearly shows the limitations of TensorFlow on the small-scale - With few layers, few neurons and over forty inputs, the neural network, while it managed respectable results, struggled to provide supreme accuracy and low information loss.

I believe that further alteration of the input is necessary for more concise results, as I fear overfitting the data with many additional layers is not a valid path to solving accuracy issues, and would not apply beyond the test set.
