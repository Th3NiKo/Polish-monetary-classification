# Polish monetary classification

![Banner](banner.png?raw=true "Coins banner")

## Purpose

Creating neural network model which will be able to recognize polish coins on close-up photos.

## Dataset

All images used in this project are created by me and possible to download from [Kaggle platform (Train set 250mb + Test set 20mb)](https://www.kaggle.com/dataset/3d332f1bb83f393ef0d8b60e014ab57ceffac075365231c065543b5562708909) \
Ready-to-use model: [Google drive (239mb)](https://drive.google.com/file/d/1BhPjHz6q7xsNcCSZjGq9cfh6hbvQECGH/view?usp=sharing)

Dataset contains 790 images (with diffrent sizes) of coins classified into 9 folders (classes). 

### Class equivalents

| Class name  | Polish equivalent | PLN fraction |
| ------------- | ------------- | ------------- |
| 11 | 1 grosz (gr) | 0.01 |
| 22 | 2 grosze (gr)| 0.02 |
| 55 | 5 groszy (gr) | 0.05 |
| 10 | 10 groszy | 0.1 |
| 20 | 20 groszy | 0.2 |
| 50 | 50 groszy | 0.5 |
| 1 | 1 złoty (zł) | 1 |
| 2 | 2 złote (zł) | 2 |
| 5 | 5 złotych (zł) | 5 |

## Training

[Notebook](https://github.com/Th3NiKo/Polish-monetary-classification/blob/main/Monetary_model_training.ipynb)

Dataset were trained using transfer learning and finetunning. Xception was used as base model (initialized with imagenet weights).
In first part of training base model weights were freezed (only output weights were trained).
In second part whole model was finetunned with lower learning rate. 

Early stopping method were used to get model which maximize validation dataset accuracy.


## Evaluation

| Type | Train_accuracy | Train_recall | Train_precision | Validation_accuracy | Validation_recall | Validation_precision | 
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| Only output parameters trained | 0.9112 | 0.6568 | 0.9867 | 0.8158 | 0.5439 | 0.9538 |
| Finetuning | 1.0 | 0.9985 | 1.0 | 0.9825 | 0.9737 | 0.9911 | 


### Independent test set

Test set included in kaggle dataset.

[Notebook]https://github.com/Th3NiKo/Polish-monetary-classification/blob/main/Evaluation_and_inference.ipynb

| Accuracy | Precision | Recall |
| -------- | -------- | -------- |
| 1.0 | 1.0 | 1.0 |

## Conclusion

Dataset trained well on xception model. It recognizes most of the close up photos. Tend to struggle with intensive light photos.