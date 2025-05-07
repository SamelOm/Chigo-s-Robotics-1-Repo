# Gesture-Controlled Robot using Webots and Mediapipe

## 🧠 Project Overview

This project enables a differential-drive robot in Webots to be controlled via **hand gestures detected by a webcam**, using **MediaPipe** on one machine and **Webots simulation** on another — connected over a **Wi-Fi network using sockets**.

Gesture recognition is handled on a separate device (Laptop A), which sends commands like `fist`, `open`, `left`, and `right` to a Webots robot simulation running on another machine (Laptop B). The robot responds in real time to these commands.

---

## 🚀 How to Run the Project

### 🔧 Requirements

- Webots installed on Laptop B
- Python 3.8–3.10 on both machines
- `mediapipe`, `opencv-python` installed on Laptop A
- Both machines connected to the **same network** (Wi-Fi or hotspot)

### 📁 File Structure

```
Robotics_Project2025/
├── controllers/
│   └── webots_controller_socket/
│       └── webots_controller_socket.py
├── gesture_sender_client.py (run on Laptop A - Mac)
├── README.md
```

### 🖥 On Laptop B (Windows – Webots Host)

1. Open Webots and load the project world.
2. Ensure your robot’s controller is set to:
   ```
   "webots_controller_socket"
   ```
3. Run simulation (press ▶️).
4. Confirm terminal output:
   ```
   🟢 Listening for gesture sender on port 5050...
   ```

### 💻 On Laptop A (Mac – Gesture Detection)

1. Open Terminal.
2. Navigate to project folder.
3. Update the IP address in `gesture_sender_client.py`:
   ```python
   SERVER_IP = "192.168.x.x"  # ← IP of Laptop B
   ```
4. Run:
   ```bash
   python3 gesture_sender_client.py
   ```

---

## 🎮 Gesture Controls

| Gesture | Action            |
|---------|-------------------|
| ✊ Fist  | Move Forward      |
| ✋ Open  | Move Backward     |
| ↩️ Tilt Left | Turn Left         |
| ↪️ Tilt Right | Turn Right        |

---

## 🧪 Example Outputs

- **Console on Laptop B:**
  ```
  📄 Gesture received: fist
  📄 Gesture received: left
  ```

- **Webots Output:**
  Robot drives forward, turns, or stops in sync with gestures.

- **Camera Window on Mac:**
  - Live feed with detected gesture printed on screen.

---

## 📚 References

- [MediaPipe Hands](https://google.github.io/mediapipe/solutions/hands.html) – for gesture detection
- [OpenCV](https://opencv.org/) – for webcam image processing
- [Webots Documentation](https://cyberbotics.com/doc/guide/index) – for robot simulation

---

## 🛠️ Future Improvements

- Add additional gestures (e.g., stop, turbo, spin).
- Implement voice control as a fallback.
- Build a GUI toggle for switching between WASD and gesture mode.
- Add ArUco markers for camera-based position feedback.
- Package with Docker or installer for plug-and-play deployment.

---



## 👥 Authors

- Chigozie Eke (Lead Developer, Gesture Control & Robotics Integration)
- Om Samel – (System Architect, Vision Streaming & Cross-Platform Integration)
