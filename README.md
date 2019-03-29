# pyts-repro: a repository to compare the accuracies between the results published in the literature and the accuracies using pyts

## Introduction

**pyts** 
([GitHub](https://github.com/johannfaouzi/pyts),
[Documentation](https://pyts.readthedocs.io/en/latest/),
[PyPI](https://pypi.org/project/pyts/)) is a Python package dedicated to time series
classification. It provides several tools to preprocess the data and implementations
for many state-of-the-art algorithms. The goal of this repository is to compare the
accuracies between the ones published in the literature and the ones using `pyts`.
Alongside the high code coverage, it aims at ensuring that the implementations 
in `pyts` are reliable.

**Note: Most algorithms have hyperparameters that need to be fine-tuned for each dataset.
If the values of these hyperparamaters are not directly available, a gridsearch is performed
using the testing set. For each of those algorithms, the accuracy reported in the `pyts`
column is the minimum of the accuracy reported in the article and the highest accuracy
obtained with the gridsearch (to avoid any overestimation of the performance of the algorithm
because of data leakage). The same gridsearches as the ones presented in the articles are
usually not done for computational reasons.**


## Datasets

The datasets used are taken from the [UCR Time Series Classification Archive](https://www.cs.ucr.edu/%7Eeamonn/time_series_data_2018/). On this website, you can download the datasets (a password is required to unzip the file, you can find it by reading the PDF or the PowerPoint) and the table with the results using a 1NN classifier with several metrics (Euclidean Distance, Dynamic Time Warping and Dynamic Time Warping with a learning warping window). For computational reasons, the algorithms are only tested on the smallest datasets. This way, anyone can run the notebooks by themselves on a single machine and verify the results. The selected datasets are presented in the table below.

| Type        | Name             | Train | Test | Class | Length |
|:-----------:|:----------------:|:-----:|:----:|:-----:|:------:|
| Image       | Adiac            | 390   | 391  | 37    | 176    |
| ECG         | ECG200           | 100   | 100  | 2     | 96     |
| Motion      | GunPoint         | 50    | 150  | 2     | 150    |
| Image       | MiddlePhalanxTW  | 399   | 154  | 6     | 80     |
| Sensor      | Plane            | 105   | 105  | 7     | 144    |
| Simulated   | SyntheticControl | 300   | 300  | 6     | 60     |


## Comparisons

[Link to the notebook]()

### 1NN classifier with Euclidean Distance, Dynamic Time Warping and Dynamic Time Warping with a learned warping window

| Name             | ED (reported) | ED (pyts) | DTW (reported) | DTW (pyts) | DTW(w) (repored)  | DTW(w) (pyts)  |
|:----------------:|:-------------:|:---------:|:--------------:|:----------:|:-----------------:|:--------------:|
| Adiac            | 0.6113        | 0.6113    | 0.6036         | 0.6036     | 0.6087            | 0.6087         |
| ECG200           | 0.8800        | 0.8800    | 0.7700         | 0.7700     | 0.8800            | 0.8800         |
| GunPoint         | 0.9133        | 0.9133    | 0.9067         | 0.9067     | 0.9133            | 0.9133         |
| MiddlePhalanxTW  | 0.5130        | 0.5130    | 0.5065         | 0.5065     | 0.5065            | 0.5065         |
| Plane            | 0.9619        | 0.9619    | 1.0000         | 1.0000     | 1.0000            | 1.0000         |
| SyntheticControl | 0.8800        | 0.8800    | 0.9933         | 0.9933     | 0.9833            | 0.9833         |


<!--
    ### SAX-VSM

    [Link to the notebook]()

    | Name             | SAX-VSM (reported) | SAX-VSM (pyts) |
    |:----------------:|:------------------:|:--------------:|
    | Adiac            |                    |                |
    | ECG200           |                    |                |
    | GunPoint         |                    |                |
    | MiddlePhalanxTW  |                    |                |
    | Plane            |                    |                |
    | SyntheticControl |                    |                |
-->


### BOSSVS classifier

[Link to the notebook]()

| Name             | BOSSVS (reported) | BOSSVS (pyts) |
|:----------------:|:-----------------:|:-------------:|
| Adiac            | 0.698             | 0.698         |
| ECG200           | 0.820             | 0.820         |
| GunPoint         | 1.000             | 1.000         |
| MiddlePhalanxTW  | 0.586             | 0.545         |
| Plane            | Unreported        | 1.000         |
| SyntheticControl | 0.960             | 0.960         |

### BOSS transformer followed by a 1NN classifier using the BOSS metric

[Link to the notebook]()

| Name             | BOSS (reported) | BOSS (pyts) |
|:----------------:|:---------------:|:-----------:|
| Adiac            | 0.765           | 0.752       |
| ECG200           | 0.870           | 0.870       |
| GunPoint         | 1.000           | 1.000       |
| MiddlePhalanxTW  | 0.526           | 0.526       |
| Plane            | 1.000           | 1.000       |
| SyntheticControl | 0.967           | 0.963       |

### WEASEL transformer followed by a logistic regression

[Link to the notebook]()

| Name             | WEASEL (reported) | WEASEL (pyts) |
|:----------------:|:-----------------:|:-------------:|
| Adiac            | 0.8312            | 0.788         |
| ECG200           | 0.8500            | 0.850         |
| GunPoint         | 1.0000            | 0.960         |
| MiddlePhalanxTW  | 0.5390            | 0.539         |
| Plane            | 1.0000            | 1.000         |
| SyntheticControl | 0.9933            | 0.973         |


