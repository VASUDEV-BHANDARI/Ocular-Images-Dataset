<h1 align="center">👁️ Ocular Images Dataset</h1>

<p align="center">
  <a href="https://www.kaggle.com" target="_blank">
    <img src="https://img.shields.io/badge/Download%20Dataset-From%20Kaggle-blue?style=for-the-badge&logo=kaggle" alt="Kaggle Dataset"/>
  </a>
</p>

---

## 📖 Overview
The **Ocular Images Dataset** is a curated medical imaging dataset containing **retinal fundus photographs** used for developing and testing **AI-based classification models** for *Diabetic Retinopathy (DR)* and *Hypertensive Retinopathy (HR)* detection.  

This dataset provides high-quality labeled images representing various severity stages of both DR and HR conditions.  
It is specifically designed for **deep learning model training, validation, and performance benchmarking**.

---

## 🎯 Objective
The main objective of this dataset is to:
- Facilitate research in **automated retinal disease detection**.  
- Provide a reliable image set for **AI model training and evaluation**.  
- Support computer vision projects in **medical imaging and healthcare analytics**.  

---

## 🩺 Disease Categories Included
The dataset covers multiple categories of **retinopathy severity**, helping models learn feature variations across different retinal conditions.

| Category | Description |
|-----------|--------------|
| **Mild DR** | Early signs of diabetic retinopathy with few microaneurysms and small hemorrhages. |
| **Moderate DR** | Increased microaneurysms, hemorrhages, and venous abnormalities visible in the retina. |
| **Severe DR/HR** | Extensive retinal bleeding, cotton wool spots, and vessel swelling — advanced stage requiring medical attention. |
| **Proliferative DR** | Formation of new abnormal blood vessels leading to possible vision loss. |
| **Proliferative HR** | Advanced hypertensive retinopathy with vascular occlusion or optic disc edema. |
| **Moderate HR** | Moderate damage due to hypertension affecting the retinal vessels. |
| **No DR/HR** | Healthy retina with no visible signs of diabetic or hypertensive retinopathy. |

---

## 🧠 Applications
This dataset can be used for:
- 🩺 **AI-based retinal disease classification**
- 🔍 **Deep learning model training and validation**
- 📈 **Computer vision and medical image segmentation**
- 📊 **Performance benchmarking for CNN architectures (ResNet, EfficientNet, etc.)**
- 🧪 **Research in ophthalmology and healthcare AI**

---

## ⚙️ Technical Details

| Attribute | Description |
|------------|--------------|
| **Source** | [Kaggle](https://www.kaggle.com) |
| **Format** | JPEG / PNG images |
| **Total Images** | Varies depending on class balance (e.g., ~100–500 per class) |
| **Resolution** | 512×512 to 1024×1024 pixels |
| **Annotations** | Class-labeled by disease type and severity |
| **Usage** | Model training, testing, and evaluation |
| **Tools Used** | Python, OpenCV, TensorFlow / PyTorch, scikit-learn |

---

## 🧩 Folder Structure
```
📁 Ocular-Images-Dataset/
│
├── 📂 Mild_DR/
├── 📂 Moderate_DR/
├── 📂 Severe_DR_HR/
├── 📂 Proliferative_DR/
├── 📂 Proliferative_HR/
├── 📂 Moderate_HR/
└── 📂 No_DR_HR/
```

Each folder contains images belonging to its respective category, labeled according to medical diagnosis.

---

## 🧪 Example Use Case
This dataset is primarily used for:
- Training **Convolutional Neural Networks (CNNs)** for multi-class classification.  
- Evaluating model accuracy, precision, recall, and F1-score across DR/HR categories.  
- Implementing **image preprocessing** techniques such as resizing, histogram equalization, and contrast enhancement.  
- Performing **Grad-CAM** or **saliency mapping** to visualize disease-related retinal regions.

---

## 🔬 Suggested Preprocessing Techniques
- Image resizing to uniform dimensions  
- CLAHE (Contrast Limited Adaptive Histogram Equalization)  
- RGB normalization  
- Data augmentation (rotation, flipping, brightness variation)  
- Gaussian filtering for noise reduction  

---

## 🧠 Model Training Example (Python)
Here’s a simplified example for using this dataset in deep learning model training:

```python
from tensorflow.keras.preprocessing.image import ImageDataGenerator
from tensorflow.keras.applications import EfficientNetB0
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense, GlobalAveragePooling2D

# Data generator
train_gen = ImageDataGenerator(rescale=1./255, validation_split=0.2)

train_data = train_gen.flow_from_directory(
    'Ocular-Images-Dataset',
    target_size=(224, 224),
    batch_size=32,
    subset='training'
)

val_data = train_gen.flow_from_directory(
    'Ocular-Images-Dataset',
    target_size=(224, 224),
    batch_size=32,
    subset='validation'
)

# Model
model = Sequential([
    EfficientNetB0(weights='imagenet', include_top=False, input_shape=(224,224,3)),
    GlobalAveragePooling2D(),
    Dense(7, activation='softmax')  # 7 classes
])

model.compile(optimizer='adam', loss='categorical_crossentropy', metrics=['accuracy'])
model.fit(train_data, validation_data=val_data, epochs=20)
```

---

## 📚 Potential Research Directions
- Diabetic vs. hypertensive retinopathy differentiation  
- Multi-label classification for comorbid eye diseases  
- Explainable AI for ophthalmic image analysis  
- Transfer learning and fine-tuning for medical imaging datasets  

---

## 📈 Citation
If you use this dataset in your research or project, please cite the source:
> Kaggle – Ocular Image Dataset for Retinopathy Classification (retrieved from https://www.kaggle.com)

---

⭐ **If you find this dataset useful, please star the repository and share it to support open-source medical AI research!**
