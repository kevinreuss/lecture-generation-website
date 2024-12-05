# Servo Motors: Basics and Control

Servo motors are a type of motor that can be controlled with a great degree of precision. They are typically used in systems where position control is important, such as robotic arms or drones.

Servo motors are composed of a small motor, a control circuit, and a potentiometer. The motor drives the output shaft and the potentiometer provides feedback on the shaft's position. This feedback loop allows the control circuit to regulate the motor's speed and position with great accuracy.

The control signal for a servo motor is a pulse-width modulation (PWM) signal. This is a digital signal that switches between on and off states. The duration of the on state (the pulse width) determines the position that the servo motor will move to.

For example, a pulse width of 1.5ms might correspond to a position at the midpoint of the servo's range of motion. Shorter pulse widths would move the servo to a position towards one end of its range, and longer pulse widths would move it towards the other end.

Here's an example of how you might control a servo motor using an Arduino:

```cpp
#include <Servo.h>

Servo myServo;  // create servo object

void setup() {
  myServo.attach(9);  // attaches the servo on pin 9
}

void loop() {
  int pos;

  // sweep from 0 to 180 degrees
  for (pos = 0; pos <= 180; pos += 1) {
    myServo.write(pos);  // tell servo to go to position 'pos'
    delay(15);           // wait 15ms for the servo to reach the position
  }

  // sweep back from 180 to 0 degrees
  for (pos = 180; pos >= 0; pos -= 1) {
    myServo.write(pos);  // tell servo to go to position 'pos'
    delay(15);           // wait 15ms for the servo to reach the position
  }
}
```

This code will cause the servo motor to sweep back and forth between 0 and 180 degrees.

Remember, different servo motors may require different pulse widths to achieve the full range of motion, so always refer to the datasheet for your specific motor.