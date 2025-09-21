# P&ID Symbol Detection with YOLOv5

This project uses YOLOv5 to detect symbols in Piping and Instrumentation Diagrams (P&IDs). It can identify various engineering symbols commonly found in industrial diagrams, making it useful for automating the interpretation of technical drawings.

![P&ID Detection Example](data/instrumentationtools.com_piping-and-instrumentation-diagram.jpg)

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Directory Structure](#directory-structure)
- [Setup & Installation](#setup--installation)
- [Usage](#usage)
- [Model Training](#model-training)
- [Inference](#inference)
- [Results](#results)
- [Customization](#customization)
- [Troubleshooting](#troubleshooting)
- [Acknowledgements](#acknowledgements)

## 🔍 Overview

This project implements an object detection system specialized for P&ID diagrams using the YOLOv5 architecture. P&ID diagrams are complex technical drawings used in process engineering that contain various standardized symbols. This tool can automatically identify and locate these symbols, which is useful for:

- Digitizing paper diagrams
- Automating diagram analysis
- Extracting engineering data from drawings
- Quality control and verification

## ✨ Features

- **Symbol Detection**: Identifies various P&ID symbols with high accuracy
- **Pretrained Model**: Includes a pretrained model for immediate use
- **Custom Training**: Supports training on custom P&ID datasets
- **Windows Compatible**: Fully compatible with Windows environments
- **Easy Setup**: Simple installation and configuration
- **Interactive Notebook**: Jupyter notebook for easy experimentation

## 📁 Directory Structure

```
predict/
├── data/                 # Sample P&ID diagrams for testing
├── dataset/              # Downloaded dataset for training
│   ├── images/           # Training images
│   ├── labels/           # Training labels
│   └── best.pt           # Pre-trained model
├── model/                # Storage for trained models
├── pid_preds/            # Storage for prediction results
├── result/               # Output directory for predictions
├── yolov5/               # YOLOv5 repository (cloned)
├── yolov5_p&ids.ipynb    # Main Jupyter notebook
├── requirements.txt      # Python dependencies
└── README.md             # This documentation
```

## 🚀 Setup & Installation

### Prerequisites

- Python 3.8 or later
- Git (optional, for cloning YOLOv5)
- CUDA-compatible GPU (optional, for faster processing)

### Installation

1. Clone this repository:
   ```
   git clone https://github.com/yourusername/pid-detection.git
   cd pid-detection
   ```

2. Install dependencies:
   ```
   pip install -r requirements.txt
   ```

3. Run the Jupyter notebook:
   ```
   jupyter notebook yolov5_p&ids.ipynb
   ```

4. Follow the cells in the notebook for setup, training, and inference

## 🛠️ Usage

The project is organized as a Jupyter notebook with cells for different stages of the workflow:

1. **Cell 1**: Setup YOLOv5 (clones repository and installs dependencies)
2. **Cell 2**: Download P&ID dataset
3. **Cell 3**: Extract dataset files
4. **Cell 4**: Verify setup and (optionally) start training
5. **Cell 5**: Run inference on P&ID diagrams
6. **Training Verification Cell**: Verify training results and manage models

## 🏋️ Model Training

The model is trained on a dataset of P&ID symbols with annotations. To train the model:

1. Run Cell 1-3 to set up YOLOv5 and download the dataset
2. Run Cell 4 and uncomment the training line to start training
3. Training parameters can be adjusted in the `start_yolov5_training()` function
4. Training progress will be displayed in real-time
5. Models are saved to `runs/train/pid_experiment/weights/`

Training typically takes 1-4 hours depending on your hardware. With a GPU, it will be significantly faster.

## 🔮 Inference

To run inference on P&ID diagrams:

1. Place your P&ID diagram in the `data/` directory
2. Update the `test_image` path in Cell 5 if needed
3. Run Cell 5 to perform inference
4. Results will be saved to `runs/detect/pid_test/`

The inference results include:
- Annotated images with bounding boxes
- Text files with detection coordinates
- Confidence scores for each detection

## 📊 Results

The model can detect various P&ID symbols including:
- Valves (Gate, Globe, Check, etc.)
- Pumps and Compressors
- Instruments and Meters
- Vessels and Tanks
- Heat Exchangers
- Control Devices

Detection results are saved in the `runs/detect/pid_test/` directory. Each image will have corresponding text files with detection coordinates and class IDs.

## ⚙️ Customization

### Model Customization

- You can adjust inference parameters in Cell 5:
  - `--conf`: Confidence threshold (default: 0.25)
  - `--iou`: IoU threshold (default: 0.45)
  - `--img`: Input image size (default: 640)

### Training Customization

- You can modify training parameters in Cell 4:
  - Batch size
  - Epochs
  - Image size
  - Base model (YOLOv5s, YOLOv5m, YOLOv5l, YOLOv5x)

### Visualization Customization

- The visualization parameters (box thickness, text size) can be customized in the `customize_visualization()` function

## 🔧 Troubleshooting

### Common Issues

1. **YOLOv5 Setup Fails**:
   - Ensure you have Git installed
   - Try manual download from https://github.com/ultralytics/yolov5

2. **Dataset Download Fails**:
   - Check your internet connection
   - Try downloading directly from https://github.com/ch-hristov/p-id-symbols

3. **Training Errors**:
   - Ensure PyTorch is correctly installed
   - Check CUDA compatibility if using GPU

4. **Inference Issues**:
   - Verify model path is correct
   - Ensure input image exists and is accessible

## 🙏 Acknowledgements

- [Ultralytics YOLOv5](https://github.com/ultralytics/yolov5) for the object detection framework
- [P&ID Symbols Dataset](https://github.com/ch-hristov/p-id-symbols) for the training data
- All contributors to the open-source libraries used in this project

---

*For issues, contributions, or questions, please open an issue on GitHub.*