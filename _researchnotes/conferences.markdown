---
layout: page
title: Conferences and presentations
description: 
img: 
importance: 3
---

# ISEC 2020 #

**Florian Hartig: Scalability and accuracy of joint species distribution models**

*Background*
Macro-scale species distribution models and ordination metacommunity models both ignore biotic interactions. 

Joint species distribution models hopefully help fill this gap.

For example:
    P/A ~ Env       + Your basic SDM
    
    P/A(1) ~ Env    + Stacked SDM if we fit models to each species
    P/A(2) ~ Env        - Multi-species if estimates for slope are 
    P/A(3) ~ Env          connected through random effects

    P/A(1) ~ Env X  + Joint SDM if we also include covariance between 
    P/A(2) ~ Env XX   species, under the assumption that some species   
                      will be more/less often found together than expected by the environment along BECAUSE of their interactions. 

    P/A(1) ~ Env X + SPACE

*What does the species covariance actually mean?*
Species associations AFTER accounting for environment and space
Tempting to attribute assocations to biotic interactions, but this isn't necessarily true. So, the question becomes what can we do with these associations and what can we learn from them?

*What can we do with the species covariance matrices?*

Example
    Link(binomial) ~ Env + Species covariance matrix + Space
    Link(binomial) ~ Env + MVN $$ (Sigma) $$ + Space

There is interesting information in A, so we would be foolish not to try to estimate A and think about what we can do with it. 

We have two problems:
1. Computationally costly -- break down with 10/20 species
2. Number of parameters scale quadratically -- need to be concerned with overfitting/regularization

Solutions?
1. Approximate with variational Bayes or Laplace approximation and using latent variables
    - See 24B1 and https://theoreticalecology.github.io/s-jsdms

2. If we don't need to worry about speed, what structure should we use to minimize estimation error? This is particularly important given that many times with these community data sets we are dealing with very WIDE data sets (e.g., 100 sites, 100 species).
    1. Re-parameterize the covariance matrix using a low-rank approximation using the latent-variable approach (Warton et al. 2015)
    2. Penalize the complexity of the covariance matrix directly 

Propose a new high-rank shrinkage regularization procedure

See preprint on arxiv.org at abs/2003.05331

**Janine Illian - INLA and INLAbru**

*Background*
INLA  stands for integrated nested Laplace approximation and is a spatial differential equations approach (SPDE). It assumes that spatial data have been collected throughout the area of interst and that the predictors are linear. 

INLAbru extends INLA by relaxing this collection assumption, and interprets the data as thinned point patterns by fitting an observation process AND process of interest. It also allows for non-linear predictors (e.g., non-linear detection functions, non-linear relationships).




