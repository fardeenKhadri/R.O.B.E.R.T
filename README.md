# R.O.B.E.R.T — Real-time Obstacle-aware Binaural Environment Responsive Tracker

An intelligent multimodal system for real-time obstacle detection, voice interaction, and visual depth estimation. Designed to assist with environmental awareness using audio-visual input, powered by advanced AI models and sensor integration.

---

## 🔧 Features

### 🧠 `ada/multimodal_live_api.py`
- Captures real-time video using a webcam and analyzes visual depth using a pretrained neural network.
- Streams audio input from a microphone and provides audio playback.
- Performs **live depth estimation** and **obstacle detection** using a custom-trained `DepthAnythingV2` model.
- Interprets environmental layout using a 2x3 zone grid and generates navigation suggestions (e.g., LEFT, RIGHT, STOP).
- Sends serial commands to microcontrollers for robotic actuation based on detected obstacles and optimal pathing.
- Visual feedback through OpenCV interface showing depth, camera feed, and navigation cues.
- Monitors and handles camera health with backup frame recovery and auto-reinitialization.

### 👁️‍🗨️ `Depth_Anything/fixxing.py`
- Lightweight version of the multimodal system.
- Captures video from webcam or screen and streams frames with accompanying audio.
- Supports interactive voice conversations with streaming input/output.
- Operates in either **camera** or **screen capture** mode, ideal for demos or desktop monitoring.

---

## 🖥️ Requirements

Install dependencies:

```bash
pip install -r requirements.txt
````

Required libraries include:

* Python ≥ 3.9
* `torch`, `opencv-python`, `pyaudio`, `dotenv`, `Pillow`, `mss`, `numpy`

---

## 🌐 Environment Setup

Create a `.env` file with your configuration keys:

```
API_KEY=your_key_here
```

Ensure model checkpoints are stored here:

```
checkpoints/depth_anything_v2_vits.pth
```

---

## 🚀 Running the Project

### For full AI-driven audio-visual system with navigation:

```bash
cd ada
python multimodal_live_api.py --mode camera
```

### For lightweight frame + audio streaming (camera or screen):

```bash
cd Depth_Anything
python fixxing.py --mode screen
# or
python fixxing.py --mode camera
```

---

## 🔌 Serial Port Integration

* Serial communication over `COM5` to send movement instructions.
* Supported commands:

  * `L` – Turn Left
  * `R` – Turn Right
  * `SA` – Move Straight Ahead
  * `S` – Stop

---

## 📊 Visual Grid & Navigation Logic

* Frame is split into a 2x3 grid for spatial reasoning.
* Color-coded detection per cell:

  * 🔴 Red = Obstacle
  * 🔵 Blue, 🟢 Green = Navigational safe zones
* Real-time output shows:

  * Depth map
  * Navigation direction
  * Frame health and camera status

---

## 🧠 Depth Model

* Based on `DepthAnythingV2`, a vision transformer model with multi-scale output.
* Optimized for real-time inference using `torch.inference_mode()`.

---

## 📄 License

This project is released under the MIT License. Free to use, modify, and distribute for research and personal use.

---

## 🙋‍♀️ Maintainers

Created by [Pramoda S R](https://github.com/Pramoda-S-R) [Anusha Rao](https://github.com/anushaarao3) [Fardeen Khadri](https://github.com/fardeenKhadri)  

---


