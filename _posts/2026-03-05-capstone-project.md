---
title: Capstone Project - The Smart Stool
layout: post
---

Capstone Project Documentation

## Description of final project choice, why chosen, and what a successful project would do:

My final project is a smart stool that combines making a stool with basic electronics. I chose this project because it allowed me to work with both physical components and electronics, which interested me more than doing only one or the other. I wanted to create something functional and interactive rather than just decorative, but at the same time I did not want to make something so hard because of my lack of experience in engineering.

A successful version of this project will function as a normal stool but also include a pressure sensor that detects when someone sits down. When pressure is applied, LED lights embedded in the stool will turn on, creating a visual response to the user. The electronics will be hidden underneath the stool so the design looks clean and intentional, with only the light visible. If completed successfully, the stool will be sturdy, visually appealing, and reliably respond to pressure.

## Attribution of project serving as inspiration:

This project is inspired by me searching on YouTube for electronic ideas and sources that could be interesting to make into a final project that is also doable. For the electronics portions, I drew inspiration from tutorials on force sensors and pressure-activated LED systems. For the wood portions, I researched furniture design and stool fabrication techniques.

Sources:
- How to Use a Force Sensor with an Arduino (Lesson #23)
- Force Pressure Sensor with Arduino LED Indicator
- Making A $3 bar stool from a 2x4 | woodworking | diy gift ideas

[YouTube - Force Sensor Tutorial](https://www.youtube.com/watch?v=r7oWtcE6QQc) | [YouTube - Pressure LED Project](https://www.youtube.com/watch?v=ZlXglJ1keIc) | [YouTube - DIY Bar Stool](https://www.youtube.com/watch?v=GsAb9DXlk-4)

## Description of how project is different than these sources:

Unlike the electronics-focused videos or woodworking videos that address only one aspect, my project combines building furniture with embedded electronics. Instead of attaching LEDs externally or making a small prototype, I am building a full-size stool with electronics fully hidden inside. I also designed my own stool dimensions and structure rather than copying an existing furniture plan. This makes my project more personalized and fabrication-focused than the individual sources that inspired it.

## Design Specification Considerations

When designing my stool, I considered:

- **Size and scale** so it can support a person safely (200+ lbs)
- **Base diameter** of 22.5 inches with wood that has a radius of .75+ inches and 18-20 inch legs
- **Material choice**, starting with cardboard prototypes before moving to wood
- **Placement of electronics** so they are hidden and protected (under the bottom of the stool)
- **Ease of assembly** and maintenance in case electronics need adjustment
- **Visual simplicity**, ensuring the LEDs enhance the design rather than distract from it

---

# INSTRUCTIONS

## Final materials list including costs:

1. Cardboard (for prototyping) - at Latin
2. Wood (final stool structure) - at Latin
3. Arduino microcontroller - at Latin
4. Load cell sensor - approximately $30-40
5. RGB LEDs - approximately $10-15 at Latin
6. Resistors - at Latin
7. PCB board - at Latin
8. Wires and connectors - at Latin
9. Power source (battery or USB) - to be obtained
10. Wood glue, screws, sandpaper, finish - at Latin

Most electronics were provided through the lab or classroom supply, keeping costs low.

## Project Management (plan and deadlines):

The project was designed with a phased approach: prototype development in the fall semester, followed by final fabrication and electronics integration in the spring semester. Key milestones included cardboard prototyping completion, CNC design finalization, and electronics testing and calibration.

## Tools Used (hand tools and Fab Lab equipment):

- **Laser cutter** - for cardboard prototype pieces (vector cut settings for clean cuts without burning)
- **Sandpaper and sanding tools** - for finishing wooden components
- **Hand saw or band saw** - for cutting wood pieces
- **Drill** - for creating holes for electronic component placement
- **Soldering iron** - for electrical connections
- **CNC router** - for precision cutting of wooden components with a 3/8" compression bit
- **Arduino IDE** - software tool for programming the microcontroller
- **Vectric Aspire** - CAD software for designing CNC cut files

## What Files Did You Include? (Arduino, Corel Draw, Fusion 360, etc.)

The project includes:
- **Arduino sketch** (`smart_stool.ino`) - embedded code for load cell calibration and LED control
- **CNC design files** (`.dxf` format) - vector files for cutting the stool base and leg components
- **Design specifications document** - detailing dimensions, material choices, and assembly procedures
- **Detailed photos** - documenting the fabrication process, component testing, and final assembly

<a href="https://docs.google.com/document/d/1CaDUQ4LmfPJc6pKK6p19hoUctoCXxTt6e9c5fYZ9dEQ/edit" target="_blank" rel="noopener">Milling workflow (open in new tab)</a> | <a href="https://docs.google.com/document/d/1Hm03u70SZn6hg4F6Bugsz9wwq4C9IR7cGyQyIbE5Zmo/edit" target="_blank" rel="noopener">Process photos (open in new tab)</a>



### Code Integration: 

Arduino Code & Sensitivity Calibration
The core functionality of the Smart Stool relies on Arduino code that reads the load cell sensor data and controls the RGB LED strip based on weight detection. The code initializes 140 addressable LEDs connected to pin 6, with a critical sensitivity threshold set to 80. This sensitivity value was calibrated to filter out environmental noise and false triggers—the code continuously reads the current weight value from the load cell, calculates the difference from the baseline resting value, and only activates the LED rainbow effect when the difference exceeds the sensitivity threshold of 80. By setting sensitivity to 80 instead of a lower value like the original 100, the stool became responsive enough to detect a person sitting while ignoring minor vibrations or air movement that would otherwise cause false activations. The loop function reads the scale, calculates the difference from the resting baseline, prints diagnostic data to the serial monitor, and triggers the LED animation only when weight is reliably detected above that threshold, creating a reliable pressure-responsive lighting system.

Code: #include "HX711.h"
#include <FastLED.h>

// --- CONFIGURATION ---
#define LED_PIN     6
#define NUM_LEDS    140   // For 1 meter Sezo strip
#define BRIGHTNESS  50
#define SENSITIVITY 80 // Increase this number if lights stay on by themselves

// --- PINS ---
const int DOUT_PIN = 3;
const int SCK_PIN = 2;

HX711 scale;
CRGB leds[NUM_LEDS];
long restingValue = 0;

void setup() {
  Serial.begin(9600);
 
  // Initialize LEDs
  FastLED.addLeds<WS2812B, LED_PIN, GRB>(leds, NUM_LEDS);
  FastLED.setBrightness(BRIGHTNESS);
  FastLED.clear();
  FastLED.show();

  // Initialize HX711
  scale.begin(DOUT_PIN, SCK_PIN);
 
  // Take a baseline reading to know what "Empty" looks like
  delay(1000);
  if (scale.is_ready()) {
    restingValue = scale.read();
    Serial.print("Resting Value Set: ");
    Serial.println(restingValue);
  }
}

void loop() {
  if (scale.is_ready()) {
    long currentValue = scale.read();
    long difference = abs(currentValue - restingValue);

    // DEBUG: View these numbers in Serial Monitor to adjust sensitivity
    Serial.print("Diff: ");
    Serial.println(difference);

    if (difference > SENSITIVITY) {
      // WEIGHT DETECTED: Show Rainbow
      fill_rainbow(leds, NUM_LEDS, millis() / 10, 5);
    } else {
      // NO WEIGHT: Force Black
      fill_solid(leds, NUM_LEDS, CRGB::Black);
    }
  } else {
    // If HX711 isn't responding, blink first LED Red as a warning
    leds[0] = CRGB::Red;
  }

  FastLED.show();
  delay(20);
}


## Electronics Testing & Component Integration

IMG_0843 (Aspire design): This image shows the initial design created using Aspire software, laying the groundwork for the stool's features. It encapsulates the both artistic design and technical skills, and this was impressive for me as I had not dealt with aspire much in the past.  ![Electronics Setup](/assets/IMG_0843.jpeg)

IMG_0852 (CNC cutting): Here, we see the CNC machine at work, cutting the stool's components from the wood. The use of CNC technology exemplifies the project's focus on accuracy, ensuring that every piece fits perfectly together for optimal functionality.![RGB LED Test 1](/assets/IMG_0852.jpeg)

IMG_0864 (allowance offset): This picture highlights the  measurement adjustments made during the machining process. By accounting for allowance offsets, I ensured that parts fit seamlessly, an essential aspect of combining design with hardware integration. ![RGB LED Test 2](/assets/IMG_0864.jpg)

IMG_0865 (Aspire on CNC): Captured in this image is the Aspire interface displaying the cutting pathway, essential for precision machining. The coordination between software and hardware emphasizes the importance of planning and precision in my project. ![Electronics Assembly Workspace](/assets/IMG_0865.jpeg)

IMG_0867 (CNC in action): This action shot of the CNC machine illustrates the real-time implementation of designs. It showcases the smart manufacturing techniques that bring this interactive stool to life, merging technology with different designs.![CNC Machine Setup](/assets/IMG_0867.jpeg)

IMG_0961-2 (electronics assembly): The assembly of electronics is shown in this image, capturing the intricate wiring needed to enable the stool's pressure-responsive lighting. This integration is key to getting the Stool to work at its best.![CNC Cutting Process](/assets/IMG_0961-2.jpeg)

IMG_0962-2 (electronics assembly): Another angle of the assembly process emphasizes the  attention to detail involved. Each connection contributes to the broader aim of me combining aesthetics with electronic functionality.![CAD Design Vectric](/assets/IMG_0962-2.jpeg)

IMG_0970 (stool upside down): This image exhibits the underside of the stool, revealing the electronic components carefully housed within. It symbolizes our project’s dual nature, offering both functionality and style.![Design Blueprint](/assets/IMG_0970.jpeg)

IMG_0976 (all 144 LEDs): Here, the full array of LEDs is displayed, illustrating the project's innovative approach to interactive lighting. Their placement and configuration are designed to enhance the stool's appeal and user engagement.![Electronics Assembly Detail](/assets/IMG_0976.jpeg)

IMG_0975 (30 LEDs): This detail shot captures a section of the LEDs in action, showcasing the vibrant illumination they provide. This design choice reflects our commitment to blending furniture design with responsive technology.[LEDs](/assets/IMG_0975.jpeg)

IMG_0990 (stool completed): The final image showcases the completed stool, beautifully merging all elements of design and technology. It stands as a testament to our collaborative efforts in creating a functional, interactive piece that embodies the essence of our project.[Stool Complete](assets/IMG_0990.jpeg)



---

# DOCUMENTATION OF LEARNING

## Important decisions and Why:

One of the biggest decisions I made was to focus on building the physical stool first. This just made the most sense to me. I wanted to know that the stool actually works as a stool before I started worrying about lights, wires, and code. Figuring out the size and leg length early helped me avoid having to redo parts of the electronics later.

I also decided to prototype everything in cardboard first because it let me experiment with proportions without wasting wood. This was crucial for understanding the spatial constraints for electronics placement. Another key choice was hiding all the electronics underneath so the stool still looks clean and intentional.

All of these decisions worked together and helped keep the project feeling doable instead of overwhelming.

## Challenges, mistakes, and how I overcame them:

**Challenge 1: Sensor Calibration**
Initially, the load cell sensor wasn't reading accurately. I discovered the HX711 amplifier pins weren't properly connected to the Arduino. I physically secured the board to the breadboard using wire bridges, which resolved the electrical gap issue.

**Challenge 2: LED Brightness Control**
The RGB LED strip stopped working at a certain pixel (#30). After investigation, I identified a dead pixel caused by a sharp bend in the data wire. I adjusted the wire routing to prevent sharp bends and now press that 30th LED to power the rest of them.

**Challenge 3: Precision Fabrication**
When testing the CNC cut files, I had to dial in the tolerance offset. I started at no offset (0"), then tested at -.1", and finally settled at -.05" to achieve a balance between sturdy assembly and easy insertion/removal of components.

**Challenge 4: Understanding the Electronics Design**
The HX711 ADC converter was initially confusing—it translates analog weight signals into digital values the Arduino can process. Understanding how calibration works (setting the zero point on startup) was critical. I used the concept of "sensitivity" (set to 80 in the code) to filter out small vibrations that would trigger false readings.

## Longer final summary (3-5 paragraphs about the project, the process, and what you learned):

**The Smart Stool Project: Integration of Design and Electronics**

The Smart Stool represents an integration of mechanical design, digital fabrication, and embedded electronics. Beginning with cardboard prototypes, I validated the demensional requirements for a full-scale piece of furniture that could support a person's weight while concealing electronic components. The design evolved through consideration of material properties and manufacturing constraints. By using CNC fabrication with precision-tested tool bits and offset tolerances, I produced wooden components that were structurally sound and aesthetically intentional.

The electronics portion required engagement with microcontroller programming and sensor integration. The load cell sensor measures weight in analog signals, which the HX711 amplifier converts to digital data at high resolution. The Arduino code implements a calibration routine on startup and applies sensitivity filtering to distinguish between intentional weight (someone sitting) and environmental noise, which is why I set the sensitivity to 80. This work exposed me to the full pipeline of embedded systems: sensor selection, signal conditioning, processing logic, and output control (the RGB LED).

What I learned most was that success in a capstone project depends on managing complexity through different phases of development, and being okay with the fact that messing up during certain steps is a lesson rather than failure. Rather than trying to build everything at once, I broke the work into stages: prototype validation, fabrication preparation, component testing, and final integration. This approach made the project feel manageable and allowed me to catch and fix problems one at a time instead of trying to juggle everything. I also learned the importance of documentation and iterative testing: every challenge I faced (sensor calibration, LED brightness, fabrication tolerance) had a solution waiting in careful observation and systematic adjustment.

When continuing this project, I would focus on remaking the stool and getting a new LED strip, with a specific concern for the stability of the legs of the stool. I will remake the legs with joints or dominos which will allow the legs to be more stable. Also, I plan on switching out the LED strips, as I would prefer all 144 to turn on instead of the first 30 when I sit down on this stool. Lastly, I would paint the entire stool and maybe use a wood finish to give it that smooth feel which I do not have right now.

---

This page will be updated as the project continues to progress.
