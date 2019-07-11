# Vehicle Re-identification on VeRi dataset
Modification of cosine_metric_learning from https://github.com/nwojke/cosine_metric_learning/issues
===============================================================
## Introduction
This repository is heavily borrowed from Deep Cosine Metric Learning for Person Re-identification(https://github.com/nwojke/cosine_metric_learning/issues).

The original github project is trained on Mars and Market1501 pedestrian dataset and aimed to extract the 128 dimensional feature of the pedestrain to achieve person re-identification.

There are two files added in this repository to train on the VeRi dataset:
- train_veri.py: The training code for vehicle re-id.
- datasets/veri.py: The dataset preprocessing for VeRi dataset.

## Dataset
The VeRi dataset contains over 50,000 images of 776 vehicles captured by 20 cameras covering an 1.0 km^2 area in 24 hours, which makes the dataset scalable enough for vehicle Re-Id and other related research. see this page for more information(https://github.com/VehicleReId/VeRidataset).


