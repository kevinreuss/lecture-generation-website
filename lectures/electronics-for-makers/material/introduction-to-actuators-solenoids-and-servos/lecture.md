# Introduction to Actuators: Solenoids and Servos

Actuators are devices that convert energy into motion. In this lecture, we'll focus on two specific types: Solenoids and Servos.

## Solenoids

A solenoid is an electromechanical device that converts electrical energy into linear motion. It's essentially a coil of wire wrapped around a movable metal core. When electricity is passed through the coil, a magnetic field is produced that moves the core forward or backward. This movement can be used to perform mechanical work.

For example, in a door lock, a solenoid can be used to engage or disengage the lock mechanism. When an electrical current is applied, the solenoid moves the lock into position. When the current is removed, a spring returns the lock to its original position.

## Servos

Servos, or servo motors, are a type of actuator that provide precise control of angular or linear position. Inside a servo, a DC motor, a gear system, a position sensor, and a control circuit work together to achieve this.

When the control circuit receives a signal, it compares the current position of the motor to the signal. If there's a difference, the circuit drives the motor in the direction necessary to eliminate it.

For example, a servo motor could be used in a robotic arm to position the arm at a specific angle. The control signal would indicate the desired position, and the servo would adjust the arm's position accordingly.

In terms of code, let's use the Arduino platform. To control a servo, you might use the `Servo` library as follows:

```cpp
#include <Servo.h>

Servo myservo;

void setup() {
  myservo.attach(9);  // attaches the servo on pin 9
}

void loop() {
  myservo.write(90);  // sets the servo position to 90 degrees
  delay(1000);  // waits for a second
  myservo.write(0);  // sets the servo position to 0 degrees
  delay(1000);  // waits for a second
}
```

This code moves the servo to a 90-degree position, waits for a second, moves it back to a 0-degree position, then waits again before repeating the process.

To summarize, solenoids and servos are actuators that convert electrical energy into mechanical motion. Solenoids provide linear motion, while servos offer precise control of angular or linear position.