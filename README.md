# Adversarial Attacks on Deep Image Classification Models

**Team Name:** DeepMochi  
**Members:** Tse Heng Hsueh (th3448), Sanjana Kosuru (sk11528), Sharmitha Vijayan (sv2877)

## 📌 Overview

This project explores the vulnerability of deep learning models to adversarial attacks. We target a pretrained **ResNet-34** model (ImageNet-1K) and evaluate various attack methods:

- **Fast Gradient Sign Method (FGSM)**
- **Projected Gradient Descent (PGD)**
- **Patch-based Attacks** (Targeted and Untargeted)

We further analyze the **transferability** of these adversarial examples to a different architecture, **DenseNet-121**, assessing both accuracy drop and perturbation imperceptibility.

## 🧪 Methodology

The project was structured into five progressive tasks:

- **FGSM attacks**: Quick, effective baseline but limited transferability.
- **Iterative PGD**: Stronger perturbations with better results.
- **Patch-based attacks**: Localized noise with practical relevance and varying transferability.
- **Targeted vs. Untargeted** comparisons.
- **Transferability analysis** across models.

### Key Hyperparameters:
- Epsilon (ϵ): Perturbation bound
- Alpha (α): Step size for PGD
- Iterations: For PGD and patch tuning

## 🗂 Dataset

- A **subset of 500 images** from 100 ImageNet classes.
- Organized using PyTorch’s `ImageFolder` structure.
- Label mapping provided via `labels_list.json`.

```
/TestDataSet/
├── class1/
│   ├── img1.jpg
├── class2/
│   ├── img2.jpg
└── labels_list.json
```

## ⚙️ Preprocessing & Setup

- **Normalization** (ImageNet standards):  
  `mean = [0.485, 0.456, 0.406]`  
  `std = [0.229, 0.224, 0.225]`

- **Models**:  
  `torchvision.models.resnet34`  
  `torchvision.models.densenet121`

- **Device**:  
  Automatically uses GPU if available.

## 📊 Evaluation Metrics

- **Top-1 and Top-5 Accuracy**
- **L∞ Norm Monitoring** (perturbation compliance)
- **Transferability Success Rate**
- **Visualizations** of:
  - Original vs. Adversarial images
  - Patch difference maps

## 🔍 Key Findings

- **FGSM**: Fast but weak in transfer settings.
- **PGD**: Strong and stealthy, especially with tuned α and steps.
- **Patch Attacks**:
  - Central vs. Random placement affects outcomes.
  - Targeted patches transfer better but are harder to optimize.
- **Transferability is not guaranteed**: Architecture and evaluation logic are crucial.
- **Visualization and debugging** helped resolve dataset filtering bugs that initially skewed results.

## 📈 Example Results

```
Top-1 Accuracy (ResNet): 65.2%
Top-5 Accuracy (ResNet): 89.2%
Top-1 Accuracy (DenseNet): 50.3% (after attack)
```

## 📦 Requirements

- Python 3.7+
- torch
- torchvision
- numpy
- json
- matplotlib (optional for visualization)

Install using:

```bash
pip install torch torchvision numpy matplotlib
```

## 📚 Citations

1. Goodfellow, I. J., Shlens, J., & Szegedy, C. (2014). Explaining and Harnessing Adversarial Examples. [arXiv:1412.6572](https://arxiv.org/abs/1412.6572)  
2. PyTorch Models: [https://pytorch.org/vision/main/models.html](https://pytorch.org/vision/main/models.html)  
3. ImageNet Dataset: [https://www.image-net.org/](https://www.image-net.org/)

## 🏁 Conclusion

This project demonstrates the susceptibility of modern CNN architectures to both simple and advanced adversarial attacks, reinforcing the need for robust evaluation pipelines and transfer-aware defenses in real-world systems.
