# Using Prefabricated PCBs and Shields

Prefabricated PCBs (Printed Circuit Boards) and shields present an easy and efficient way of extending the capabilities of your microcontroller. They are commonly used with platforms like Arduino and Raspberry Pi.

## Prefabricated PCBs

Prefabricated PCBs come with the components already soldered onto the board. For example, you might purchase a PCB with an accelerometer or a temperature sensor already mounted. You just need to connect the PCB to your microcontroller, and you're ready to start coding.

Here's an example of how you might code an Arduino to read data from a prefabricated PCB with a temperature sensor (TMP36):

```c
int tempPin = 0; // TMP36 connected to analog pin 0

void setup() {
  Serial.begin(9600);
}

void loop() {
  int reading = analogRead(tempPin);
  float voltage = reading * 5.0;
  voltage /= 1024.0;
  float temperatureC = (voltage - 0.5) * 100 ;
  Serial.print(temperatureC);
  delay(1000);
}
```
In this code, we're reading the temperature from the TMP36 sensor, converting it to a voltage, and then converting that to a temperature in Celsius.

## Shields

Shields are essentially prefabricated PCBs that are designed to plug directly into your microcontroller. They can add a wide range of capabilities, from Ethernet or WiFi connectivity, to LCD screens, to motor control.

Here's an example of how you might use an Ethernet shield with an Arduino:

```c
#include <SPI.h>
#include <Ethernet.h>

byte mac[] = { 0xDE, 0xAD, 0xBE, 0xEF, 0xFE, 0xED };
IPAddress ip(192,168,1,177);

EthernetServer server(80);

void setup() {
  Ethernet.begin(mac, ip);
  server.begin();
}

void loop() {
  EthernetClient client = server.available();
  if (client) {
    // Handle client requests here
  }
}
```
In this code, we're setting up the Arduino as a simple web server. We specify a MAC address and IP address for the Arduino, and start the server. In the loop function, we check for incoming client connections and handle them as needed.

The beauty of prefabricated PCBs and shields lies in their plug-and-play nature. They are a quick and convenient way to extend the functionality of your microcontroller, allowing you to focus on your code rather than the intricacies of the hardware.