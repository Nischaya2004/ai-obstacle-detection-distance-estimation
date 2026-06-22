# Optical Obstacle Size and Distance Estimation System with AI

This project is based on my Bachelor thesis in Applied Artificial Intelligence. It investigates a robot-mounted optical obstacle detection and distance estimation system using computer vision, laser projection, Raspberry Pi, and machine learning.

## Project Overview

The goal was to design, build, and experimentally validate a short-range optical sensing system that can estimate obstacle distance using camera images and structured laser projections.

The system uses:

- Raspberry Pi 4 Model B
- Raspberry Pi Camera Module 3 Wide
- Four red line laser modules
- Custom mechanical holder
- Industrial robot for repeatable sensor positioning
- Cross-shaped aluminium obstacle
- Python/OpenCV processing pipeline
- Random Forest regression model

## Experimental Setup

The sensing unit was mounted on an industrial robot to achieve controlled and repeatable positioning. The robot moved the sensor head across six reference distances:

- 130 mm
- 120 mm
- 110 mm
- 100 mm
- 90 mm
- 80 mm

At each distance, 15 laser combinations were tested with 10 images per combination, producing a final dataset of 900 raw images.

## Data Processing Pipeline

1. Capture dark-room raw images
2. Apply HSV red-laser segmentation
3. Generate binary masks
4. Apply morphological cleaning
5. Detect laser regions
6. Extract per-laser features
7. Train and evaluate distance-estimation models

## Extracted Features

- Laser detection flag
- Centroid x/y
- Normalized centroid coordinates
- Area
- Bounding box
- Standard deviation
- Laser-line angle
- Line length
- Density

## Machine Learning Approach

A four-output distance-estimation structure was used, corresponding to four physical laser directions:

- A: top laser
- B: right laser
- C: bottom laser
- D: left laser

Random Forest regression models were trained to estimate distance from extracted laser-image features.

## Reported Results

Random Forest distance-estimation performance by laser:

| Laser | Samples | MAE (mm) | RMSE (mm) | R² |
|---|---:|---:|---:|---:|
| A | 360 | 0.51 | 1.30 | 0.994 |
| B | 473 | 0.84 | 2.40 | 0.979 |
| C | 375 | 1.53 | 4.07 | 0.947 |
| D | 474 | 2.51 | 6.47 | 0.854 |

Red-laser detection rate:

| Laser | Detection Rate |
|---|---:|
| A | 75.0% |
| B | 98.5% |
| C | 78.1% |
| D | 98.8% |

## Tech Stack

Python, OpenCV, pandas, scikit-learn, matplotlib, Raspberry Pi, Raspberry Pi Camera, laser segmentation, image processing, machine learning, experimental robotics

## Repository Status

This repository is being prepared as a public portfolio version of the thesis project. Full raw data and sensitive academic files may be excluded, but the methodology, architecture, project summary, and selected visuals will be documented.

## Author

Nischaya Barotha  
Applied Artificial Intelligence Graduate  
Vilnius, Lithuania
