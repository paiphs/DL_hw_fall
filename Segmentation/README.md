# Semantic Segmentation Experiments

## Dataset
The **CamVid dataset** is used for training, validation, and testing. It contains images of urban scenes and corresponding pixel-level annotations. The dataset was processed to ensure image dimensions are divisible by 32, which is required for U-Net models.

## Models and Loss Functions
### Encoders
The following encoder architectures were evaluated:
1. **ResNet34**
2. **DenseNet121**

### Loss Functions
Three loss functions from the `segmentation_models_pytorch` library were tested:
1. **DiceLoss**
2. **JaccardLoss**
3. **FocalLoss**

## Pre-Fine-Tuning Metrics
Before fine-tuning on the CamVid dataset, the models were evaluated with their ImageNet pre-trained weights. The Intersection over Union (IoU) scores for the validation set were as follows:

| Encoder       | IoU     |
|---------------|---------|
| ResNet34      | 0.010100|
| DenseNet121   | 0.010632|

## Fine-Tuning Results
The models were fine-tuned using the CamVid dataset, and their performance was measured on the validation set. The results for each encoder and loss function combination are shown below:

| Encoder       | Loss Function | Val Loss  | Val IoU  |
|---------------|---------------|-----------|----------|
| ResNet34      | DiceLoss      | 0.111093  | 0.620937 |
| ResNet34      | JaccardLoss   | 0.148295  | 0.607671 |
| ResNet34      | FocalLoss     | 0.156535  | 0.441159 |
| DenseNet121   | DiceLoss      | 0.105749  | 0.630606 |
| DenseNet121   | JaccardLoss   | 0.151662  | 0.600078 |
| DenseNet121   | FocalLoss     | 0.151727  | 0.472506 |