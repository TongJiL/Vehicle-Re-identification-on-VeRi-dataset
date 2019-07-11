# Vehicle Re-identification on VeRi dataset
## Modification of cosine_metric_learning from https://github.com/nwojke/cosine_metric_learning

## Introduction
This repository is heavily borrowed from Deep Cosine Metric Learning for Person Re-identification(https://github.com/nwojke/cosine_metric_learning).

The original github project is trained on Mars and Market1501 pedestrian dataset and aimed to extract the 128 dimensional feature of the pedestrain to achieve person re-identification.

There are two files added in this repository to train on the VeRi dataset:
- train_veri.py: The training code for vehicle re-id.
- datasets/veri.py: The dataset preprocessing for VeRi dataset.

This vehicle re-id is mainly used for [deep_sort tracker](https://github.com/nwojke/deep_sort).


## Dataset
The VeRi dataset contains over 50,000 images of 776 vehicles captured by 20 cameras covering an 1.0 km^2 area in 24 hours, which makes the dataset scalable enough for vehicle Re-Id and other related research. see this page for more information(https://github.com/VehicleReId/VeRidataset).

![image](https://github.com/TongJiL/Vehicle-Re-identification-on-VeRi-dataset/blob/master/pic/VeRi_240.png)

If you need to use this dataset, please contact the author of VeRi.


## Train on VeRi
The following description assumes you have downloaded the VeRi dataset to ./VeRi. The following command starts training using the cosine-softmax classifier described in this paper(https://elib.dlr.de/116408/):

```markdown
python train_market1501.py \
    --dataset_dir=./VeRi/ \
    --loss_mode=cosine-softmax \
    --log_dir=./output/veri/ \
    --run_id=cosine-softmax
```
This will create a directory ./output/veri/cosine-softmax where TensorFlow checkpoints are stored and which can be monitored using tensorboard:
```markdown
tensorboard --logdir ./output/veri/cosine-softmax --port 6006
```

Sometimes there would be some bugs with the tensorboard and the site can not be displaied. You can try:
```markdown
tensorboard --logdir ./output/veri/cosine-softmax --port 8080
```

## Model export
To export your trained model for use with the deep_sort tracker, run the following command:
```markdown
python train_veri.py --mode=freeze --restore_path=PATH_TO_CHECKPOINT
```

