# Capstone Project

## Introduction

[Your existing 194 lines of content go here]

## Arduino Code & Sensitivity Calibration

The Arduino code plays a crucial role in managing sensor actions and processing input data. In this project, we selected a sensitivity value of 80, which plays a vital role in determining the responsiveness of the system. A higher sensitivity value means that the Arduino is more responsive to subtle changes in data signals, making it ideal for sensitive applications such as environmental monitoring. By adjusting the sensitivity, we can strike a balance between responsiveness and the prevention of false positives from noise.

The operational logic in the Arduino code is structured to gather real-time data from the sensors and analyze this data against defined thresholds. Sensor readings are captured in a loop, where they are continuously compared to the predefined sensitivity level of 80. If a reading exceeds this threshold, the Arduino triggers appropriate actions, whether that be activating alerts, logging data, or adjusting device outputs based on the needs of the project.

Moreover, the code is designed with modularity in mind, allowing for easy adjustments to the sensitivity level should the project requirements change or if testing indicates that a higher or lower sensitivity is necessary.

Here are the references for the setup and logic diagrams used in this project:

![Arduino Code Setup](arduino-code-setup.jpg)
![Arduino Code Logic](arduino-code-logic.jpg)

## DOCUMENTATION OF LEARNING

[Following content continues here]