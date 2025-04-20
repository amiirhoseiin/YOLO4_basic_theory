# YOLOv4 Object Detection on Google Colab with Darknet

This project sets up YOLOv4 (You Only Look Once version 4) on Google Colab using the Darknet framework. It provides a step-by-step guide for configuring the environment, enabling GPU acceleration, and preparing the model for training or inference.

## ✨ Why This Project Matters

YOLOv4 is a powerful real-time object detection model widely used in computer vision tasks such as surveillance, traffic monitoring, medical imaging, and more. This project simplifies the process of running YOLOv4 by leveraging Google Colab's free GPU environment and streamlining setup using Google Drive integration. It’s an ideal starting point for students, researchers, and developers working on deep learning and object detection projects.

## 🧠 What's Inside the Notebook?

The notebook (`codee.ipynb`) includes:
- Mounting Google Drive to save data and results persistently
- Cloning and compiling the Darknet repository
- Enabling necessary features like GPU, OpenCV, cuDNN, and Half Precision
- Preparing the environment for training a custom object detection model using YOLOv4

## ⚙️ Setup Instructions (Colab)

1. **Mount your Google Drive**
   ```python
   from google.colab import drive
   drive.mount('/content/drive')
   ```

2. **Navigate to your working directory in Google Drive**
   ```python
   %cd /content/drive/MyDrive/Dataforproject/projrct
   ```

3. **Clone the YOLOv4 Darknet repository**
   ```bash
   !git clone https://github.com/AlexeyAB/darknet.git
   %cd darknet
   ```

4. **Configure the build settings**
   Update the `Makefile` to enable all necessary options:
   ```bash
   !sed -i 's/OPENCV=0/OPENCV=1/' Makefile
   !sed -i 's/GPU=0/GPU=1/' Makefile
   !sed -i 's/CUDNN=0/CUDNN=1/' Makefile
   !sed -i 's/CUDNN_HALF=0/CUDNN_HALF=1/' Makefile
   ```

5. **Compile Darknet**
   ```bash
   !make
   ```

6. **Test the compiled binary**
   ```bash
   !./darknet
   ```

## 🧪 Example Use Case

While this notebook sets up the environment, the next steps typically include:

- Preparing a dataset in YOLO format
- Adjusting YOLO configuration files (like `.cfg`, `.names`, `.data`)
- Training the model using your dataset:
  ```bash
  !./darknet detector train data/obj.data cfg/yolov4-custom.cfg yolov4.conv.137
  ```
- Running inference on new images or videos

These steps can be added or customized based on your specific detection task.

## 🧾 License

This project uses [AlexeyAB's Darknet](https://github.com/AlexeyAB/darknet) under the original license terms.
