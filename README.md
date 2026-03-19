# AdaptSeg – Offroad Semantic Segmentation

## Overview
AdaptSeg is a deep learning project focused on semantic segmentation of off-road environments.  
It uses a transformer-based model (DINOv2) to classify each pixel in an image into meaningful categories such as terrain, vegetation, and obstacles.

---

## Objective
- Perform pixel-level classification on off-road images  
- Improve segmentation performance using transformer-based models  
- Optimize training for speed, memory, and accuracy  

---

## Environment and Dependencies

### System Requirements
- Python 3.8+
- GPU (recommended: NVIDIA RTX series with CUDA support)
- Linux or Windows

### Required Libraries
Install dependencies using:

```bash
pip install torch torchvision pytorch-cuda opencv-contrib-python tqdm ultralytics ultralytics-thop
