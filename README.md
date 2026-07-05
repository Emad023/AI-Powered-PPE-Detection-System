# AI-Powered PPE Detection System

A sophisticated computer vision system that monitors Personal Protective Equipment (PPE) compliance in real-time using advanced YOLO models and intelligent tracking algorithms.

## Demo

![PPE Detection Demo](output.gif)

*Real-time PPE detection in action - tracking workers and monitoring helmet & vest compliance with sequential ID assignment*

## Overview

The Workplace Safety Monitor is designed to enhance workplace safety by automatically detecting people and their required safety equipment (helmets and safety vests) in video streams. The system uses state-of-the-art computer vision techniques to provide accurate, real-time monitoring with minimal false positives.

## Key Features

- **Real-time Detection**: Live person and PPE detection using YOLO models
- **Smart Association**: Intelligent PPE-to-person matching using anatomical region analysis
- **Multi-Source Support**: Works with webcams, IP cameras, and video files
- **Video Recording**: Outputs annotated MP4 videos with detection results
- **Temporal Smoothing**: Reduces false positives through frame-to-frame consistency
- **High Accuracy**: Advanced filtering and validation for reliable results
- **Real-time Performance**: Optimized for live video processing
- **Flexible Configuration**: Customizable thresholds and parameters

## Use Cases

### 1. **Workplace Safety Monitoring**
Monitor construction sites, factories, and industrial facilities for PPE compliance in real-time.

### 2. **Access Control Security System** 
**Deploy as a security checkpoint** to allow facility entry only for workers wearing proper safety equipment:
- Install cameras at facility entrances
- Automatically verify helmet and vest compliance
- Integrate with access control systems (gates, turnstiles)
- Log entry attempts and safety violations
- Send alerts for non-compliant personnel
- Generate compliance reports for safety managers

### 3. **Construction Site Oversight**
Continuous monitoring of construction workers to ensure safety protocol adherence.

### 4. **Industrial Facility Monitoring**
Monitor manufacturing plants, warehouses, and processing facilities for safety compliance.

### 5. **Safety Training & Education**
Use recorded footage to train workers and demonstrate proper PPE usage.

## Installation

### Prerequisites
- Python 3.8+
- OpenCV 4.x
- NumPy
- (Optional) Ultralytics for advanced YOLO models

### Quick Setup
```bash
# Clone the repository
git clone <repository-url>
cd Safety_Gear_Detection_Camera

# Install dependencies
pip install opencv-python numpy
pip install ultralytics  # Optional, for advanced YOLO models

# Verify installation
python3 workplace_safety_monitor.py --help
```

## Requirements

Create a `requirements.txt` file:
```
opencv-python>=4.8.0
numpy>=1.21.0
ultralytics>=8.0.0
torch>=1.13.0
torchvision>=0.14.0
```
## Project Structure

```
Safety_Gear_Detection_Camera/
├── workplace_safety_monitor.py    
├── README.md                      
├── requirements.txt               
├── best.pt         
├── output.gif                                  
├── .gitignore            
```

## How It Works

### 1. **Person Detection**
- Uses YOLO models for high-accuracy person detection
- Falls back to OpenCV HOG detector if YOLO unavailable
- Filters detections by size and aspect ratio

### 2. **PPE Detection**
- Separate YOLO model trained specifically for helmets and safety vests
- Supports both Ultralytics (.pt) and ONNX formats
- Configurable confidence thresholds per equipment type

### 3. **Intelligent Association**
- Maps PPE items to specific persons using anatomical regions
- Helmets must overlap with head region (upper 40% of person box)
- Vests must overlap with torso region (middle section)
- Ensures PPE is mostly contained within person boundaries

### 4. **Temporal Smoothing & Smart Tracking**
- Tracks persons across frames using IoU-based tracking
- Applies temporal filtering to reduce single-frame false positives
- Maintains detection history for stable results
- **Smart boundary validation**: Automatically removes tracks stuck at frame edges
- **Edge detection**: Identifies when people exit the frame and cleans up tracking boxes immediately

### 5. **Visualization & Output**
- Real-time display with color-coded bounding boxes
- Green: Compliant (has required PPE)
- Red: Non-compliant (missing PPE)
- Blue: PPE detection boxes
- Saves annotated MP4 video and individual frames

## Future Enhancements

- [ ] Multi-camera support for comprehensive coverage
- [ ] Database integration for violation logging
- [ ] Web-based dashboard for remote monitoring
- [ ] Mobile app for notifications
- [ ] Additional PPE types (gloves, boots, masks)
- [ ] Integration with existing security systems
- [ ] Machine learning model auto-updates
- [ ] Analytics and reporting features

