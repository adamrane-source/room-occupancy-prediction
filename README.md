# room-occupancy-prediction
comparing logistic regression and random forest for a room occupancy detection
# Room Occupancy Prediction

This project compares Logistic Regression and Random Forest to predict
whether an office room is empty (0) or occupied (1), using environmental
sensor measurements. A majority-class baseline is also included.

## Files

- Room_Occupancy_Project.ipynb: code, explanations and results.
- datatraining.txt: 8,143 training observations.
- datatest.txt: 2,665 earlier-period test observations.
- datatest2.txt: 9,752 later-period test observations.

## Dataset and licence

Candanedo, L. (2016). Occupancy Detection.
UCI Machine Learning Repository.
https://doi.org/10.24432/C5X01N

Source: https://archive.ics.uci.edu/dataset/357/occupancy-detection

The dataset is licensed under Creative Commons Attribution 4.0
International (CC BY 4.0). The included data files are provided unchanged.

## How to run in Google Colab

1. Download the notebook and three data files from this repository.
2. Open https://colab.research.google.com/ and upload the notebook.
3. Upload all three .txt files to the Colab Files panel under /content/.
4. Select Run all to execute the notebook from top to bottom.

The notebook produces charts and CSV results in /content/.
Download generated files before the runtime is deleted.

## Software versions

- Python 3.13.18
- pandas 2.2.3
- scikit-learn 1.6.1
- matplotlib 3.10.0
- seaborn 0.13.2

These versions were recorded during the Colab rerun.

## Method

The supplied training set is used for exploratory analysis and model
development. Validation uses three expanding chronological splits,
with a gap of 60 observations between training and validation.

Logistic Regression uses standardisation within a pipeline.
Both test sets are reserved for final evaluation.

## Results

Logistic Regression without humidity ratio was selected using pooled
validation F1. On the later-period test set:

| Model | Accuracy | Precision | Recall | F1 |
|---|---:|---:|---:|---:|
| Logistic Regression | 0.9867 | 0.9743 | 0.9619 | 0.9681 |
| Random Forest | 0.9880 | 0.9721 | 0.9707 | 0.9714 |

Random Forest performed slightly better on the later test period,
while Logistic Regression performed better on the earlier test period.
The models were not retuned using test results.

## Limitations

The data covers one room over a short recording period. Neighbouring
observations are time-dependent, and results may not generalise to
other rooms, buildings or seasons.
