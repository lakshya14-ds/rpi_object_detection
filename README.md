# 🍓 Raspberry Pi Real-Time Object Detection & Tracking

<p align="center">

![Platform](https://img.shields.io/badge/Platform-Raspberry%20Pi-C51A4A?logo=raspberrypi&logoColor=white)
![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB?logo=python&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-4.x-5C3EE8?logo=opencv&logoColor=white)
![YOLO](https://img.shields.io/badge/YOLO-Ultralytics-00FFFF)
![TensorFlow Lite](https://img.shields.io/badge/TensorFlow-Lite-FF6F00?logo=tensorflow&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)

</p>

A collection of **Computer Vision** applications built for **Raspberry Pi** using **OpenCV**, **TensorFlow Lite**, and **Ultralytics YOLO** to perform **real-time object detection, face detection, motion detection, and object tracking**.

Although optimized for Raspberry Pi 4/5, every module can also run on **Linux**, **Ubuntu**, and **macOS** with any USB webcam.

This repository serves as a practical toolkit for learning **Edge AI**, **Computer Vision**, and **Embedded Machine Learning**.

---

# ✨ Features

✔ Real-time camera streaming

✔ Face Detection

✔ Motion Detection

✔ TensorFlow Lite Object Detection

✔ YOLO Object Detection

✔ Color-based Object Tracking

✔ Feature-based Tracking

✔ Shape Detection & Tracking

✔ Modular project structure

✔ Raspberry Pi & Desktop compatible

---

# 📸 Demo

> Add screenshots or GIFs inside the **images/** folder.

```
images/
│── camera_test.gif
│── face_detection.png
│── motion_detection.gif
│── yolo_detection.gif
```

Example:

```markdown
![YOLO Demo](images/yolo_detection.gif)
```

---

# 📦 Modules

| Module | Description |
|---------|-------------|
| 📷 camera-test | Verifies camera connection and streams video. |
| 🙂 face-detection | Detects faces using Haar Cascade or DNN. |
| 🏃 motion-detection | Detects moving objects using background subtraction. |
| 🤖 object-detection-tflite | Lightweight TensorFlow Lite object detection. |
| 🧠 object-detection-yolo | High-accuracy object detection using Ultralytics YOLO. |
| 🎨 object-tracking-color | HSV color-based object tracking. |
| 🧩 object-tracking-feature | ORB/SIFT feature tracking. |
| 🔷 object-tracking-shape | Contour and geometric shape tracking. |
| 🛠 utils | Shared helper utilities. |

---

# 🧰 Hardware Requirements

- Raspberry Pi 4 (2GB+)
- Raspberry Pi 5 (Recommended)
- Raspberry Pi Camera Module
- USB Webcam
- Raspberry Pi OS Bookworm (64-bit)
- Active cooling (recommended)

Desktop users only need:

- Linux
- Ubuntu
- macOS
- USB webcam

---

# 📂 Project Structure

```text
rpi_object_detection/
│
├── images/
│
├── src/
│   ├── camera-test/
│   ├── face-detection/
│   ├── motion-detection/
│   ├── object-detection-tflite/
│   ├── object-detection-yolo/
│   ├── object-tracking-color/
│   ├── object-tracking-feature/
│   ├── object-tracking-shape/
│   └── utils/
│
├── install.sh
├── requirements.txt
├── LICENSE
└── README.md
```

---

# 🚀 Installation

Clone the repository.

```bash
git clone https://github.com/lakshya14-ds/rpi_object_detection.git

cd rpi_object_detection
```

Run the installer.

```bash
chmod +x install.sh

./install.sh
```

Activate the virtual environment.

```bash
source venv/bin/activate
```

---

# 🛠 Manual Installation

```bash
sudo apt update

sudo apt install -y \
libopencv-dev \
libatlas-base-dev \
python3-pip \
python3-venv
```

Create a virtual environment.

```bash
python3 -m venv --system-site-packages venv

source venv/bin/activate
```

Install Python packages.

```bash
pip install --upgrade pip

pip install -r requirements.txt
```

---

# 📦 Python Dependencies

```
opencv-python
opencv-contrib-python
numpy
scipy
matplotlib
pillow
ultralytics
packaging
python-dateutil
pyparsing
six
```

---

# ▶ Running the Applications

Camera Test

```bash
python src/camera-test/camera_test.py
```

Face Detection

```bash
python src/face-detection/face_detection.py
```

Motion Detection

```bash
python src/motion-detection/motion_detection.py
```

TensorFlow Lite Detection

```bash
python src/object-detection-tflite/object_detection_tflite.py
```

YOLO Detection

```bash
python src/object-detection-yolo/object_detection_yolo.py
```

Color Tracking

```bash
python src/object-tracking-color/color_tracking.py
```

Feature Tracking

```bash
python src/object-tracking-feature/feature_tracking.py
```

Shape Tracking

```bash
python src/object-tracking-shape/shape_tracking.py
```

---

# 🎮 Keyboard Controls

| Key | Action |
|------|--------|
| q | Quit application |
| Esc | Exit (if implemented) |
| Space | Pause (optional) |

---

# 🧠 Deep Learning Models

TensorFlow Lite supports lightweight object detection.

YOLO supports:

- YOLOv8n
- YOLOv8s
- YOLOv11n
- Custom trained models

Example:

```python
model = YOLO("yolov8n.pt")
```

---

# ⚙ How It Works

### OpenCV

- Camera capture
- Image processing
- Drawing bounding boxes
- Video display

### TensorFlow Lite

- Lightweight inference
- Fast edge deployment
- Low memory usage

### YOLO

- High accuracy
- Multiple object classes
- Bounding boxes
- Confidence scores

### Tracking Algorithms

- HSV Thresholding
- Background Subtraction
- Contour Detection
- Optical Flow
- ORB/SIFT Feature Matching

---

# 📊 Expected Performance

| Device | Camera | YOLOv8n FPS |
|---------|--------|-------------|
| Raspberry Pi 4 | 640×480 | 5–10 FPS |
| Raspberry Pi 5 | 640×480 | 12–20 FPS |
| Desktop CPU | 640×480 | 20–40 FPS |
| Desktop GPU | 640×480 | 60+ FPS |

*Performance depends on model size, resolution, and hardware configuration.*

---

# 🩺 Troubleshooting

| Problem | Solution |
|----------|----------|
| ModuleNotFoundError: picamera2 | Create venv using `--system-site-packages`. |
| Camera not detected | Try changing `VideoCapture(0)` to `VideoCapture(1)`. |
| Black screen | Verify CSI cable orientation or USB webcam permissions. |
| Illegal instruction | Use Raspberry Pi OS Bookworm (64-bit). |
| YOLO slow | Use `yolov8n.pt` or reduce resolution. |
| Qt display error | Run with desktop session or use SSH X-forwarding. |

---

# 🛣 Roadmap

- [ ] Unified CLI launcher
- [ ] MJPEG video streaming
- [ ] Video recording
- [ ] Detection logging
- [ ] Coral TPU support
- [ ] ONNX Runtime support
- [ ] Multi-object tracking (DeepSORT)
- [ ] Web dashboard
- [ ] FPS benchmarking

---

# 🤝 Contributing

Contributions are welcome.

1. Fork the repository.
2. Create a feature branch.
3. Commit your changes.
4. Push the branch.
5. Open a Pull Request.

---

# 🙏 Acknowledgements

- Raspberry Pi Foundation
- OpenCV
- Ultralytics
- TensorFlow Lite

Inspired by:

https://github.com/automaticdai/rpi-object-detection

---

# 📜 License

This project is released under the **MIT License**.

Feel free to use, modify, and distribute it for educational and commercial purposes.
