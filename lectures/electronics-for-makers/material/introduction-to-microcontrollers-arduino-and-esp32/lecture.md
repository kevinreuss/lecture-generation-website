# Introduction to Microcontrollers: Arduino and ESP32

Microcontrollers are compact integrated circuits designed to perform specific operations in an embedded system. Two popular microcontrollers are the Arduino and the ESP32.

## Arduino

Arduino is an open-source electronics platform based on easy-to-use hardware and software. Arduino boards can read inputs - light on a sensor, a finger on a button, or a Twitter message - and turn it into an output - activating a motor, turning on an LED, publishing something online.

Arduinos run on a language that is a set of C/C++ functions. All standard Arduino functions like digitalRead, digitalWrite, Serial.begin, delay, etc. are available.

```C++
int ledPin = 13;

void setup() {
  pinMode(ledPin, OUTPUT);
}

void loop() {
  digitalWrite(ledPin, HIGH);
  delay(1000);
  digitalWrite(ledPin, LOW);
  delay(1000);
}
```
This simple program blinks an LED connected to pin 13 of the Arduino board every second.

## ESP32

The ESP32 is a series of low-cost, low-power microcontrollers with integrated Wi-Fi and dual-mode Bluetooth. The ESP32 series is created and developed by Espressif Systems, a Shanghai-based Chinese company.

ESP32 can be programmed with different software environments like ESP-IDF, Arduino IDE, MicroPython, Python, Lua, JavaScript, etc. Here is an example of an ESP32 code snippet that connects to a Wi-Fi network:

```C++
#include <WiFi.h>

const char* ssid = "your_SSID";
const char* password = "your_PASSWORD";

void setup() {
  Serial.begin(115200);

  WiFi.begin(ssid, password);

  while (WiFi.status() != WL_CONNECTED) {
    delay(1000);
    Serial.println("Connecting to WiFi...");
  }
  
  Serial.println("Connected to WiFi");
}

void loop() {}
```
This program tries to connect to a specified Wi-Fi network and prints a message on the serial monitor once the connection is successful.

Remember, both Arduino and ESP32 are versatile microcontrollers with a large supportive community, making them ideal for both beginners and professionals.