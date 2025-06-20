# Real-Time Traffic Density Estimation and Violation Detection using YOLOv8

## 🚦 Project Overview

This project implements a real-time computer vision system for **traffic density estimation** and **potential traffic violation detection** using the state-of-the-art **YOLOv8** object detection model. The system processes video streams (e.g., from traffic cameras) to identify and track vehicles, calculate traffic density, and flag abnormal behaviors that could indicate violations.

This project can be a valuable tool for traffic management, urban planning, and enhancing road safety by providing real-time insights into traffic flow and identifying problematic driving patterns.

**Key Features:**
* **Object Detection:** Accurately identifies various road users (cars, trucks, motorcycles, pedestrians, buses, etc.) using a fine-tuned YOLOv8 model.
* **Traffic Density Estimation:** Calculates traffic congestion levels based on the number and spatial distribution of detected vehicles within defined regions of interest.
* **Traffic Violation Detection:** Implements rule-based logic to detect potential violations such as:
    * [**Vehicles crossing a predefined stop line during a red-light phase, or vehicles moving in a direction opposite to the designated flow in a specific lane.**]
* **Real-time Processing:** Designed for efficient analysis of live video streams or pre-recorded footage.
* **Customizable Zones:** Ability to define specific areas within the video frame for targeted analysis (e.g., counting zones, detection zones).

## ✨ How It Works

This project leverages the power of deep learning for object detection, combined with custom logic for traffic analysis.

1.  **YOLOv8 Object Detection:**
    * The core of the system is a YOLOv8 model, which has been either utilized as a pre-trained model or fine-tuned on a relevant dataset (e.g., COCO, or a custom traffic dataset).
    * It takes video frames as input and outputs bounding boxes and class labels for each detected object (e.g., `car`, `truck`, `person`).

2.  **Traffic Density Calculation:**
    * Once objects are detected, the system counts the number of specific vehicle types within the frame or within user-defined regions of interest (ROIs).
    * Traffic density metrics are derived from these counts, providing an indication of congestion.

3.  **Violation Detection Logic:**
    * For violation detection, [**For Red-Light Running:** "Virtual lines are defined on the road, and the system tracks vehicles' movement across these lines in conjunction with simulated traffic light states. If a vehicle crosses a defined stop line while the light is 'red,' it's flagged as a potential violation."
        * **For Wrong-Way Driving:** "Defined lane directions are established. If a vehicle's detected movement vector is consistently opposite to the expected flow for its lane, it's flagged."
        * **General:** "Rule-based algorithms are applied to the real-time detection and tracking data. These rules check for predefined conditions (e.g., object presence in restricted zones, movement patterns) that signify a potential violation."
**]

## 🛠️ Technologies Used

* **Programming Language:** Python
* **Deep Learning Framework:** PyTorch (YOLOv8's underlying framework)
* **Computer Vision:** OpenCV
* **Object Detection:** Ultralytics YOLOv8
* **Data Handling:** Pandas, NumPy
* **Serialization:** YAML (for model configuration, if any)

## 🚀 Getting Started

### Prerequisites

Make sure you have Python 3.x and `pip` installed on your system.

### Installation

1.  **(No Git Needed for this method!) Download the project:**
    * On the GitHub repository page, click the green "Code" button.
    * Select "Download ZIP" and extract the contents to your desired location on your computer.

2.  **Navigate to the project directory:**
    Open your terminal or command prompt and go to the extracted project folder (e.g., `cd traffic-estimation-yolov8-main`).

3.  **Create a virtual environment (highly recommended):**
    This isolates your project dependencies.
    ```bash
    python -m venv venv
    # On Windows:
    .\venv\Scripts\activate
    # On macOS/Linux:
    source venv/bin/activate
    ```

4.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

5.  **Download Trained Model Weights:**
    * Your custom trained model weights (`best.pt`) are crucial for the detection.
    * **If `models/best.pt` is included in the GitHub upload:** No extra steps needed here.
    * **If `models/best.pt` was too large for direct GitHub upload:**
        * Download the `best.pt` file from the link above and place it into the `models/` directory within your project folder.

### Usage

To run the traffic estimation and violation detection on a sample video:

1.  Ensure you have a sample video file ready. You can place it in the `data/raw/` directory (e.g., `data/raw/sample_traffic.mp4`).

2.  Execute your main detection script from the project's root directory:
    ```bash
    # Adjust 'traffic_detector.py' to your actual script name if different.
    # Adjust input/output paths as per your script's arguments.
    python src/traffic_detector.py --input_video data/raw/sample_traffic.mp4 --output_video results/output_video.avi
    ```
    * *(Optional: If your script has arguments for defining regions of interest or violation rules, provide examples here.)*
    * *(Example: `python src/traffic_detector.py --input_video data/raw/highway.mp4 --output_path output_highway.avi --config_file config/highway_rules.yaml`)*

3.  The processed video with detections, counts, and violation alerts will be saved to the specified `output_video` path (e.g., `results/output_video.avi`).

## 📊 Results & Demos

*(This is where you make your project shine!)*

* **[Optional: Embed a GIF or short video demo here!]**
    *(You can drag and drop a GIF/video directly into the GitHub README editor, and it will generate the Markdown link for you.)*
* **[Optional: Include Screenshots]**
    *(Show snapshots of your system's output: bounding boxes, counts, density indicators, violation alerts.)*

Example Description:
"The system accurately identifies and tracks vehicles in varying traffic conditions. The output video displays bounding boxes around detected objects, class labels, and a real-time count of vehicles. Potential violations are highlighted with [mention how, e.g., a red overlay, specific text warnings]."

## 📁 Repository Structure
