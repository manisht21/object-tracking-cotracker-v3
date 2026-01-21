# Object Tracking in Self-Recorded Videos using CoTracker-v3

## Overview
This project implements an end-to-end object tracking system using CoTracker-v3, designed to track objects in self-recorded videos (smartphone or webcam). The system is robust to occlusion, abrupt motion, and complex backgrounds, and provides accurate trajectory extraction and visual motion analysis.

## Key Features
- Transformer-based multi-point object tracking using CoTracker-v3
- Robust tracking under occlusion and fast motion
- Object-centric cropping and trajectory visualization
- Frame-to-frame displacement analysis
- Supports real-world, self-recorded videos

## Tech Stack
- Language: Python 3.10+
- Libraries: PyTorch, NumPy, Matplotlib, ImageIO, OpenCV
- Model: CoTracker-v3 (Transformer-based space-time attention)

## Project Structure
object-tracking-cotracker-v3/
├── tracking.py
├── requirements.txt
├── checkpoints/
│   └── scaled_offline.pth
├── dataset/
│   ├── input_videos/
│   └── expected_outputs/
├── output/
│   ├── tracked_videos/
│   └── trajectory_plots/
├── report/
├── presentation/
└── demo/

## Dataset
- Source: Self-recorded videos
- Conditions: Varied lighting, background clutter, motion patterns
- Object tracked: Tennis ball (extendable to other objects)

## Methodology
1. Preprocess video (resize, frame-rate normalization)
2. Initialize tracker with manually selected object points
3. Perform forward tracking using CoTracker-v3
4. Extract trajectories, bounding boxes, and visibility masks
5. Visualize tracking results and analyze motion patterns

## Installation
pip install -r requirements.txt

## Usage
Place input video in:
dataset/input_videos/input_video.mp4

Run tracking:
python tracking.py --video dataset/input_videos/input_video.mp4 --output output/tracked_videos/output_tracked.mp4

## Model Checkpoint
Ensure the following file exists:
checkpoints/scaled_offline.pth

## Hyperparameters
- Grid size: 20
- Tracking direction: Forward only
- Object-centric crop size: 50 × 50
- Hardware: GPU-enabled recommended

## Outputs
- Tracked videos with bounding box overlays
- Object trajectory plots
- Frame-wise displacement measurements

## Results & Observations
- Successful tracking from frame 50 onward
- Frame-to-frame displacement:
  - Frame 50 → 100: 233.24 pixels
  - Frame 100 → 150: 223.61 pixels
- Smooth trajectories with minimal drift

## Demo & Documentation
- Project Report: report/Project_Report_Object_Tracking.pdf
- Presentation: presentation/Object_Tracking_Presentation.pdf
- Demo Video: demo/demo_video.mp4

## References
- Girdhar, R., et al. “CoTracker: It’s Better to Track Together.” CVPR 2023, arXiv:2301.03281
- https://github.com/facebookresearch/cotracker
- https://co-tracker.github.io/

## Author
Manish Tiwari  
MSc Physics | Machine Learning & Computer Vision

## Future Improvements
- Backward and bi-directional tracking
- Automatic object initialization
- Quantitative evaluation metrics (IoU, drift)
- Real-time inference optimization
