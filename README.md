# CO₂ Methanation Modeling

This project compares data-driven, physics-based, and physics-informed approaches for predicting methane yield during CO₂ methanation.

The processed dataset contains 215 experiments with different temperatures, gas compositions, and flow conditions. Model performance is evaluated using RMSE under three protocols:

- interpolation with 5-fold cross-validation;
- generalization to excluded operating regions;
- temperature extrapolation from below 260 °C to 260 °C and above.

## Notebooks

Run the notebooks in this order:

1. [Preprocessing and EDA](notebooks/preprocessing_eda.ipynb) : cleans the data and explores the operating space.
2. [Machine Learning baseline](notebooks/machine_learning_baseline.ipynb) : compares conventional regression models.
3. [Physics-based kinetic modeling](notebooks/physics_based_kinetic_modeling.ipynb) : implements reversible Power Law and LHHW models.
4. [PINN-LHHW](notebooks/physics_informed_neural_network_LHHW.ipynb) : combines a neural network with the LHHW reactor balance.

## Installation

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Open the notebooks with JupyterLab, Jupyter Notebook, or VS Code.

## Main Results

RMSE is reported in methane-yield percentage points.

| Model | Interpolation | Regional generalization | Temperature extrapolation |
|---|---:|---:|---:|
| Neural Network | 1.754 | 6.264 | 10.417 |
| Reversible Power Law | 1.628 | 2.680 | 3.607 |
| LHHW | **1.132** | **1.630** | **3.138** |
| PINN-LHHW | 1.576 | 3.999 | 4.098 |

The LHHW model gives the best results across all three evaluation protocols. The compact PINN improves over the conventional Neural Network but does not outperform the calibrated LHHW model.

## Project Structure

```text
data/       Processed dataset and data dictionary
notebooks/  Preprocessing, ML, kinetic modeling, and PINN notebooks
papers/     Reference research paper
reports/    Generated metrics and figures
```

The cleaned dataset is available at `data/processed/co2_methanation_clean.csv`, and column definitions are documented in [DATA_DICTIONARY.md](data/DATA_DICTIONARY.md).
