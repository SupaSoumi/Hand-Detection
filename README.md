Hand Tracking Project

This project demonstrates how to perform hand tracking using OpenCV and MediaPipe. It consists of three main scripts:

basics.py: A basic example of hand tracking using MediaPipe directly.

handtrackingmodule.py: A modular implementation for hand detection and landmark extraction.

projectexample.py: A project example that utilizes the handtrackingmodule for more structured hand tracking.

Prerequisites

Before running the project, ensure the following dependencies are installed:

Python 3.7 or later

OpenCV

MediaPipe

Installation

Install the required libraries using pip:

pip install opencv-python mediapipe

File Descriptions

basics.py

This script demonstrates basic hand tracking functionality using MediaPipe. It uses the camera feed to detect and display hand landmarks.

How to Run:

python basics.py

handtrackingmodule.py

This module encapsulates hand tracking functionality into a reusable class handDetector. The class provides two main methods:

findHands(img, draw=True): Detects hands in an image and optionally draws the landmarks.

findPosition(img, handNo=0, draw=True): Extracts and optionally draws the coordinates of landmarks for a specified hand.

projectexample.py

This script demonstrates how to use handtrackingmodule in a project. It captures video from the webcam, tracks hand landmarks, and displays them along with the FPS.

How to Run:

python projectexample.py

Key Features

Detects multiple hands in real-time.

Provides the coordinates of hand landmarks.

Displays hand landmarks and connections.

Modular design for easy integration into other projects.

Usage

Example Usage of handtrackingmodule:

import cv2
import handtrackingmodule as htm

detector = htm.handDetector()
cap = cv2.VideoCapture(0)

while True:
    success, img = cap.read()
    img = detector.findHands(img)
    lmList = detector.findPosition(img)
    if len(lmList) != 0:
        print(lmList[4])  # Print thumb tip position

    cv2.imshow("Image", img)
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

cap.release()
cv2.destroyAllWindows()

Troubleshooting

Camera Not Detected:

Ensure the correct camera index is used in cv2.VideoCapture. Default is 0.

Attribute Errors:

Ensure MediaPipe and OpenCV are correctly installed.

Validate that multi_hand_landmarks is not None before accessing it.

Performance Issues:

Reduce the resolution of the video feed for better performance.

Notes

Press q to quit the application.

Make sure your webcam is functional and accessible.

License

This project is open-source and can be modified or distributed under the terms of the MIT License.
