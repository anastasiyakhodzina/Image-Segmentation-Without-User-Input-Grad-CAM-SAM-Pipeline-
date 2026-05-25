# Grad-CAM & SAM

In this project I implemented Grad-CAM – a method for producing heatmaps of regions that are most relevant to a model and designed a pipeline that takes only an image and outputs a segmentation of particular shape.


The project demonstrates how to automate image segmentation with:

1.  **Classifier:** A ResNet-18 model classifies shapes.
2.  **Grad-CAM:** Generates heatmaps to localize the object.
3.  **Prompt Extraction:** Automatically finds foreground (and background in the second approach) points based on heatmap intensity.
4.  **SAM (Segment Anything Model):** Uses these points to generate high-quality segmentation masks.
## Fast Replication (Google Colab)

You can reproduce the experiments, training, and evaluation directly in your browser using Google Colab.

[Open In Colab](https://colab.research.google.com/drive/166sEy-j3mqDPOAsaMsxgawVbpRdMcSxS?usp=sharing)

---

## Approximate Runtime

The code is optimized to run quickly on standard cloud GPUs.

* **Device:** T4 GPU (Standard Colab Free Tier).
* **Total Execution Time:** ~10-20 minutes for the whole code.

---

## Expected Outputs

Upon successful execution of the notebook, the following assets and metrics will be generated:

### 1. Training Visualization
* Visualization of the classifier training process.

### 2. Visualizations
* **Grad-CAM Heatmaps:** Overlays showing where the model "looks".
* **SAM Segmentation Masks:** Comparisons between the Input Image, Basic SAM Predicted Mask, and Ground Truth.
* **Segmentation mask generated with the help of implemented two approaches**

### 3. Evaluation Metrics
The pipeline is evaluated on the test set  reporting:

* **Hit Rate:** how often generated foreground points fall inside the ground-truth mask .
* **Distance:** distance from the center of mass of the ground-truth mask to generated foreground points.
* **IoU (Intersection over Union):** The overall quality of the segmentation.

---

##  Resource Requirements

### Hardware
* **GPU:** Strongly recommended (NVIDIA T4 or better).
* **RAM:** 8 GB minimum.

### Software & Dependencies
* **Python:** 3.8+
* **Key Libraries:** `torch`,  `numpy`, `cv2`, `matplotlib.pyplot`, `os`, `random`, `PIL.Image`, `scipy.ndimage`, `torchvision`, `tqdm`, `segment-anything`.