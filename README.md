"# 🍓 Raspberry Pi Real-Time Object Detection & Tracking

<p align=\"center\">
  <img src=\"https://img.shields.io/badge/Platform-Raspberry%20Pi-C51A4A?logo=raspberrypi&logoColor=white\" alt=\"Platform\">
  <img src=\"https://img.shields.io/badge/Python-3.9%2B-3776AB?logo=python&logoColor=white\" alt=\"Python\">
  <img src=\"https://img.shields.io/badge/OpenCV-4.x-5C3EE8?logo=opencv&logoColor=white\" alt=\"OpenCV\">
  <img src=\"https://img.shields.io/badge/YOLO-Ultralytics-00FFFF\" alt=\"YOLO\">
  <img src=\"https://img.shields.io/badge/TensorFlow-Lite-FF6F00?logo=tensorflow&logoColor=white\" alt=\"TFLite\">
  <img src=\"https://img.shields.io/badge/License-MIT-green\" alt=\"License\">
</p>

A collection of computer-vision modules that run **on a Raspberry Pi** (and any Linux/macOS machine with a webcam) to perform **real-time object detection, face detection, motion detection and object tracking** using OpenCV, TensorFlow Lite and YOLO (Ultralytics).

This project is a hands-on toolkit for learning practical computer vision on edge devices — from a simple camera sanity-check to deep-learning powered object detection.

---

## ✨ Features

This repository ships several **independent demos**, each in its own folder under `src/`:

| Module | What it does |
|---|---|
| 📷 **camera-test** | Verifies the Pi/USB camera works and streams frames via OpenCV. |
| 🙂 **face-detection** | Detects faces in the video feed (Haar cascade / DNN). |
| 🏃 **motion-detection** | Highlights moving regions using frame-differencing / background subtraction. |
| 🤖 **object-detection-tflite** | Runs a lightweight TensorFlow Lite model for multi-class object detection. |
| 🧠 **object-detection-yolo** | Runs Ultralytics **YOLO** for high-accuracy object detection. |
| 🎨 **object-tracking-color** | Tracks an object based on its HSV color signature. |
| 🧩 **object-tracking-feature** | Feature-based tracking (keypoints / descriptors). |
| 🔷 **object-tracking-shape** | Tracks objects by detecting geometric shapes / contours. |
| 🛠️ **utils** | Shared helpers (FPS counter, camera wrappers, drawing utilities). |

---

## 🧰 Hardware Requirements

- **Raspberry Pi 4 / 5** (2 GB RAM minimum, 4 GB+ recommended) — *or any Linux/macOS machine*
- **Camera**, one of:
  - Raspberry Pi Camera Module (v1 / v2 / v3 / HQ) via the CSI ribbon, **or**
  - USB webcam (UVC compatible)
- microSD card with **Raspberry Pi OS (Bookworm)** flashed
- (Optional) Active cooling — YOLO/TFLite inference will warm the SoC
- (Optional) Display / SSH access to view the OpenCV preview window

---

## 📂 Project Structure

```
rpi_object_detection/
├── images/                          # Demo images & screenshots
├── src/
│   ├── camera-test/                 # Basic camera streaming test
│   ├── face-detection/              # Real-time face detection
│   ├── motion-detection/            # Motion / background subtraction
│   ├── object-detection-tflite/     # Object detection w/ TensorFlow Lite
│   ├── object-detection-yolo/       # Object detection w/ Ultralytics YOLO
│   ├── object-tracking-color/       # Color-based tracking (HSV)
│   ├── object-tracking-feature/     # Feature-based tracking
│   ├── object-tracking-shape/       # Shape / contour-based tracking
│   └── utils/                       # Shared utilities (camera, FPS, drawing)
├── install.sh                       # One-shot environment setup
├── requirements.txt                 # Python dependencies
└── README.md
```

---

## 🚀 Quick Start

### 1. Clone the repository

```bash
git clone https://github.com/lakshya14-ds/rpi_object_detection.git
cd rpi_object_detection
```

### 2. Run the install script

The provided `install.sh` will:

- Update apt and install system libraries (`libopencv-dev`, `libatlas-base-dev`, `python3-venv`, `python3-pip`)
- Create a Python virtual environment at `./venv`
  - On Raspberry Pi it uses `--system-site-packages` so that **`libcamera` / `picamera2`** (preinstalled by Raspberry Pi OS) remain available inside the venv
- Install all Python dependencies from `requirements.txt`

```bash
chmod +x install.sh
./install.sh
```

### 3. Activate the virtual environment

```bash
source venv/bin/activate
```

> 💡 You only run `install.sh` once. After that, just `source venv/bin/activate` whenever you open a new terminal.

---

## 🧪 Manual Installation (alternative)

If you prefer to set things up by hand:

```bash
# System packages (Debian/Raspberry Pi OS / Ubuntu)
sudo apt-get update
sudo apt-get install -y libopencv-dev libatlas-base-dev python3-venv python3-pip

# Python env
python3 -m venv --system-site-packages venv   # drop --system-site-packages on non-Pi
source venv/bin/activate
pip install --upgrade pip setuptools wheel
pip install -r requirements.txt
```

### Python dependencies (`requirements.txt`)

```
matplotlib
numpy
opencv-contrib-python
opencv-python
packaging
pillow
pyparsing
python-dateutil
scipy
six
ultralytics
```

---

## ▶️ Running the Demos

Each module is a self-contained Python script. After activating the venv, run any demo from the project root, e.g.:

```bash
# Sanity-check the camera
python src/camera-test/camera_test.py

# Real-time face detection
python src/face-detection/face_detection.py

# Motion detection
python src/motion-detection/motion_detection.py

# TFLite object detection
python src/object-detection-tflite/object_detection_tflite.py

# YOLO object detection (Ultralytics)
python src/object-detection-yolo/object_detection_yolo.py

# Object tracking variants
python src/object-tracking-color/color_tracking.py
python src/object-tracking-feature/feature_tracking.py
python src/object-tracking-shape/shape_tracking.py
```

> 📌 The exact script filenames may differ slightly inside each folder — open the folder and run the `.py` file you find there. Press **`q`** in the preview window to quit.

---

## ⚙️ How It Works (in a nutshell)

- **OpenCV** captures frames from the camera, handles drawing and the preview window.
- **`picamera2` / `libcamera`** (on Raspberry Pi) provides a modern camera backend; on non-Pi systems OpenCV falls back to the standard webcam driver.
- **Classical CV** demos (motion / color / shape / feature tracking) rely on thresholding, contour analysis, optical flow and keypoint descriptors from OpenCV.
- **Deep-learning** demos use:
  - **TensorFlow Lite** for a small, fast multi-class detector that runs comfortably on a Pi.
  - **Ultralytics YOLO** for higher-accuracy detection (great on Pi 5 / desktop; usable on Pi 4).

---

## 🩺 Troubleshooting

| Problem | Fix |
|---|---|
| `ModuleNotFoundError: picamera2` | Make sure the venv was created with `--system-site-packages` *and* you're on Raspberry Pi OS. |
| Black/garbled preview window | Try a different camera index (`cv2.VideoCapture(0)` → `1`) or check the CSI ribbon orientation. |
| `Illegal instruction` on Pi | You may be on an older OS / 32-bit build — use Raspberry Pi OS Bookworm 64-bit. |
| YOLO is very slow | Use a smaller variant (e.g. `yolov8n.pt`), reduce input resolution, or run on Pi 5. |
| `qt.qpa.xcb: could not connect to display` | Run on the Pi desktop, or enable X-forwarding: `ssh -X pi@raspberrypi.local`. |

---

## 🗺️ Roadmap / Ideas

- [ ] Add a unified CLI (`python -m rpi_od <demo>`) to launch any module
- [ ] Stream the annotated video over HTTP / MJPEG
- [ ] Record detections to disk with timestamps
- [ ] Add Coral USB Accelerator support for TFLite
- [ ] Benchmark FPS table across Pi 4 / Pi 5 / desktop

---

## 🙏 Acknowledgements

- Inspired by [`automaticdai/rpi-object-detection`](https://github.com/automaticdai/rpi-object-detection) (referenced in `install.sh`).
- [OpenCV](https://opencv.org/) and [Ultralytics YOLO](https://github.com/ultralytics/ultralytics) for the underlying CV/ML stacks.
- The Raspberry Pi Foundation for `libcamera` & `picamera2`.

---

## 📜 License

Released under the **MIT License**. See `LICENSE` for details (add one if missing).

---
