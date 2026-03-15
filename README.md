# End-to-end PASCAL VOC Object Detection with Faster R-CNN

This repository marks a significant personal milestone: **my first ever end-to-end deep learning pipeline**. From data ingestion to training and real-world testing, I have built every component of this object detection system using the **Faster R-CNN** architecture with a **MobileNetV3-Large** backbone.

---

## Video Demo

Click the images below to watch the model in action on various video samples:

<div align="center">
  <a href="https://www.youtube.com/watch?v=hdipd4-nzAM">
    <img src="https://img.youtube.com/vi/hdipd4-nzAM/0.jpg" alt="Video Demo 1" style="width:45%;">
  </a>
  <a href="https://www.youtube.com/watch?v=KT_-X-a4BnE">
    <img src="https://img.youtube.com/vi/KT_-X-a4BnE/0.jpg" alt="Video Demo 2" style="width:45%;">
  </a>
</div>

---

## Detection Samples

Below are some example predictions on the PASCAL VOC test set:

<div align="center">
  <img src="demo/1.png" width="45%"> <img src="demo/2.png" width="45%">
  <br>
  <img src="demo/3.png" width="45%"> <img src="demo/4.png" width="45%">
</div>

---

## The Pipeline Breakdown

This project consists of a complete workflow, developed entirely from scratch to handle object detection tasks.

### 1. Custom Dataset Management (`voc_dataset.py`)
* **Inheritance & Customization**: I inherited from the standard `VOCDetection` class and built a new dataset class tailored to specific requirements.
* **Label Mapping**: Implemented custom logic to map XML annotations to integer labels across the 20 PASCAL VOC categories.

### 2. Professional Training Engine (`train_fasterrcnn.py`)
I developed a fully featured training script designed with industry-standard practices:
* **Custom Architecture**: Modified the Faster R-CNN model's box predictor to match the specific number of classes for the VOC dataset.
* **Professional UI**: Integrated `tqdm` progress bars for a clean and informative terminal output during training and validation.
* **Advanced Configuration**: Wrote a robust `get_args` function using `argparse` for easy hyperparameter tuning and model management.
* **Experiment Tracking**: Integrated **TensorBoard** to monitor real-time loss curves and performance metrics.
* **Evaluation Metrics**: Utilized `torchmetrics` to calculate the **Mean Average Precision (mAP)**, ensuring precise performance tracking.
* **Data Augmentation**: Implemented a comprehensive augmentation pipeline (RandomAffine, ColorJitter) to enhance model robustness.
* **Persistence**: Built complete logic for saving the **best** and **last** model checkpoints and resuming training from existing weights.

### 3. Dedicated Inference Scripts
* **Image Testing (`test_image_fasterrcnn.py`)**: A custom script for processing static image inputs and saving the predicted bounding boxes.
* **Video Testing (`test_video_fasterrcnn.py`)**: A custom script designed to process video files frame-by-frame and export a result video with real-time detections.

---

## Training Results (TensorBoard)

Below is the visualization of the model learning process:

![TensorBoard Results](demo/9.jpg)

---
