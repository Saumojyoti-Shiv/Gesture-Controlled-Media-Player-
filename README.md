# YouTube Gesture Controller 🤚🎥

A Python-based computer vision project that lets you control YouTube video playback and Windows system volume using hand gestures. It uses **MediaPipe** for real-time hand tracking, **OpenCV** for webcam feed processing, and **Selenium** to interact with the browser.

## ✨ Features & Supported Gestures

This script detects specific hand poses and maps them to browser and system controls:

### Right Hand (Playback Controls)
* **1 Finger (Index up) ☝️:** Skip Forward 5 seconds.
* **2 Fingers (Peace sign) ✌️:** Skip Backward (Rewind) 5 seconds.
* **Closed Fist ✊:** Pause Video.
* **Open Hand 🖐️:** Play Video.

### Left Hand (Volume Controls)
* **Pinch Gesture 🤏:** Controls Windows system volume. The distance between your thumb tip and index finger tip dynamically adjusts the master volume.

### Both Hands
* **Both Hands Closed Fists ✊✊:** Mute YouTube Video.
* **Both Hands Open 🖐️🖐️:** Unmute YouTube Video.

---

## 🛠️ Prerequisites

Before running the project, ensure you have the following installed:
1.  **Python 3.x**
2.  **Google Chrome Browser** (required by the Selenium WebDriver)
3.  A working **Webcam**
4.  **Windows OS** (The `pycaw` library is specifically used for Windows system volume control).

## 📦 Installation

1. **Clone the repository** (or download the script):
   ```bash
   git clone https://github.com/yourusername/youtube-gesture-controller.git
   cd youtube-gesture-controller
   ```

2. **Install the required Python packages**:
   You can install the dependencies via pip:
   ```bash
   pip install opencv-python numpy mediapipe selenium pycaw comtypes
   ```

*(Note: Selenium will automatically attempt to manage the ChromeDriver for your version of Google Chrome. If it fails, you may need to manually install ChromeDriver.)*

---

## 🚀 Usage

1. Run the Python script:
   ```bash
   python main.py
   ```
2. A new Chrome window will open and navigate to YouTube. 
3. **Wait for 15 seconds** (as programmed in the script) to allow you to log in or manually select and start a video.
4. Once the video is playing, your webcam will activate, and a window titled "YouTube Gesture Control" will appear.
5. Perform the gestures in front of your camera to control the video and volume!
6. To exit the program safely, press the **`q`** key while focused on the webcam window.

---

## 🧠 How it Works

* **OpenCV (`cv2`)**: Captures video frames from your webcam.
* **MediaPipe**: Processes each frame to detect hands, classify them as Left or Right, and map 21 3D landmarks on each hand.
* **Selenium**: Injects JavaScript directly into the YouTube DOM to manipulate the `<video>` element (e.g., `.play()`, `.pause()`, `.currentTime`).
* **Pycaw**: Interfaces with the Windows Core Audio API to change the actual system-level volume based on the pixel distance between specific finger landmarks.

---

## ⚠️ Limitations & Notes
* **Platform Restriction**: Volume control currently uses `pycaw`, which only works on Windows. 
* **Lighting**: Hand tracking relies heavily on good lighting. Ensure you are in a well-lit room for the gestures to register smoothly.
* **Cooldowns**: Skipping forward/backward has a 0.7-second cooldown built-in to prevent accidental rapid skipping.
