# scone
Re-implementation of [SCONE paper](https://arxiv.org/pdf/2106.04370.pdf) by Helen Qu

## Overview

This project aims to classify Type Ia supernovae from other transients and variable phenomena using a convolutional neural network. The dataset used is the [PLAsTiCC dataset](https://plasticc.org/), which contains light curves for various objects. The data is too large to include on GitHub, but it's available for download on Kaggle.

## Methods

Because CNNs are particularly good at working with images, I generated "heatmaps" from light curves by using Gaussian Process Regression. An sample light curve is shown below:

![Sample light curve](/lightcurve.png "Sample light curve")

Given the flux values at different times, as well as the passband for each measurement, Gaussian Process Regression can yield a 2D matrix, with one dimension being time and the other being wavelength. Essentially, we "augment" the data and generate light curves at various wavelengths. This heatmap is the input to the CNN, which detects patterns in the heatmap to classify Type Ia supernovae.

## Results
![Accuracies](/accuracies.png "Accuracies")

Overall, the model achieves a training accuracy of 98.16%, a validation accuracy of 86.24%, and a test accuracy of 83.18%. The training set was class-balanced, while the validation and test sets were not. The paper achieves a test accuracy of 83-87% on similar datasets. The amount of data I could use was limited as I am developing on a personal computer, but the model performed well nonetheless.
