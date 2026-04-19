# Automated Melanoma Detection Using Deep Learning

## Overview
This project focuses on building a binary classifier for dermoscopic skin lesion images to distinguish between **melanoma** and **non-melanoma (other)** cases.

The aim is to support clinical decision-making by developing a model that can assist in early melanoma detection while maintaining interpretability.

---

## Dataset
The dataset used is the **ISIC 2017 dermoscopic image dataset**, structured as:

- **Training set**: Balanced (Melanoma vs Other)
- **Validation set**: Balanced
- **Test set**: Imbalanced (fewer melanoma cases)

> Note: The dataset is not included in this repository due to size and licensing.  


---

## Methodology

### Data Preprocessing
- Images resized to **224 × 224**
- Normalisation using ImageNet statistics

### Data Augmentation
- Random horizontal and vertical flips  
- Random rotations  
- Brightness and contrast adjustments  

These steps help improve generalisation and reduce overfitting.

---

### Model
- **Architecture**: ResNet-50 (pretrained on ImageNet)
- Transfer learning applied to leverage learned visual features
- Final fully connected layer modified for **binary classification**

---

### Training Setup
- **Loss Function**: CrossEntropyLoss  
- **Optimizer**: Adam  
- **Learning Rate Scheduler**: ReduceLROnPlateau  

---

## Evaluation Metrics
To ensure a robust evaluation, multiple metrics were used:

- Accuracy  
- Precision  
- Recall  
- F1-score  
- ROC-AUC  

Special focus was placed on **recall**, as correctly identifying melanoma cases is critical in clinical settings.

---

## Results (Test Set)

- **Accuracy**: ~68%  
- **Melanoma Recall**: ~82%  
- **Precision (Melanoma)**: ~36%  
- **F1-score**: ~0.50  
- **ROC-AUC**: ~0.83  

### Key Insight
The model achieves strong recall for melanoma, meaning most melanoma cases are detected. However, this comes with increased false positives.

---

## Interpretability
Grad-CAM was used to visualise model decision-making.

- In many cases, the model focuses on lesion regions  
- Some cases show attention to artefacts (e.g., skin texture or markings)

This helps assess model reliability and transparency.
<img width="831" height="293" alt="image" src="https://github.com/user-attachments/assets/072f73bf-2aba-4c2e-b575-ef755923a998" />

---

## Limitations
- Imbalanced test dataset affects precision  
- False positives are present  
- Some sensitivity to image artefacts  
- Limited dataset diversity  

---

## Future Work
- Improve precision while maintaining high recall  
- Use more diverse and larger datasets  
- Explore advanced architectures and fine-tuning strategies  
- Further validate model in clinical settings
