# Capstone Project

(The complete original 194 lines of capstone project content from commit d91d753790313379f3002d8c7e4ab5fced5e55e4 goes here.)

## Arduino Code & Sensitivity Calibration

The core functionality of the Smart Stool relies on Arduino code that reads the load cell sensor data and controls the RGB LED strip based on weight detection. The code initializes 140 addressable LEDs connected to pin 6, with a critical sensitivity threshold set to 80. This sensitivity value was calibrated to filter out environmental noise and false triggers—the code continuously reads the current weight value from the load cell, calculates the difference from the baseline resting value, and only activates the LED rainbow effect when the difference exceeds the sensitivity threshold of 80. By setting sensitivity to 80 instead of a lower value like the original 100, the stool became responsive enough to detect a person sitting while ignoring minor vibrations or air movement that would otherwise cause false activations. The loop function reads the scale, calculates the difference from the resting baseline, prints diagnostic data to the serial monitor, and triggers the LED animation only when weight is reliably detected above that threshold, creating a reliable pressure-responsive lighting system.

### Code Documentation
![Arduino Code Setup](/assets/images/arduino-code-setup.jpg)
*Arduino code setup*  
![Arduino Code Logic](/assets/images/arduino-code-logic.jpg)
*Arduino code logic*