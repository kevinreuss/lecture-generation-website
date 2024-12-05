# LEDs: Types, Applications, and Control

## Types of LEDs

There are various types of LEDs, each with unique characteristics:

1. **Miniature LEDs**: Widely used in electronic devices and indicator lamps.
2. **High Power LEDs**: Used in high-intensity lighting solutions.
3. **RGB LEDs**: These combine red, green, and blue light to produce different colors.
4. **OLEDs (Organic LEDs)**: Used in display technology in phones and TVs.

## Applications

LEDs find use in several areas due to their efficiency, longevity, and versatility:

- **Indicators and Signs**: Miniature LEDs are used in electronic devices.
- **Traffic Signals and Automotive Lighting**: High-intensity LEDs are used due to their low power consumption and high visibility.
- **Display and Backlighting**: RGB LEDs and OLEDs are used in screens for phones, TVs, and computers.

## Control 

LEDs can be controlled in two main ways:

1. **Pulse Width Modulation (PWM)**: This involves changing the light intensity by adjusting the pulse width of the control signal. For instance, in Arduino, you might use the `analogWrite()` function:

```c
int ledPin = 9; // LED connected to digital pin 9
void setup() { pinMode(ledPin, OUTPUT); }
void loop() {
  for (int i = 0; i <= 255; i++) {
    analogWrite(ledPin, i); // sets the LED brightness
    delay(10); // Wait for 10 milliseconds
  }
}
```

2. **Digital Multiplexing (DMX)**: This is a protocol for controlling multiple LEDs (or other devices) from a single controller. A standard Arduino library, `DMXSerial`, can be used for DMX control.

```c
#include <DMXSerial.h>
void setup() { DMXSerial.init(DMXController); }
void loop() {
  for (int i = 1; i <= 512; i++) {
    DMXSerial.write(i, 255); // sets the DMX channel to full intensity
    delay(10); // Wait for 10 milliseconds
  }
}
```

Remember, while PWM is suitable for simple, single-LED setups, DMX should be used for more complex, multi-LED systems.