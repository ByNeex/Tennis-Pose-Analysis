# Pose Estimation and Kinematic Analysis: Application to Tennis

![Python](https://img.shields.io/badge/Python-3.x-blue?style=flat&logo=python)
![MMPose](https://img.shields.io/badge/MMPose-OpenMMLab-red?style=flat)
![Colab](https://img.shields.io/badge/Google_Colab-Compatible-orange?style=flat&logo=google-colab)

This project was developed as part of our **Double B.Sc. in Mathematics and Computer Science**. It aims to analyze the biomechanics of a tennis forehand stroke using computer vision (Human Pose Estimation) and kinematic analysis techniques.

## Authors
- **Bastien BABU**
- **Jérémy CLAUX**
- **Pierre PARODI**
- **David QASSEMYAR**

---

## Project Overview

The goal is to extract accurate biomechanical data from a standard video of a tennis player, then model the motion to analyze speed and predict the future trajectory of the arm.

### Key Features:
1. **Human Pose Estimation:** Leveraged the **HRNet** (High-Resolution Net) model via the MMPose library to detect 17 anatomical keypoints.
2. **Kinematic Analysis:**
   * Computation of wrist velocity and acceleration.
   * 2D trajectory visualization.
   * Data smoothing using a moving average filter to reduce inference noise.
3. **Trajectory Prediction:** Explored forecasting future arm motion using a Recurrent Neural Network (**LSTM**).

### Technical Choices:
- **Model Selection:** Prioritized **HRNet** on CPU for its high spatial precision and robustness to occlusions, after experimenting with *RTMPose* (whose GPU implementation proved unstable in our environment).
- **Data Processing:** Frame-by-frame processing to ensure stable kinematic computations.

---

## Installation & Usage

This project was designed to run on **Google Colab** to simplify managing complex `mmcv` and `mmpose` dependencies.

### Running the Project:
1. Open the main notebook: `notebooks/main_analyse_hrnet.ipynb`.
2. Click the "Open in Colab" badge (if hosted on GitHub).
3. Run the cells sequentially. The script automatically handles the installation of `mmpose`, `mmdet`, and `mmcv-lite`.

### Repository Structure:
- `notebooks/main_analyse_hrnet.ipynb`: Complete pipeline (environment setup, inference, graphical analysis, LSTM).
- `notebooks/experiments/`: Experimental setups and GPU model attempts (RTMPose).
- `report/`: Full project report in PDF format with detailed explanations.

---

## Results

Successfully achieved:
- Generated a smooth skeletal overlay of the player in motion.
- Plotted the wrist velocity curve (capturing the forehand "loop").
- Identified the limitations of 2D analysis (perspective distortion skewing certain joint angles).

> See the [Full Report](report/Rapport_Estimation_Pose.pdf) for detailed plots and mathematical explanations.

---

## Tech Stack
- **Python**
- **OpenMMLab** (MMPose, MMCV, MMDet, HRNet)
- **OpenCV** (Video processing)
- **Matplotlib** (Data visualization)
- **TensorFlow / Keras** (LSTM model)
