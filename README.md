# Brain Age Prediction from EEG

Final project for REI505M – Artificial Intelligence, University of Iceland.

The goal of the project is to predict chronological age from EEG recordings.

## Project structure

- `notebooks/eda.ipynb` – exploratory data analysis
- `notebooks/baseline.ipynb` – simple EEG features + linear regression
- `notebooks/cnn.ipynb` – CNN trained on EEG segments
- `notebooks/starter/` – starter notebooks provided for the project
- `src/` – reusable Python code
- `results/figures/` – figures generated from experiments

The EEG dataset is stored separately in the shared Google Drive and is not included in this repository.

## Experiment log

| Date | Person | Model | Features / Input | Segment length | Validation MAE | Notes |
|------|--------|-------|------------------|----------------|----------------|-------|
| 2026-11-04 | Hildur | Linear regression | Hjorth mobility | TBD | TBD | Initial baseline |
| | | | | | | |
| | | | | | | |

## Current tasks

- [ ] Load and inspect preprocessed EEG data
- [ ] Exploratory data analysis
- [ ] Extract Hjorth features
- [ ] Extract band-power features
- [ ] Train linear regression baseline
- [ ] Evaluate baseline with MAE/RMSE
- [ ] Implement CNN
- [ ] Train CNN
- [ ] Compare baseline and CNN

## Team responsibilities

### Hildur – Data & EDA
- Understand the provided EEG starter code
- Set up data loading
- Verify train/validation/test splits
- Explore age distribution and dataset statistics
- Visualize example EEG recordings
- Investigate channels and potential artifacts
- Maintain `notebooks/eda.ipynb`

### Arnar Gauti – Feature-based baseline
- Extract simple EEG features
- Hjorth parameters
- Spectral/band-power features
- Train linear regression baseline
- Evaluate using MAE/RMSE
- Maintain `notebooks/baseline.ipynb`

### Pétur – CNN
- Set up EEG segment loading
- Implement CNN
- Train CNN from scratch
- Track training/validation performance
- Evaluate CNN
- Maintain `notebooks/cnn.ipynb`

### Shared
- Review each other's code
- Decide final experimental setup
- Compare baseline and CNN
- Analyze results
- Prepare final report