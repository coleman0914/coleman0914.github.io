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

## Detailed photos and videos

### Electronics Testing & Component Integration

The electronics setup showcases the Keyestudio microcontroller, load cell sensor integration, and RGB LED control system. Below are images documenting the testing and calibration process:

<div class="image-gallery" style="display:grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 15px; margin: 20px 0;">
  <figure>
    <img src="{{ '/assets/electronics-setup-1.jpg' | relative_url }}" alt="Keyestudio microcontroller with load cell and RGB LED setup" style="width:100%; height:auto; border-radius: 8px;">
    <figcaption style="font-size: 0.9em; color: #666; margin-top: 8px;">Keyestudio board connected to load cell sensor, power supply, and breadboards for component organization</figcaption>
  </figure>

  <figure>
    <img src="{{ '/assets/rgb-led-test-1.jpg' | relative_url }}" alt="RGB LED strip color testing with weight sensor" style="width:100%; height:auto; border-radius: 8px;">
    <figcaption style="font-size: 0.9em; color: #666; margin-top: 8px;">RGB LED strip displaying full color spectrum during calibration testing with digital scale</figcaption>
  </figure>

  <figure>
    <img src="{{ '/assets/rgb-led-test-2.jpg' | relative_url }}" alt="Rainbow color gradient on addressable LED strip" style="width:100%; height:auto; border-radius: 8px;">
    <figcaption style="font-size: 0.9em; color: #666; margin-top: 8px;">Addressable RGB LED strip showing smooth color gradient and responsiveness to control signals</figcaption>
  </figure>

  <figure>
    <img src="{{ '/assets/electronics-assembly-workspace.jpg' | relative_url }}" alt="Electronics components and materials organized on workbench" style="width:100%; height:auto; border-radius: 8px;">
    <figcaption style="font-size: 0.9em; color: #666; margin-top: 8px;">Complete component inventory including microcontroller, sensor modules, breadboards, and wiring</figcaption>
  </figure>
</div>

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


### CNC Fabrication & Design Process

The CNC fabrication process involved designing precise cutting patterns in CAD software, then using the CNC router to cut wooden components with exact tolerances. Below are images showing the design and fabrication workflow:

<div class="image-gallery" style="display:grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 15px; margin: 20px 0;">
  <figure>
    <img src="{{ '/assets/cnc-machine-setup.jpg' | relative_url }}" alt="CNC router machine with wooden base loaded" style="width:100%; height:auto; border-radius: 8px;">
    <figcaption style="font-size: 0.9em; color: #666; margin-top: 8px;">Industrial CNC router positioned to cut wooden stool base and legs with precision</figcaption>
  </figure>

  <figure>
    <img src="{{ '/assets/cnc-cutting-process.jpg' | relative_url }}" alt="CNC machine in operation cutting the base design" style="width:100%; height:auto; border-radius: 8px;">
    <figcaption style="font-size: 0.9em; color: #666; margin-top: 8px;">CNC router executing cut patterns on wooden material with compressed bit tool</figcaption>
  </figure>

  <figure>
    <img src="{{ '/assets/cad-design-vectric.jpg' | relative_url }}" alt="CAD design file in Vectric Aspire software" style="width:100%; height:auto; border-radius: 8px;">
    <figcaption style="font-size: 0.9em; color: #666; margin-top: 8px;">Vector design in Vectric Aspire showing circular base pattern and rectangular leg components</figcaption>
  </figure>

  <figure>
    <img src="{{ '/assets/design-blueprint.jpg' | relative_url }}" alt="Detailed design blueprint with dimensions" style="width:100%; height:auto; border-radius: 8px;">
    <figcaption style="font-size: 0.9em; color: #666; margin-top: 8px;">Design specifications documenting exact dimensions and component layout for fabrication</figcaption>
  </figure>
</div>

### Final Assembly & Completed Smart Stool

The final assembly brings together the wooden furniture structure with integrated electronics. Below are images showing the completed stool and component assembly process:

<div class="image-gallery" style="display:grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 15px; margin: 20px 0;">
  <figure>
    <img src="{{ '/assets/stool-completed.jpg' | relative_url }}" alt="Finished smart stool with orange seat and wooden legs" style="width:100%; height:auto; border-radius: 8px;">
    <figcaption style="font-size: 0.9em; color: #666; margin-top: 8px;">Completed smart stool with orange seat top, decorative beaded trim, and integrated electronics hidden underneath</figcaption>
  </figure>

  <figure>
    <img src="{{ '/assets/electronics-assembly-detail.jpg' | relative_url }}" alt="Electronics during assembly showing wire connections and board layout" style="width:100%; height:auto; border-radius: 8px;">
    <figcaption style="font-size: 0.9em; color: #666; margin-top: 8px;">Electronics assembly process showing Keyestudio board, load cell connections, and power routing configuration</figcaption>
  </figure>
</div>

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
