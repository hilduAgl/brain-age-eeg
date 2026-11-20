
# Brain Age Prediction from EEG

Final project for REI505M – Artificial Intelligence,
University of Iceland, November 2026.

## Project Overview

This project investigates predicting children's chronological
age from preprocessed EEG recordings.

We compare two machine-learning approaches:

1. Feature-based regression using Hjorth parameters,
   spectral band-power features and Ridge regression.
2. A convolutional neural network (CNN) trained on
   8-second EEG windows.

We also investigate whether averaging CNN predictions
from multiple windows improves age prediction.

## Dataset

The dataset contains approximately 1,032 children,
with ages ranging from 0.16 to 16.01 years.

The preprocessed recordings contain 20 bipolar EEG
channels sampled at 64 Hz.

Subject-level splits:
- Training: 825 children
- Validation: 103 children
- Test: 104 children

The dataset is stored separately in Google Drive
and is not included in this repository.

## Project Structure

- `notebooks/starter/`
  Starter notebooks provided for the project.

- `notebooks/eda.ipynb`
  Dataset exploration, age distributions, EEG
  visualizations and channel analysis.

- `notebooks/baseline.ipynb`
  Handcrafted EEG feature extraction, linear
  regression and Ridge regression experiments.

- `notebooks/cnn.ipynb`
  CNN architecture, training, hyperparameter
  experiments and checkpoint creation.

- `notebooks/cnn_multisegment.ipynb`
  Multi-window CNN inference using 1, 5, 10
  and 20 windows per subject.

- `evaluation.ipynb`
  Final model comparison, evaluation metrics
  and prediction visualizations.

- `results/figures/`
  Output figures, when exported locally.

## Final Results

All errors are measured in years.

| Model | Validation MAE | Test MAE | Test RMSE |
|---|---:|---:|---:|
| Ridge regression | 1.1346 | 1.1251 | 1.4647 |
| CNN, 1 window | 1.4846 | — | — |
| CNN, 20 windows | 1.2507 | 1.0214 | 1.3416 |

The 20-window CNN configuration was selected
using validation MAE.

Earlier CNN development experiments inspected
test-set results, so the test set was not
completely untouched during development.

## Multi-Window CNN Experiment

The trained CNN predicts age from one 8-second
EEG window at a time.

We compared averaging predictions from
1, 5, 10 and 20 windows per child.

| Windows | Validation MAE |
|---|---:|
| 1 | 1.4846 |
| 5 | 1.3343 |
| 10 | 1.3159 |
| 20 | 1.2507 |

The CNN weights were kept fixed throughout
this experiment.

## Running the Notebooks

The notebooks were developed in Google Colab.

1. Open the project notebooks in Colab.
2. Mount Google Drive.
3. Ensure the preprocessed EEG data and split
   files are available under:
   `/content/drive/MyDrive/BrainAge/data/`
4. Run the EDA or baseline notebook as needed.
5. Run `cnn.ipynb` to train a CNN and save
   a checkpoint, if a checkpoint is not
   already available.
6. Run `cnn_multisegment.ipynb` using the
   saved CNN checkpoint.
7. Run `evaluation.ipynb` to compare the
   saved subject-level predictions.

The multi-window notebook expects the checkpoint at:

`/content/drive/MyDrive/BrainAge/cnn_best.pth`

Prediction CSVs are stored under:

`/content/drive/MyDrive/BrainAge/results/`

The final CNN checkpoint uses the flat architecture,
8-second windows and 64 Hz sampling.

## Dependencies

The required Python packages are listed in
`requirements.txt`.

The notebooks use Google Colab for Drive access
and PyTorch for CNN training and inference.

## Team Contributions

- Hildur Agla: EDA, dataset split checks,
  multi-window CNN inference, final evaluation
  and visualizations.
- Arnar Gauti: EEG feature extraction,
  linear regression and Ridge regression.
- Pétur Valur: CNN architecture, training
  and hyperparameter experiments.

Project planning, discussion and final reporting
were shared among the team.

## Reproducibility Notes

The CNN training notebook records the architecture
and training configuration in its saved checkpoint.

Multi-window inference uses the same trained
weights for each window-count experiment.

The original EEG recordings and large model files
are not included in this repository.

The final report contains the full methodology,
results, limitations and AI-use disclosure.
