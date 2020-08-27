---
layout: page
title: Machine learning
description: 
img: 
importance: 3
---

# Notes Associated with GMRI Quant Group Machine Learning Symposium 07/15/2020
## Background reading
**Olden 2008 - Machine Learning for Ecologists**  
*Why Machine Learning?*
Our ultimate goal is not only to understand ecological processes, but also have the capacity to predict them (Peters 1991). The need for these predictive tools, or forecasts, continues to rise in importance as ecosystems face increasing threats from global climate change (Clark et al. 2001). To reach this goal and build our predictive capacity, we need to contend with many challenges arising from the inherent complexity of ecological processes, which integrate historical conditions, time lages, interactions, and feedback loops varying over both space and time (Levin 1998).

Ecoinformatics, and to a greater degree machine learning areas within ecoinformatics, provide promising opportunities to help ecologists reach our goal as these tools are specifically developed to make predictions from complex and non-linear data.

*Types of machine learning algorithms*
- Supervised: Known inputs and outputs, with all data having a label. This includes methods like artificial neural networks, cellular automata, classification and regression, fuzzy logic, genetic algorithms and progreamming, maximum entropy, support vector machines, and wavelet analysis. 
- Unsupervised: All data, no labels or specific classifcation of input and output or feature and label or response and predictor. This includes things like Hopfield neural networks and self-organizing maps.

*Worked examples*
To illustrate the utility of machine learning algorithms to answer ecological questions, going to use an example of relating fish species richness to environmental characteristics across 8000+ lakes. 
- Classification and Regression Trees (CART)
These models excel when dealing with large ecological datasets with nonlinear and interacting relationships (De'ath and Fabricus 2000). It works using three steps: 
1. Tree building. The algorithm builds a decision tree by repeatedly splitting the data into mutually exclusive groups, maximizing within group similarity. 
2. Stopping the build. The algortithm stops splitting when it reaches some level of observations per child node (set by the user), when all observations within a child node can't be split by an independent variable, or the number of tree split threshold has been reached. 
3. Tree pruning or optimal tree selection. Algorithm then tries to reduce the tree complexity, removing child nodes that do not substantially increase the model error. This essentially becomes a trade off between overfitting and model prediction error.  
Bagging, random forests and boosting techniques are similar, but with slight differences to account for some of the limitations associated with CART. For example, with bagging, we would take many different splits of the data, build CART and then average them to get our dinal results. Random forests are a specific case of bagigng when the number of potential predictors at each split is equal to the number of variables. When it is less, however, random forests can provide even more of a benefit, where at each split variables are selected randomly for possible inclusion, and each tree is independent. In contrast, with CART or bagging, the most important variables are always going to be selected first most likely. In turn, averaging them doesn't really reduce the amount of variance. Boosting is somewhat similar to bagging, except instead of building the model on boostrapped samples of the data, boosting works sequentially on the residuals of the previous model fit. [Here's a good description of differences between random forests and boosted regression trees](https://www.datasciencecentral.com/profiles/blogs/decision-tree-vs-random-forest-vs-boosted-trees-explained).

- Artificial Neural Networks
ANN's are also referred to as multilayer perception models stemming from the way that biological nervous systems handle complex data. ANN's can be supervised or unsupervised. In this example, focusing on a one hidden-layer, supervised, feedforward, back-propagation algorthm.  
The structure of an ANN starts with the neurons. In a feedforward ANN, these neurons are organized in an input layer, a hidden layer, and an output layer. Connections between these differnt layers are referred to as axons. Importantly, neurons WITHIN each layer and in non-adjacent layers are not connected. 
- A few key components of the ANN:
1. The number of neurons in the hidden layer. This becomes a bias - variance trade off, where increasing number of neurons increases fit to the data and reduces the bias, but also decreases predictive skill and increases the prediction variance. 
2. "Variable" or "connection" importance can be derived by looking at the activity level of a given neuron or the connection weight of each axon. 
3. To establish these connection weights, algorithms try to reduce the output signal error (back-propagation algorithms). At each iteration, connection weights modified, then data entered, adjustment of input hidden and output hidden connection weights. Algorithm proceeds until it hits some stopping rule based on an acheived error rate. 
ANN's have a number of advantages (nonlinear interactions, no assumptions about distributional characteristics of response or predictor variables). Among the key limitations are that they can be sensitive to inital weight assignments (want to run multiple) and they can be a bit harder to interpret. 

- Evolutionary computation: genetic algorithms and programming  
These are generally classified as "stochastic optimization tools". Included within this group are models like simulated annealing, evolutionary programming, evolutionary strategies, genetic algorithms and genetic programming, with all of them essentially inspired by the processes of evolution related to sexual reproduction. 

Genetic algorithms and programming have been most commonly used in ecology. Both of them work on populations of competing solutions, which are allowed to evolve through time and converge on a solution. These solutions (i.e., chromosomes) are composed of specific characteristics (i.e., genes). They involve four main steps:
1. Random solutions (chromosomes) are developed.
2. Potential solutions are mated together using reproduction, mutation and crossover.
3. New solutions are evaluated.
4. Most fit solutions are selected, and then steps 2 through 4 are repeated. 
These approaches have some advantages, common to the others seen before (nonlinear data, interactions, etc). They also have limitations (suffer from over predictions, GAs limit range of solutions, GP solutions are basically uninterpretable).

**Beyan and Browman - Machine Learning for Ecologists**  
Machine learning is a subset of artificial intelligence, using dynamic models to create data-driven solutions. Machine learning provides many potential advantages, including dealing with high-dimensional, nonlinear, complex big datasets, handling missing data, and small-sample size problems.

Deep learning is a subset of machine learning, itself a subset of artificial intelligence. It stems from the idea of ANNs, but basically amounts to a large and deep (many hidden layers), neural network. Among the popular methods are recurrent neural networks and convolutional neural networks.

**Jennifer Hoeting's talk: Deep learning opening the black box**
Deep learning is a small part of machine learning, itself a part of artificial intelligence:
    AI: Techniques that enable machines to mimic human behavior
    ML: Subset of AI that uses statistical methods to enable machines to improve with experience (i.e., learn)
    DL: Subset of ML that makes it possible to compute multi-layer (i.e., deep) and large neural networks possible

Difference between statistics and machine learning? 
    Stats = inference (and uncertainty?)
    Machine learning = prediction (without uncertainty?)

Types of ML:
- Supervised: Labeled response and predictors. Possible with caret package and tidymodels in R. Examples include linear classifiers, support vector machines, tree-based methods, neural networks and deep learning
- Unsupervised: No labels. 

More on deep learning:
- Allows for computers to learn from experience with an aim towards producing models with the best predictions
- Representations are learned and not assumed
- Uses a hierarchy of layers, allowing the algorithm to learn abstract concepts that we may not be able to represent or understand. This produces a "deep" graph with MULTIPLE hidden layers. 
- Has many advantages (excels at predictions, nonlinear, hierarchcical, interactions, complex large data, no assumptions) and a few limitations (not good for inferences, easy to overfit, no uncertainty estimates)

Neural networks: three views
1. Black box. Put something in, it goes through the network, and you get something out.
2. Deep learning view. Deep learning model is essentially a neural network on steroids, with multiple hidden layers. 
3. As a non-linear model. Fit nonlinear model to response and predictors, where the predictors are themselves transformed variables derived using multivariate techniques like PCA.

Neural Networks as Regression models: a progression.
1. Linear regression. This is where we will start. Fit a model $y = /beta_0 + /beta_1x + /epsilon$, where $epsilon$ is normally distributed with mean 0 and SD $sigma^2$.
2. Nonparametric regression. Given non-linear relationships, we might instead use something like regression splines (constructed from piece wise polynomial functions). In doing so, we adopt a non-parametric model as we do not make any distributional assumptions about the error term of the model. 
3. Neural network. Now, instead of just using the predictors, we are going to use some transformation of these predictors, which is a "hidden layer" with some number of nodes. 
4. Deep learning model. Building from the neural network, we expand the number of hidden layers, such that each predictor is not just a transformation, but a neural network model itself. 

Deep learning model fitting steps:
1. Define network structure: deep feedforward networks, convolutional netowrks, recurrent and recursive nets, Bayesian networks. Another keep component to the structure is the activation function. This function basically takes in output signal from previous node and packages it up for input into the next one. Helps with computational issues (values need to be realistic) and for introducing nonlinearity.
2. Select the loss function: measures predictive performance, we want to find the parameters that minimize this one value. Common examples include MSE, cross-entropy
3. Select the optimizer: Need a way to efficiently find the best parameters. Stochastic gradient descent is commonly used where:
    a. Set starting values for weights are assigned
    b. Calculate partial derivitabe of loss function with respect to each weight.
    c. Take a step in downhill direction (opposite the gradient)
    d. Repeat.

[For more on deep learning in ecology, check this paper out, too.](https://besjournals.onlinelibrary.wiley.com/doi/abs/10.1111/2041-210X.13256)