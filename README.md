# Vibe Check

![License](https://img.shields.io/github/license/b0uks/vibe-check)
![Issues](https://img.shields.io/github/issues/b0uks/vibe-check)
![Forks](https://img.shields.io/github/forks/b0uks/vibe-check)
![Stars](https://img.shields.io/github/stars/b0uks/vibe-check)

## 📖 About

**Vibe Check** is an Arduino-based project that brings vibrant and dynamic lighting effects to your LED strips using the [FastLED](https://fastled.io/) library. Whether you're looking to enhance your home decor, create ambient lighting for events, or simply experiment with LED animations, Vibe Check offers a variety of customizable effects to set the perfect mood.

## 🚀 Features

- **Rainbow Cycles**: Display a spectrum of colors that smoothly transition across the LED strip.
- **Color Wipe**: Sequentially illuminate LEDs in a forward or backward direction with adjustable speed.
- **Random Colors**: Generate and display random colors across all LEDs for a lively ambiance.
- **Dissolve Effect**: Randomly turn off a specified number of LEDs to create a fading effect.
- **Stripes**: Alternate between two colors in striped patterns with customizable width.
- **Cylon Motion**: Simulate the iconic Cylon eye movement with adjustable width and speed.
- **Lightning Flashes**: Create sudden flashes of light to mimic lightning strikes.
- **Theater Chase**: Sequentially illuminate every third LED, creating a chasing effect.
- **Theater Chase Rainbow**: Combine theater chase with rainbow colors for a mesmerizing display.
- **Flashing Effects**: Flash specific colors or random colors with customizable speed and count.

## 🛠️ Installation

### 🔧 Hardware Requirements

- **Arduino Board**: Compatible boards like Arduino Uno, Mega, Nano, etc.
- **LED Strip**: Neopixel (WS2812) or similar addressable RGB LED strips.
- **Power Supply**: Suitable for your LED strip (e.g., 5V, sufficient current).
- **Resistor**: 470Ω resistor for data line protection.
- **Capacitor**: 1000µF, 6.3V or higher capacitor to prevent power spikes.
- **Connecting Wires**
- **Breadboard** (optional)

### 📦 Software Requirements

- **Arduino IDE**: Download and install from [here](https://www.arduino.cc/en/software).
- **FastLED Library**: Install via Arduino Library Manager or download from [GitHub](https://github.com/FastLED/FastLED).

### 🔌 Wiring Instructions

1. **Connect the LED Strip to Arduino**
   - **Data Pin**: Connect the LED strip's data input to Arduino's pin `10` (modifiable in code).
   - **Power**: Connect the LED strip's `5V` and `GND` to a suitable power supply.
   - **Ground**: Ensure the Arduino's `GND` is connected to the LED strip's `GND`.

2. **Add a Resistor and Capacitor**
   - Place a `470Ω` resistor between the Arduino's data pin and the LED strip's data input.
   - Connect a `1000µF` capacitor across the LED strip's `5V` and `GND` to stabilize power.

   ![Wiring Diagram](https://github.com/b0uks/reactive_LED/blob/main/LED_IDA_bb.pdf)

### 🖥️ Software Setup

1. **Clone the Repository**

   ```bash
   git clone https://github.com/b0uks/vibe-check.git
   cd vibe-check
   ```
2. **Open the Project in Arduino IDE**

Launch the Arduino IDE.
Open the VibeCheck.ino file from the cloned repository.
3. **Install FastLED Library**

In the Arduino IDE, navigate to Sketch > Include Library > Manage Libraries...
Search for FastLED and install the latest version.
4. **Configure the Code (Optional)**

Number of LEDs: Modify #define NUM_LEDS 60 to match your LED strip length.
Data Pin: Change #define DATA_PIN 10 if using a different Arduino pin.
Effect Speeds and Directions: Adjust speed constants (SLOW, MEDIUM, FAST) and effect parameters as desired.
5.**Upload the Code**

Connect your Arduino board to your computer via USB.
Select the correct board and port in Tools > Board and Tools > Port.
Click the Upload button to flash the code to your Arduino.
## ⚙️ Usage
Once the code is uploaded, the LED strip will automatically cycle through various lighting effects. You can customize the behavior by modifying the code parameters or adding new effects.

## 📜 Code Overview
- Setup Function

Initializes the FastLED library, seeds the random number generator, and starts serial communication.

```cpp
Copy
void setup() { 
  FastLED.addLeds<NEOPIXEL, DATA_PIN>(leds, NUM_LEDS);
  randomSeed(analogRead(0));
  Serial.begin(9600);
}
```
- Loop Function

Sequentially executes different lighting effects with delays to create a dynamic display.

```cpp
void loop() { 
  rainbow(0, NULL);
  delay(3000);
  colorWipe(CRGB::Black, FORWARD, FAST);
  allRandom();
  delay(3000);
  disolve(15, 100, MEDIUM);
  // ... additional effects
}
```
- Effect Functions

A variety of functions like `allColor`, `allRandom`, `disolve`, `flash`, `colorWipe`, `rainbow`, `theaterChase`, etc., define different lighting animations.

## 📁 Project Structure
```bash
vibe-check/
├── VibeCheck.ino        # Main Arduino sketch
├── README.md            # Project documentation
└── LICENSE              # Licensing information
```
VibeCheck.ino: Contains the Arduino code controlling the LED effects.
README.md: This documentation file.
LICENSE: Licensing details for the project.
## 🧪 Testing
To verify that the LED effects work as intended:
1. Power the Setup
Ensure the Arduino and LED strip are properly connected and powered.
2. Monitor Serial Output
Open the Serial Monitor in the Arduino IDE (Tools > Serial Monitor) to view debug messages and API responses (if applicable).
3. Observe LED Behavior
Watch the LED strip as it cycles through the predefined effects. Ensure each effect transitions smoothly and operates at the expected speed.
4. Troubleshooting
No LEDs Lighting Up: Check wiring connections, ensure the correct data pin is defined, and verify power supply.
Incorrect Colors or Flickering: Ensure the data line has a resistor and the power supply is stable with a capacitor.
Serial Monitor Issues: Verify the correct baud rate (9600 in this case) is selected.
