## Surface EMG-Based Hand Gesture Recognition (CNN–LSTM)

This project implements a **surface electromyography (sEMG) based hand gesture recognition system** using the publicly available **NinaPro DB1 dataset**.  
It is adapted from the research paper:  
*A Surface Electromyography Based Hand Gesture Recognition Framework Leveraging Variational Mode Decomposition Technique and Deep Learning Classifier*.  

Instead of Variational Mode Decomposition (VMD), this implementation uses **Raw EMG + Overlap Segmentation + CNN–LSTM** to achieve high accuracy on a realistic dataset.

---

## Project Overview
- **Goal:** Classify 10 hand gestures from sEMG signals.
- **Dataset:** NinaPro DB1 (10 sEMG channels, 10 gestures + rest).
- **Model:** CNN–LSTM hybrid.
- **Accuracy:** ~88% validation accuracy.
- **Key Advantage:** Works with noisy, multi-subject public dataset.

---

## Dataset
- **Source:** [NinaPro DB1 Dataset](http://ninapro.hevs.ch/)
- **Channels:** 10 sEMG channels.
- **Gestures:** 10 gestures (selected from dataset).
- **Sampling rate:** 100 Hz.
- **Structure:**
  - `.mat` files for each subject and session.
  - EMG signals + gesture labels.

---

## Methodology
1. **Data Acquisition**
   - Loaded `.mat` files for multiple subjects.
2. **Preprocessing**
   - Segmentation: 500 samples/window (~250 ms), **50% overlap**.
   - Normalization: StandardScaler applied per channel.
3. **Data Augmentation**
   - Gaussian noise addition.
   - Amplitude scaling.
   - Time shifting.
4. **Model Architecture**
   - **CNN layers** for feature extraction.
   - **LSTM layer** for temporal modeling.
   - **Dense layers + Softmax** for gesture classification.
5. **Training**
   - Optimizer: Adam.
   - Loss: Categorical Crossentropy.
   - Regularization: Dropout, Batch Normalization, Early Stopping.
6. **Evaluation**
   - Validation accuracy ~88%.
   - Confusion matrix shows strong classification across gestures.

---

## Results
- **Validation Accuracy:** ~88%
- **Training Accuracy:** ~94%
- **Loss:** Validation loss ~0.44
- **Observations:**
  - Strong diagonal in confusion matrix.
  - Minor confusion between similar gestures (e.g., G4 vs G5).

---

## Technologies Used
- **Languages:** Python
- **Libraries/Frameworks:**
  - TensorFlow / Keras
  - NumPy, Pandas
  - SciPy
  - scikit-learn
  - Matplotlib, Seaborn
- **Dataset:** NinaPro DB1

---

## Future Work
-Test on additional datasets (NinaPro DB2, DB5).
-Explore Transformer-based architectures (TraHGR).
-Real-time implementation using low-latency inference.

---

## Author
**Apoorv Gupta**
