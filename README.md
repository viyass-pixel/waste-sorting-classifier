# ♻️ Waste Sorting Classifier
 
An image classifier built with **PyTorch** that looks at a photo of trash and predicts which category it belongs to: **cardboard, glass, metal, paper, plastic, or trash**.
 
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/viyass-pixel/waste-sorting-classifier/blob/main/waste_classifier.ipynb)
 
## 🎯 Problem Statement
 
Manual waste sorting is slow and error-prone. This project explores whether a deep learning model can automatically recognize the type of waste from an image, as a small step toward automated recycling systems.
 
## 📊 Results
 
| Metric | Value |
|---|---|
| **Test accuracy** | **90.1%** (on 253 unseen images) |
| Model | ResNet18 (pretrained on ImageNet) |
| Training time | A few minutes on a free Colab T4 GPU |
 
 
## 🗂️ Dataset
 
- **TrashNet** by Gary Thung and Mindy Yang (Stanford)
- ~2,500 images across 6 classes: cardboard, glass, metal, paper, plastic, trash
- Source: [garythung/trashnet](https://github.com/garythung/trashnet) / [Hugging Face](https://huggingface.co/datasets/garythung/trashnet)
## 🧠 Approach
 
1. **Data split:** stratified 80% train / 10% validation / 10% test (fixed random seed for reproducibility)
2. **Preprocessing:** resize to 224×224, convert to tensors, normalize with ImageNet statistics
3. **Data augmentation (train only):** random horizontal flip, random rotation (±15°), brightness/contrast jitter
4. **Model:** pretrained **ResNet18** with its final layer replaced by a 6-class output layer (**transfer learning**)
5. **Training:** cross-entropy loss, Adam optimizer (lr = 3e-4), batch size 32, 8 epochs
6. **Model selection:** the checkpoint with the best validation accuracy is saved and evaluated once on the test set
7. **Evaluation:** test accuracy, loss/accuracy curves, and a confusion matrix
## 🛠️ Tech Stack
 
- Python
- PyTorch & torchvision
- scikit-learn (data splitting, confusion matrix)
- Matplotlib
- Google Colab (GPU)
- Gradio (optional demo)
## 🚀 How to Run
 
1. Click the **Open in Colab** badge above (or upload `waste_classifier.ipynb` to [Google Colab](https://colab.research.google.com))
2. Go to **Runtime > Change runtime type** and select **T4 GPU**
3. Run all cells from top to bottom. The dataset is downloaded automatically.
## 📁 Project Structure
 
```
├── waste_classifier.ipynb   # Full notebook: data, training, evaluation, demo
├── confusion_matrix.png     # Test set confusion matrix
├── training_curves.png      # Loss and accuracy curves
└── README.md
```
 
## 📚 What I Learned
 
- **PyTorch:** building data pipelines with `Dataset` / `DataLoader`, writing a training loop, working with loss functions and optimizers
- **Computer Vision:** image preprocessing, data augmentation, and how CNNs like ResNet learn visual features
- **Transfer learning:** reusing a pretrained model instead of training from scratch
- **Model evaluation:** using validation/test splits, accuracy curves, and a confusion matrix to understand model behavior
## 🔮 Future Improvements
 
- [ ] Gradio web demo for uploading a photo and getting a live prediction
- [ ] Compare other architectures (MobileNet, EfficientNet)
- [ ] Train on a more diverse dataset with real-world, messy photos
- [ ] Deploy as a web app
## 🙏 Acknowledgements
 
Dataset: [TrashNet](https://github.com/garythung/trashnet) by Gary Thung and Mindy Yang.
 
## 👤 Author
 
**Viyass S**
[LinkedIn](https://linkedin.com/in/viyass-s-538943255) · [GitHub](https://github.com/viyass-pixel)
