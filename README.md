# 🐶 Fine-Grained Image Classification: Dog Breeds with Deep CNNs

This project tackles the complex challenge of **fine-grained image classification** by training deep learning models to recognize **120 distinct dog breeds**. Despite achieving strong classification accuracy, the models consistently report **high loss values**, a phenomenon that reflects the difficulty of the task rather than a failure in performance.

---

## 📦 Dataset

- Stanford Dogs Dataset
- 120 classes with high inter-class similarity
- Split strategy: experiments ranged from 80-10-10 to 60-30-10 for better validation stability

---

## 🧠 Models Compared

| Model           | Train Acc | Val Acc | Key Traits                                                                 |
|------------------|-----------|---------|-----------------------------------------------------------------------------|
| MobileNetV2      | ~10%      | ~9%     | Lightweight, underfits fine-grained data                                   |
| EfficientNetB0   | ~40%      | ~36%    | Balanced, benefits from tuning, struggles with subtle class variation      |
| ResNet50         | ~60%      | ~41%    | Strong mid-level features, requires fine-tuning for better generalization  |
| **DenseNet121**  | **99%**   | **60%+**| Dense feature reuse, best generalization, especially with regularization   |

---

## ⚖️ Why Is the Loss High Despite Good Accuracy?

> 🔎 **Validation Accuracy Peaks ~60%, Yet Categorical Crossentropy Loss Stays > 2.5**

This paradox is rooted in:
- **Class Imbalance & Fine-Grained Similarity**: The model becomes less confident in its predictions even when correct
- **L2 Regularization**: Adds penalty to large weights, increasing the reported loss
- **Loss Function Behavior**: Categorical crossentropy heavily penalizes low-confidence predictions
- **Overfitting Pressure**: The model memorizes quickly but struggles to generalize past ~50–60% due to dataset limitations

---

## 🧪 Experiment Strategies

- 🧬 Data Augmentation: Introduced transformations to enrich minority classes
- 🔓 Fine-tuning: Unfroze last 20 layers of DenseNet121
- 🧨 Regularization: L2 regularization (λ=0.001) proved more effective than Dropout
- ⏹ Early Stopping: Preserved peak generalization between Epochs 13–16
- 📊 Metrics tracked: Accuracy, loss, augmentation impact, and optimizer sensitivity

---

## 🚀 How to Run

This project was developed in Google Colab with TensorFlow and Keras.

1. Upload the notebook
2. Prepare a structured dataset directory or use a Kaggle import
3. Modify model saving paths if needed
4. Run cells — models are trained, evaluated, and saved with logs

---

## 🧠 Key Takeaways

- DenseNet121 is best suited for fine-grained tasks due to its feature reuse architecture.
- Regularization techniques improve generalization but increase reported loss.
- You cannot solve 120-class problems with <100 samples/class without advanced augmentation or more data.

---

## 📂 Output Examples

> Include here:
- 📉 Accuracy/Loss curves
- 🐶 Sample predictions with confidence scores
- 🔍 Misclassifications that looked visually similar

---

