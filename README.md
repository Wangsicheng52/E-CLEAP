# E-CLEAP: An Ensemble Learning Model for Efficient and Accurate Identification of Antimicrobial Peptides

[![DOI](https://img.shields.io/badge/DOI-10.1371%2Fjournal.pone.0300125-blue)](https://doi.org/10.1371/journal.pone.0300125)

## Introduction

E-CLEAP is an ensemble learning model designed for the identification of antimicrobial peptides (AMPs). AMPs are small molecular peptides with broad-spectrum antimicrobial activity that offer advantages such as rapid action, low resistance development, and minimal selective pressure compared to traditional antibiotics.

With the increasing problem of antimicrobial drug resistance, E-CLEAP provides a computational solution to efficiently and accurately identify antimicrobial peptides, which can accelerate the discovery of new antimicrobial agents.

## Model Architecture

E-CLEAP consists of four MLPClassifier models with different parameters and architectures:

- **clf1 & clf4**: Two hidden layers (100, 50 nodes)
- **clf2 & clf3**: Four hidden layers (100, 100, 50, 25 nodes)

Common parameters for all classifiers:
- Random seed: 420
- Maximum iterations: 5000
- Initial learning rate: 0.001
- Momentum factor: 0.9
- Batch size: 8
- Optimization algorithm: Adam
- Activation function: ReLU

The model combines predictions through soft voting, where probabilities are weighted and averaged based on the model's weights.

![Ensemble model architecture diagram](images/Fig2.png)

## Features

E-CLEAP uses two main feature extraction methods:

1. **Amino Acid Composition (AAC)**: Calculates the frequency of occurrence of each amino acid in the entire sequence
2. **Pseudo Amino Acid Composition (PseAAC)**: Captures structural and functional information of sequences by counting occurrence frequencies of amino acid fragments

## Dataset

The dataset consists of:
- 1750 experimentally validated antimicrobial peptide samples from APD3, PlantPepDB, BaAMPs, and BioPepDB
- 1750 non-antimicrobial peptide samples from UniProt database

For model construction:
- Training set: 3000 samples
- Test set: 500 samples

## Performance

E-CLEAP significantly outperforms traditional machine learning models (SVM, Bayes, K-NN, DT) in antimicrobial peptide identification:

### AAC Feature Results on Test Set:
- Accuracy: 97.33%
- Recall: 98.68%
- Precision: 96.15%
- F1-score: 97.40%

### PseAAC Feature Results on Test Set:
- Accuracy: 84.00%
- Recall: 87.65% 
- Precision: 83.53%
- F1-score: 85.54%

![ROC curves and AUC values for different models on the test set (AAC features)](images/Fig6.png)

## Requirements

- Python 3.x
- NumPy
- Scikit-learn
- Pandas
- Matplotlib
- Biopython

## Usage

### 1. Clone the repository

```bash
git clone https://github.com/Wangsicheng52/E-CLEAP.git
cd E-CLEAP
