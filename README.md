# Pixel Coordinate Prediction using CNN

## Overview
This project solves a pixel localization problem using Deep Learning.  
Given a **50×50 grayscale image** where **exactly one pixel has intensity 255** and all others are 0, the goal is to **predict the (x, y) coordinates** of that pixel.

A **fully convolutional neural network (CNN)** is used to generate a **pixel-wise heatmap**, and the final coordinates are extracted using an `argmax` operation.

The focus of this assignment is on **approach, clarity, and correctness**, rather than model complexity.

---

## Problem Statement
- Input: 50×50 grayscale image
- Condition: Exactly one pixel has value 255, all others are 0
- Output: (x, y) coordinates of the pixel with value 255

---

## Approach
1. **Dataset Generation**
   - A synthetic dataset is generated programmatically.
   - Each image contains exactly one active pixel (value = 255).
   - All 2500 possible pixel locations are covered (50×50).
   - Labels are stored as pixel coordinates in a CSV file.

2. **Model Architecture**
   - A simple **fully convolutional CNN** is used.
   - No pooling layers are applied to preserve spatial precision.
   - The model outputs a **50×50 heatmap** representing pixel likelihoods.

3. **Prediction**
   - The predicted pixel location is obtained using `argmax` on the heatmap.
   - This avoids direct coordinate regression and preserves spatial structure.

4. **Evaluation**
   - Dataset split: 80% Train / 10% Validation / 10% Test
   - Metrics: Binary Crossentropy Loss, Accuracy
   - Visual comparisons between ground truth and predictions are saved.

---

## Model Architecture

- **Input:** 50×50×1 grayscale image  
- **Conv2D:** 16 filters, 3×3 kernel, ReLU  
- **Conv2D:** 32 filters, 3×3 kernel, ReLU  
- **Conv2D:** 1 filter, 1×1 kernel, Linear  
- **Output:** 50×50×1 heatmap  

This architecture is intentionally minimal and sufficient for the task.

---

## Results
- The model converges quickly due to the deterministic nature of the data.
- Training, validation, and test accuracy reach 100%.
- Loss decreases smoothly without divergence.
- Sample visualizations show perfect alignment between predicted and ground truth coordinates.

All plots and sample outputs are saved in the `results/` directory.

---

## Dependencies

All required dependencies are listed in `requirements.txt`.

## Installation
```bash
pip install -r requirements.txt
```

---

## How to Run
1. Install dependencies using the command above
2. Open notebook.ipynb
3. Run all cells sequentially
4. Generated datasets, graphs, visualizations and the trained model will be saved automatically.

---

## Notes
- The dataset is noise-free and deterministic; perfect accuracy is expected.
- The simplicity of the model is intentional and aligns with the evaluation criteria.
- The project demonstrates a clean and explainable approach to pixel localization.
