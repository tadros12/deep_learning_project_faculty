# Arabic Handwritten Character Recognition (AHCD)

This project performs a comparative study of Deep Learning architectures for classifying Arabic handwritten characters using the **AHCD Dataset** (16,800 images).

## 📊 Project Overview
Arabic OCR is challenging due to the cursive nature of the script. We evaluated four architectures to determine the impact of **input resolution** and **transfer learning** on accuracy.

| Model | Type | Input Size | Accuracy | Observation |
|-------|------|------------|----------|-------------|
| **InceptionV3** | Transfer Learning | **75x75** (Upscaled) | **~80%** | 🏆 **Best Performer** |
| ResNet50 | Transfer Learning | 32x32 | ~54% | Suffered from spatial information loss |
| MobileNetV2 | Transfer Learning | 32x32 | ~42% | Efficient but low accuracy on small inputs |
| VGG-19 | Custom (Scratch) | 32x32 | 3.5% | ❌ Failed (Vanishing Gradient) |

## 🧠 Methodology
1.  **Data Preprocessing:**
    * Images normalized to `[0, 1]`.
    * **Adapter Layer:** Learned `Conv2D` layer to convert Grayscale (1 channel) to RGB (3 channels) for pre-trained models.
    * **Upscaling:** InceptionV3 used a `Resizing` layer to convert 32x32 $\to$ 75x75.
2.  **Training:**
    * Optimizer: Adam
    * Loss: Categorical Crossentropy
    * Monitoring: TensorBoard

## 📂 Project Structure
```text
├── data/               # Dataset (GitIgnored)
├── notebooks/          # Jupyter Notebooks for training
├── models/             # Saved Keras models (GitIgnored)
├── logs/               # TensorBoard logs
├── doc/                # LaTeX Documentation & Report
└── README.md           # Project Documentation
