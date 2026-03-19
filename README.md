#  AdaptSeg: Off-Road Semantic Scene Segmentation

##  About the Project

AdaptSeg is a deep learning-based project focused on understanding complex off-road environments through **semantic segmentation**. Unlike basic image classification, this project assigns a label to every pixel in an image, allowing the model to distinguish between terrain, vegetation, obstacles, and other elements present in outdoor scenes.

The goal of this project is to build an intelligent system capable of interpreting real-world environments, which can be applied in areas such as autonomous navigation, robotics, and off-road path analysis.

What makes this project powerful is the use of a **Vision Transformer (DINOv2)** combined with a custom segmentation head, enabling both global understanding and efficient prediction.

---

##  How It Works

The model follows a simple but effective pipeline:

Input Image → DINOv2 Feature Extraction → Segmentation Head → Output Mask

Instead of directly learning from raw pixels, the model first extracts meaningful features using a transformer-based backbone and then converts those features into a segmentation map.

---

##  Model Architecture

The system consists of two main components:

###  DINOv2 Backbone (ViT-S/14)
- A transformer-based architecture
- Captures global relationships in images
- Outputs feature tokens instead of convolution maps
- Used in frozen mode to improve efficiency

###  Segmentation Head
- A lightweight CNN-based module
- Converts transformer features into spatial feature maps
- Produces pixel-wise class predictions

---

##  Dataset Structure

The dataset is organized as follows:

dataset/
 ├── train/
 │    ├── Color_Images/
 │    ├── Segmentation/
 ├── val/
      ├── Color_Images/
      ├── Segmentation/

Each image has a corresponding segmentation mask.

---

##  Data Processing

Before feeding images into the model:

- Images are resized to 448 × 896
- Normalized using ImageNet statistics
- Augmented using:
  - Random Horizontal Flip
  - Color Jitter

###  Mask Conversion

Custom pixel values are mapped into class indices:

value_map = {
    0: 0, 100: 1, 200: 2, 300: 3,
    500: 4, 550: 5, 700: 6,
    800: 7, 7100: 8, 10000: 9
}

This ensures consistency during training.

---

##  Training Configuration

- Batch Size: 16
- Learning Rate: 3e-4
- Epochs: 15+
- Image Size: 448 × 896
- Number of Classes: 10

---

##  Loss Function

A combination of two loss functions is used:

Total Loss = 0.5 × CrossEntropy + 0.5 × Dice Loss

- Cross Entropy ensures correct classification
- Dice Loss improves segmentation overlap

---

##  Optimization Strategy

To improve performance, the following techniques were used:

- AdamW optimizer for better generalization
- Frozen backbone to reduce computation
- Efficient feature extraction using DINOv2
- GPU-based training for speed

---

##  Training Process

During training:

1. Images are passed through the DINOv2 backbone
2. Feature tokens are extracted
3. Segmentation head processes the features
4. Output is resized to match original dimensions
5. Loss is computed and backpropagated
6. Best model is saved based on validation performance

---

##  Evaluation & Metrics

###  IoU (Intersection over Union)

IoU measures how well predicted segmentation overlaps with ground truth.

Two approaches were used:
- Basic IoU (pixel accuracy)
- Class-wise mean IoU (more reliable metric)

---

##  Test Time Augmentation (TTA)

To improve prediction accuracy:

- Model runs on original image
- Model runs on horizontally flipped image
- Final output is the average of both predictions

This helps reduce prediction errors.

---

##  Results

- Model performance improved progressively during training
- Best model selected automatically
- Final evaluation based on mean IoU score

---

##  Model Usage

To load the trained model:

model.load_state_dict(torch.load("best_model.pth"))
model.eval()

Inference includes:
- Feature extraction
- Segmentation prediction
- Mask generation

---

##  Dependencies

Install required libraries:

pip install torch torchvision timm opencv-python numpy tqdm pillow

---

##  Challenges Faced

- High memory usage due to large image size
- Training time with transformer-based architecture
- Class imbalance in dataset

---

##  Solutions Implemented

- Used feature extraction instead of full fine-tuning
- Combined Dice and CrossEntropy loss
- Applied data augmentation and TTA
- Optimized training pipeline

---

##  Future Improvements

- Improve IoU score further
- Fine-tune transformer backbone
- Optimize inference speed
- Extend to real-time applications

---

##  Authors

- Tarun 
- Rohit
- Aditya
- Sameer
- Team DevErrors

---

##  Final Thoughts

AdaptSeg demonstrates how modern transformer-based architectures can be applied to solve real-world segmentation problems. By combining efficiency and accuracy, this project highlights the potential of deep learning in understanding complex outdoor environments.

---

⭐ If you found this project interesting, consider giving it a star!
