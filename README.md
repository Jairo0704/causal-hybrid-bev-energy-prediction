# A Causal Hybrid Framework for Microscopic BEV Energy Consumption Prediction under Real Driving Conditions

This repository contains the source code associated with the research article:

**"A Causal Hybrid Framework for Microscopic BEV Energy Consumption
Prediction under Real Driving Conditions"**

The proposed framework integrates physics-based causal modeling with
data-driven machine learning to predict microscopic battery energy
consumption using real-world BEV driving data.

## Machine Learning Models

Five machine learning models are implemented:

- Multiple Linear Regression (MLR)
- Support Vector Regression (SVR)
- Random Forest (RF)
- Multilayer Perceptron (MLP)
- Extreme Gradient Boosting (XGBoost)

## Input Variables

The predictive framework integrates three categories of variables:

### Causal physical variables
- Wheel-level rolling-resistance energy
- Wheel-level aerodynamic-drag energy
- Wheel-level road-grade energy
- Wheel-level inertial energy

### BEV operational variables
- Electric motor torque

### System state variables
- Battery state of charge
- Battery temperature
- Motor temperature

## Model Validation

The dataset is partitioned at the trip level into training, validation,
and test subsets to reduce temporal information leakage between
observations belonging to the same driving trip.

## Data Availability

The real-world BEV driving dataset used in this study is publicly
available on Zenodo:

[Zenodo DOI – to be added]

## Repository Structure

The source code required to reproduce the machine-learning experiments
reported in the article is provided in this repository.

## Citation

Citation information will be added upon publication of the associated
article.

## License

License information will be added before the final release.
