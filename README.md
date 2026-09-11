# A Causal Hybrid Framework for Microscopic BEV Energy Consumption Prediction under Real Driving Conditions

This repository contains the source code associated with the research article:

**"A Causal Hybrid Framework for Microscopic BEV Energy Consumption Prediction under Real Driving Conditions"**

The proposed framework integrates physics-based causal modeling with data-driven machine learning to predict microscopic battery energy consumption using real-world battery electric vehicle (BEV) driving data.

## Machine Learning Models

Five machine learning models are implemented and evaluated:

- Multiple Linear Regression (MLR)
- Support Vector Regression (SVR)
- Multilayer Perceptron (MLP)
- Extreme Gradient Boosting (XGBoost)
- Random Forest (RF)

Model selection is based exclusively on validation-set performance. The independent test set is used afterward to assess generalization performance.

## Final Predictor Set

The final machine-learning predictor set contains eight variables organized into three categories.

### Causal physical variables

Four wheel-level energy components derived from longitudinal vehicle dynamics:

- Aerodynamic-drag wheel energy (`Ew_drag`)
- Rolling-resistance wheel energy (`Ew_roll`)
- Road-grade wheel energy (`Ew_grade`)
- Inertial wheel energy (`Ew_inertia`)

### BEV operational variable

- Electric motor torque (`MotorTorque`)

### System state variables

- Battery state of charge (`SoC`)
- Maximum battery temperature (`BattTemp_max`)
- Motor temperature (`MotorTemp`)

### Target variable

- Microscopic net battery energy (`E_batt_net`)

## Trip-Wise Data Partition

To reduce temporal information leakage between observations belonging to the same driving trip, complete trips are maintained as independent units when constructing the training, validation, and test subsets.

The partition used in the study is:

- **Training:** trips 2, 3, 4, 5, 7, 8, 11, 13, and 15
- **Validation:** trips 1, 6, and 14
- **Test:** trips 9, 10, and 12

The corresponding number of observations is:

- **Training:** 26,624 observations
- **Validation:** 8,948 observations
- **Test:** 9,144 observations
- **Total:** 44,716 observations

This trip-wise partition is explicitly defined in the public notebook to ensure consistency with the experimental design reported in the manuscript.

## Repository Structure

```text
causal-hybrid-bev-energy-prediction/
├── README.md
├── LICENSE
├── CITATION.cff
├── requirements.txt
├── .gitignore
├── GITHUB_UPLOAD_CHECKLIST.md
├── FINAL_CODE_AUDIT.md
│
├── data/
│   ├── README.md
│   └── data_schema.csv
│
├── notebooks/
│   ├── 01_modeling_pipeline.ipynb
│   └── 02_correlation_vif.ipynb
│
├── src/
│   └── dem/
│       └── Algoritmo_Altitude.m
│
├── reference_results/
│   ├── model_performance_reference.csv
│   ├── svr_epsilon_reference.csv
│   └── final_vif_reference.csv
│
└── outputs/
    └── README.md
```

## Code Description

### Machine-learning workflow

The main computational workflow is provided in:

```text
notebooks/01_modeling_pipeline.ipynb
```

This notebook includes:

- loading and normalization of the model-ready dataset;
- definition of the final predictor set;
- trip-wise training, validation, and test partition;
- feature scaling based on the training set;
- SVR epsilon sensitivity analysis;
- training and evaluation of the five machine-learning models;
- validation-based model selection;
- independent test-set evaluation;
- test performance analysis by trip; and
- predictor-importance analysis.

### Correlation and multicollinearity analysis

The statistical analysis supporting predictor selection is provided in:

```text
notebooks/02_correlation_vif.ipynb
```

This notebook includes:

- Pearson correlation analysis;
- correlation-matrix generation;
- variance inflation factor (VIF) analysis for the initial candidate variables; and
- post-selection VIF analysis for the final eight-predictor set.

### DEM-based elevation and road-grade processing

The DEM-based elevation reconstruction and road-grade processing algorithm is provided in:

```text
src/dem/Algoritmo_Altitude.m
```

This code supports the topographic preprocessing methodology described in the associated manuscript.

## Expected Local Dataset

The experimental dataset is not included in this repository.

Authorized users wishing to reproduce the analyses should place the model-ready dataset locally at:

```text
data/BEV_model_ready_dataset.xlsx
```

The expected variable structure is documented in:

```text
data/data_schema.csv
```

The repository `.gitignore` is configured to prevent experimental and derived row-level datasets from being committed to the repository.

## Installation

The Python dependencies required to run the analysis are listed in:

```text
requirements.txt
```

They can be installed using:

```bash
pip install -r requirements.txt
```

The machine-learning and statistical analyses were implemented in Python. The DEM-based elevation and road-grade processing algorithm is provided separately in MATLAB.

## Running the Analysis

After installing the required dependencies and placing an authorized copy of the model-ready dataset in the local `data/` directory, run the notebooks in the following order:

1. `notebooks/01_modeling_pipeline.ipynb`
2. `notebooks/02_correlation_vif.ipynb`

Generated figures and summary tables are written locally to:

```text
outputs/
```

Generated outputs are excluded from version control to reduce the risk of unintentionally publishing experimental or derived row-level information.

## Reference Results

Aggregate reference results reported in the manuscript are provided in:

```text
reference_results/
```

These include:

- machine-learning model performance;
- SVR epsilon sensitivity results; and
- final VIF values.

These files contain only aggregate results and do not include row-level experimental data.

## Reproducibility Scope

This repository provides the source code and methodological workflow required to reproduce the computational analyses reported in the associated study.

Because the experimental real-world BEV driving dataset is not publicly distributed, the repository provides **code transparency and conditional computational reproducibility**. Full numerical reproduction requires authorized access to the experimental dataset.

## Data Availability

The source code supporting the findings of this study is publicly available in this repository. The experimental data supporting the findings of this study are available from the corresponding author upon reasonable request.

## Citation

If you use this code or methodology, please cite the associated research article.

Citation information and the article DOI will be added upon publication.

## License

The source code in this repository is distributed under the MIT License. See the `LICENSE` file for details.
