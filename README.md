
# 🤚 Real-Time Hand Landmark & Finger Counter

A real-time computer vision project that uses **MediaPipe** and **OpenCV** to detect hands, track hand landmarks, and count the number of raised fingers using a webcam.

The system supports detecting up to **two hands simultaneously** and displays the finger count for each hand as well as the total number of raised fingers.

---

## 🚀 Features

* ✋ Real-time hand detection
* 🤚 Support for up to **2 hands**
* 📍 Detection of **21 hand landmarks** per hand
* ☝️ Real-time finger counting
* 🔢 Individual finger count for each detected hand
* 🧮 Total finger count across both hands
* 📷 Webcam-based processing
* 🟢 Visual display of hand landmarks
* ⚡ Real-time computer vision processing

---

## 🛠️ Technologies

* **Python**
* **OpenCV**
* **MediaPipe**
* **Computer Vision**

---

## 📂 Project Structure

```text
Real-Time-Hand-Landmark-and-Finger-Counter/
│
├── finger_counter.py
├── hand_landmarker.task
└── README.md
```

---

## ⚙️ How It Works

The project follows these main steps:

### 1. Initialize MediaPipe Hand Landmarker

The MediaPipe Hand Landmarker model is loaded using the `hand_landmarker.task` model file.

```python
base_options = python.BaseOptions(
    model_asset_path='hand_landmarker.task'
)
```

The detector is configured to detect up to two hands:

```python
options = vision.HandLandmarkerOptions(
    base_options=base_options,
    running_mode=vision.RunningMode.IMAGE,
    num_hands=2
)
```

### 2. Capture Webcam Frames

OpenCV is used to access the computer's webcam:

```python
cap = cv2.VideoCapture(0)
```

Each frame is flipped horizontally to provide a natural mirror-like view.

### 3. Detect Hand Landmarks

Each webcam frame is converted from **BGR to RGB** and processed by MediaPipe.

MediaPipe identifies the hand landmarks and returns their normalized coordinates.

Each detected hand contains **21 landmarks**.

### 4. Count Raised Fingers

The program checks the relative positions of specific landmarks to determine whether a finger is raised.

The main landmarks used are:

| Finger | Landmark |
| ------ | -------: |
| Thumb  |        4 |
| Index  |        8 |
| Middle |       12 |
| Ring   |       16 |
| Pinky  |       20 |

For the four fingers other than the thumb, the program compares the `y` coordinates of the fingertip and lower finger landmark.

### 5. Display Results

The program displays:

```text
Hand 1: 5
Hand 2: 3
Total Fingers: 8
```

It also draws the detected hand landmarks directly on the webcam frame.

---

## 🧠 Hand Landmark Model

MediaPipe detects **21 key points** on each hand.

```text
          8   12   16   20
          |    |    |    |
          |    |    |    |
          7   11   15   19
          |    |    |    |
          6   10   14   18
           \   |    |   /
            5  9   13  17
             \ |    | /
              \|    |/
               0
              / \
             1   2
                 |
                 3
                 |
                 4
```

These landmarks provide the geometric information required for hand tracking and finger detection.

---

## 📦 Installation

### 1. Clone the repository

```bash
git clone https://github.com/aytenakl/Real-Time-Hand-Landmark-and-Finger-Counter.git
```

### 2. Navigate to the project directory

```bash
cd Real-Time-Hand-Landmark-and-Finger-Counter
```

### 3. Install the required libraries

```bash
pip install opencv-python mediapipe
```

### 4. Make sure the model file exists

The project requires:

```text
hand_landmarker.task
```

Place the model file in the same directory as:

```text
finger_counter.py
```

---

## ▶️ Usage

Run the program using:

```bash
python finger_counter.py
```

A webcam window will open automatically.

Show your hand(s) in front of the camera and the program will detect the landmarks and count the raised fingers in real time.

### Exit

Press:

```text
Q
```

to close the application.

---

## 🎯 Example

If one hand has five raised fingers:

```text
Hand 1: 5
Total Fingers: 5
```

If two hands have five raised fingers each:

```text
Hand 1: 5
Hand 2: 5
Total Fingers: 10
```

---

## 🔮 Future Improvements

Possible improvements for future versions include:

* ✋ More accurate thumb detection for both hands
* 🎯 Gesture recognition
* 👍 Recognition of gestures such as:

  * Thumbs Up
  * Peace
  * Fist
  * Open Palm
  * OK Sign
* 🎮 Gesture-based computer control
* 🖱️ Hand gesture mouse control
* 🔊 Gesture-controlled applications
* 📊 Real-time FPS display
* 🎥 Video recording
* 🤖 Integration with robotics and automation systems

---

## 💡 Applications

This project can serve as a foundation for:

* Human-Computer Interaction
* Gesture Recognition
* Computer Vision applications
* Robotics
* Touchless interfaces
* Smart home control
* Educational computer vision projects
* AI-powered interaction systems

