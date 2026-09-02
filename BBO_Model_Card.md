# BBO Model Card
## Overview
**Name:** Bayesian Optimization using Model Ensembles  
**Type:** Framework for Sequential Bayesian Optimization  
**Version:** 1.0  
## Intended Use
### Suitable Tasks
- Limited-query Bayesian optimization
- Handling black-box problems
- Expensive experimentation
- Scientific discovery
- Continuous observations
### Unsuitable Tasks
- Unlimited-query Bayesian optimization
- Cheap experimentation
- Discrete observations
- Batch acquisition functions where q>1
## Methodology
- Update most recent week's inputs and outputs in Pandas dataframes
- Update five models for each function:
  - GaussianProcessRegressor using Upper Confidence Bound
  - GaussianProcessRegressor using Expected Improvement
  - Sequential Model-based Algorithm Configuration
  - Bayesian Optimization in PyTorch
  - Differential Evolution
- Compare results from each model
- Select inputs based on criteria specific to that week
## Evolution
I have gradually added models as time has progressed. To maintain diversity of the sampling approach, the first strategy is to give each model at least one week of inputs. If each model has forecasted at least one week of inputs, I will then choose the inputs based on how exploratory or exploitative I want to be in a particular week. Additionally, I have tweaked the models over time to add robustness and optimize hyperparameters.
## Performance
### Model Accuracy
- Kernel length scales
- Model standard deviations
- Model log marginal likelihood values
### Output Accuracy
- Leave-one-out cross-validation
- Expected output
- Actual output relative to expected
### Summary
Over the thirteen weeks, I found new maxima for every function. This was a fun exercise that helped me learn about Bayesian optimization and improved my Python skills.
## Assumptions
The main assumption was that I was able to model these functions with either deterministic models or probabilistic regressions.
## Limitations
If I could not model these functions with either deterministic models or probabilistic regressions. Also, if my forecasts of these models and regressions was wildly off from the true ones given the sparse dataset.
## Ethical Considerations
To the best of my knowledge, all of these numbers are fabricated and are not based on anything in the real world. However, transparency is important so that others don't unknowingly misuse the code and/or concepts.
## How to Run the Code
In the notebooks folder, there are seven Jupyter notebooks. To run the different models, first, run the initial_setup notebook to create dataframes of each function. Feel free to append the new datapoints that I found over the course of the thirteen-week project. The two GaussianProcessRegressor notebooks can then be run on their own - they tune themselves automatically. To switch functions within the notebooks, there are a few modifications that need to be made in the code which are clearly stated in the comments.     
The BoTorch notebook can also be run on its own as it automatically optimizes itself. To switch functions in this notebook, there are only a few required modifications which are clearly stated in the comments.       
The Sequential_Model_based_Algorithm_Configuration and differential_evolution notebooks are slightly more involved. First, run the cross_validation_RBFInterpolator notebook for whichever function you choose in order to find the optimal parameters for the surrogate model, RBFInterpolator, using a grid search. Once you have the optimal parameters, run Sequential_Model_based_Algorithm_Configuration or differential_evolution. To change the function within those notebooks, there are a few modifications required that are clearly marked in the comments. Of note, differential_evolution gives similar results to Sequential_Model_based_Algorithm_Configuration and is much quicker to run.
