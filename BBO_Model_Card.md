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
