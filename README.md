# Microsoft-SAP Human Pose Estimation

A Computer Vision and Deep Learning project that detects human body keypoints and estimates human posture from images and videos using Python, OpenCV, and a pretrained TensorFlow-format deep learning model.

## Overview

Human Pose Estimation is a computer vision technique used to identify and locate important human body landmarks, such as the nose, shoulders, elbows, wrists, hips, knees, and ankles.

This project implements an OpenPose-style human pose estimation pipeline using a pretrained neural network. It processes images and video frames, detects body keypoints, and connects them to generate a visual representation of the human skeleton.

The project also includes a Streamlit-based web application that allows users to upload images, adjust detection confidence thresholds, and visualize the estimated human pose.

## Features

- **Human Keypoint Detection:** Detects 18 major human body landmarks.
- **Skeleton Visualization:** Connects detected body joints using lines and circles.
- **Image Processing:** Estimates human posture from static images.
- **Video Processing:** Performs pose estimation on individual video frames.
- **Interactive Web Interface:** Provides an image-upload interface using Streamlit.
- **Adjustable Confidence Threshold:** Allows users to control the minimum confidence required for accepting detected keypoints.
- **Pretrained Deep Learning Model:** Uses a TensorFlow-format frozen model loaded through OpenCV's DNN module.

## Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| OpenCV | Image processing, video processing, and model inference |
| NumPy | Numerical computations and image arrays |
| TensorFlow-format model | Pretrained human pose estimation network |
| Streamlit | Interactive web application |
| Pillow (PIL) | Image loading and handling |
| Matplotlib | Imported in the standalone scripts |

## Project Architecture

The project follows this processing pipeline:

1. **Input:** An image or video frame is provided.
2. **Preprocessing:** The input image is resized and normalized using OpenCV's `blobFromImage()`.
3. **Model Inference:** The pretrained neural network processes the image.
4. **Heatmap Generation:** The network generates heatmaps for different body landmarks.
5. **Keypoint Extraction:** The maximum-confidence location of each body-part heatmap is identified using `cv2.minMaxLoc()`.
6. **Coordinate Mapping:** Heatmap coordinates are converted into the original image dimensions.
7. **Confidence Filtering:** Keypoints below the specified confidence threshold are discarded.
8. **Skeleton Construction:** Detected joints are connected using predefined body-part pairs.
9. **Output:** The resulting image or video frame displays the estimated human skeleton.



## Body Keypoints

The implementation uses 18 human body landmarks and one background channel.

| Index | Body Part |
|---|---|
| 0 | Nose |
| 1 | Neck |
| 2 | Right Shoulder |
| 3 | Right Elbow |
| 4 | Right Wrist |
| 5 | Left Shoulder |
| 6 | Left Elbow |
| 7 | Left Wrist |
| 8 | Right Hip
