# Car License Plate OCR – Template Matching vs CNN (Part 4)

This project focuses on the **Optical Character Recognition (OCR)** component of a broader "Moving Car License Plate Reading" system.  
I implemented and compared two OCR methods to recognize segmented characters from car license plates: **Template Matching** and **Convolutional Neural Networks (CNN)**.

---

# My Contribution – Part 4: Optical Character Recognition

In this part, I focused on recognizing alphanumeric characters from segmented license plate images provided by previous processing steps (Part 3).  
I implemented two distinct approaches and evaluated their performance:

---

## Method 1 – Template Matching

This traditional method matches segmented character images with a set of predefined templates (A–Z, 0–9) using correlation.

### Steps:
1. Created binary template images for each character (A–Z, 0–9)
2. Compared each segmented character using correlation with all templates
3. Selected the best match based on maximum correlation
4. Compared predictions with ground truth labels to evaluate accuracy

### Result:
- **Accuracy**: 52.17%
- **Challenges**: Poor performance under noise, variable lighting, and font variations  
- **Pros**: Fast and light on computation  
- **Cons**: Extremely sensitive to distortion and alignment

---

## Method 2 – CNN with TensorFlow (Deep Learning)

To improve accuracy, I implemented a CNN model using TensorFlow and Keras.

### Model Overview:
- Architecture: 3 Convolutional layers + MaxPooling + Dense + Softmax
- Input: Grayscale segmented character images (e.g., 32x32)
- Optimizer: Adam  
- Loss: Sparse categorical cross-entropy  
- Data Augmentation: rotation, shift, shear, zoom

### Training Pipeline:
1. Preprocessed segmented characters from dataset ([Roboflow dataset](https://universe.roboflow.com/search?q=license+plate+numbe+image+dataset))
2. Augmented training data for generalization
3. Trained CNN on character images and evaluated on test set

### Result:
- **Accuracy**: 96.95%
- **Loss**: ~12%
- **Strengths**: Robust to noise, rotation, lighting variation
- **Limitations**: Requires more computation and larger labeled datasets

---

## Final Comparison

| Method           | Accuracy | Notes |
|------------------|----------|-------|
| Template Matching | 52.17%   | Fast but sensitive to distortion |
| CNN (TensorFlow) | 96.95%   | Highly robust, ideal for deployment |

---

## Conclusion

After testing both methods, the CNN model was clearly superior in terms of recognition accuracy and robustness.  
Therefore, the **CNN method was selected as the final OCR solution** for this project.

---

## Future Work

- Improve CNN accuracy by adding more training data
- Resolve character confusion cases (e.g., "B" vs "R", "1" vs "I")
- Try other architectures (e.g., ResNet) and better loss functions

---

## Code Demo Video

[![Watch on YouTube](https://img.shields.io/badge/YouTube-Demo-red?logo=youtube)](https://www.youtube.com/watch?v=YGx4TaSjJnw)

---

**Lee Gyumin (이규민)**  
HKUST ECE, ELEC4130 – Machine Learning on Images  
Email: [gleeag@connect.ust.hk]  
