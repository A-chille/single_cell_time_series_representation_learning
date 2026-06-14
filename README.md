# Code and data for "Representation learning of single-cell time-series with deep variational autoencoders"

## Description

Code and data for paper "Representation learning of single-cell time-series with deep variational autoencoders" by Fraisse et al, 2025. This repository contains code for training and evaluating machine learning models to learn meaningful representations of time-series from single cell experiments. Files contain the two datasets used in this study (which can also be found in their respective storage) in `/temperature_dataset` and `growth_antibiotic_dataset.csv`. This repository also contains Jupyter notebooks with code for training the models, encoding the data and evaluating the embeddings.

## Repository Structure

## Environment and Dependencies
- The `environment.yml` file contains all regular dependencies needed to run the code. It can be installed in a fresh Conda environment using the following command: `conda env create -f environment.yml`.
- Additionally, you will need the VRAE code from this GitHub repository: https://github.com/tejaslodaya/timeseries-clustering-vae

### Datasets: 
Those datasets MUST be downloaded from ZENODO: https://zenodo.org/records/17152452
- `/temperature_dataset`: Dataset from Tanouchi, Y., Pai, A., Park, H. et al. Long-term growth data of Escherichia coli at a single-cell level. Sci Data 4, 170036 (2017). https://doi.org/10.1038/sdata.2017.36.
- `growth_antibiotic_dataset.csv`: Dataset from James Broughton, Achille Fraisse, Meriem El Karoui. Suppression of bacterial cell death underlies the antagonistic interaction between ciprofloxacin and tetracycline in Escherichia coli. bioRxiv 2024.04.18.590101; https://doi.org/10.1101/2024.04.18.590101

### Model Weights
-`/model_12.pth`: Weights for the variational recurrent autoencoder to be imported by the Jupyter notebooks. Notable parameters:

    - sequence_length = 72
    - number_of_features = 1
    - latent_length = 12
    - hidden_size = 90
    - hidden_layer_depth = 2
    - block = `LSTM`

### Code Notebooks
- `/vrae_training.ipynb`: Code for importing the training dataset, training the autoencoder and generating latent space projections of the embedded data. Also imports our trained model weights to generate embeddings.
- `/antibiotic_control_classification.ipynb`: Code for importing the trained model weights and the antibiotic dataset, encoding the data, and performing binary classification.
- `/temperature_dataset_analysis.ipynb`: Code for importing the trained model weights and the temperature dataset, showing reconstructions of the time-series, encoding the data and performing projections in the latent space.

### Usage
After installation, you can run the provided notebooks to preprocess data, train models, and visualize results.
