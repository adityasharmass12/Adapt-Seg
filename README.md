# 🚀 AdaptSeg – Offroad Semantic Segmentation
### 🧠 Duality AI Offroad Scene Understanding | XƎN-O-THON Project

> *Building intelligent vision systems that understand complex off-road environments.*

---

## 📌 Overview
**AdaptSeg** is a deep learning-based semantic segmentation project designed to understand and classify off-road scenes.  
The model performs **pixel-level classification** to identify terrain, vegetation, obstacles, and ground clutter.

Developed during **XƎN-O-THON Hackathon** by team **DevErrors**.

---

## 🎯 Objective
- Perform semantic segmentation on off-road images  
- Improve model performance using transformer-based architecture  
- Optimize training for speed, memory, and accuracy  

---

## 🧠 Model & Approach

### 🔹 Model Used
- **DINOv2 ViT-S/14 (Vision Transformer)**  
  - Efficient and fast transformer-based feature extractor  
  - Strong visual understanding capability  

---

### 🔹 Key Techniques
- Transformer-based feature extraction  
- Custom segmentation classifier  
- AdamW optimizer for better convergence  
- Image size optimization to prevent memory overflow  
- Feature caching for faster training  

---

## ⚙️ Tech Stack
- Python  
- PyTorch  
- Torchvision  
- CUDA (GPU Acceleration)  
- OpenCV  
- Ultralytics  
- tqdm  

---

## 🛠️ Installation & Setup

```bash
# Clone the repository
git clone https://github.com/your-username/AdaptSeg.git

# Navigate to project folder
cd AdaptSeg

# Create virtual environment
python -m venv venv

# Activate environment
source venv/bin/activate   # Linux/Mac
venv\Scripts\activate      # Windows

# Install dependencies
pip install -r requirements.txt
