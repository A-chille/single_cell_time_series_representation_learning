# Code and data for "Representation learning of single-cell time-series with deep variational autoencoders"

## Description

Code and data for paper "Representation learning of single-cell time-series with deep variational autoencoders" by Fraisse et al, 2025. This repository contains code for training and evaluating machine learning models to learn meaningful representations of time-series from single cell experiments. 

## Repository Structure

## Environment and Dependencies
- The `environment.yml` file contains all regular dependencies needed to run the code. It can be installed in a fresh Conda environment using the following command: `conda env create -f environment.yml`.
- Additionally, you will need the VRAE code from this GitHub repository: https://github.com/tejaslodaya/timeseries-clustering-vae

### Datasets: 
Those datasets MUST be downloaded from ZENODO: [https://zenodo.org/records/17152452](https://zenodo.org/records/20747946)
- `/temperature_dataset`: Dataset from Tanouchi, Y., Pai, A., Park, H. et al. Long-term growth data of Escherichia coli at a single-cell level. Sci Data 4, 170036 (2017). https://doi.org/10.1038/sdata.2017.36.
- `growth_antibiotic_dataset.csv`: Dataset from James Broughton, Achille Fraisse, Meriem El Karoui. Suppression of bacterial cell death underlies the antagonistic interaction between ciprofloxacin and tetracycline in Escherichia coli. bioRxiv 2024.04.18.590101; https://doi.org/10.1101/2024.04.18.590101

- Additionally, preprocessed datasets used in the Jupyter notebooks are saved in `/saved training sets`

### Model Weights: 
Multiple saved model weights can be found in `/saved_models`. Notably the trained 12-latent space VRAE is saved as `vrae_autoencoder_12.pth`. Most other models were saved using joblib dump.

### Code Notebooks
- `vrae_training.ipynb`: Import the growth/antibiotic training dataset, train the VRAE autoencoder, and generate latent space projections. Includes code to load pretrained model weights and create embeddings.
- `antibiotic_control_classification_vrae.ipynb`: Import the antibiotic dataset, preprocess single-cell tracks, encode sequences with the pretrained VRAE, and evaluate classification performance with explainability diagnostics.
- `temperature_dataset_analysis.ipynb`: Import the temperature dataset, reconstruct time-series, encode with the pretrained VRAE, and visualize latent projections and reconstructions.
- `1DCNN.ipynb`: Train a 1D CNN autoencoder on the antibiotic growth data and train MLP classifiers for antibiotic response prediction tasks, with model training and evaluation metrics..
- `LSTM_classifer.ipynb`: Define and tune LSTM-based classifiers for antibiotic response prediction tasks, with model training and evaluation metrics.
- `tsfresh+MLP_classifier.ipynb`: Extract tsfresh time-series features and train MLP classifiers for antibiotic response prediction tasks, with model training and evaluation metrics.
- `time_series_regression.ipynb`: Encode growth trajectories using VRAE latent embeddings and perform regression to predict elongation rate and fluorescence targets with XGBoost.
- `SOS_and_multivariate_results.ipynb`: Construct multivariate single-cell datasets, encode them with VRAE, and compare results across SOS fluorescence and multivariate feature representations.

### Usage
First get the datasets from zenodo and put them in this folder (one csv file and one folder called `temperature_dataset`).
After installation, you can run the provided notebooks to preprocess data, train models, and visualize results.
