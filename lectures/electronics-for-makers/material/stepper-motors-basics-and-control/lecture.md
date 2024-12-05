# Stepper Motors: Basics and Control

Stepper motors are electric motors that divide a full rotation into a number of equal steps. The motor's position can be controlled precisely, without any feedback mechanism, as long as the motor is carefully sized to the application.

Stepper motors come in two varieties: Permanent Magnet (PM) and Variable Reluctance (VR), each having unique characteristics.

PM motors have a high torque and low speeds, while VR motors have low torque and high speeds. The choice of motor is application-specific.

## Control

The control of stepper motors involves two key concepts: 

- **Step Sequence:** This is the order in which the electromagnetic coils are activated to make the motor shaft move one step. The sequence differs depending on the type of motor (2-phase, 4-phase, etc.).

- **Step Mode:** This is the method used to activate the coils, determining the division of the full step rotation. Modes include Full Step, Half Step, and Microstepping.

## Control Example (Arduino)

Controlling a stepper motor via an Arduino can be done using the `Stepper` library. Here's a simple example of rotating a stepper motor in one direction:

```c
#include <Stepper.h>

const int stepsPerRevolution = 200;  // change this to fit the number of steps per revolution for your motor

// initialize the stepper library on pins 8 through 11:
Stepper myStepper(stepsPerRevolution, 8, 9, 10, 11);

void setup() {
  // set the speed at 60 rpm:
  myStepper.setSpeed(60);
}

void loop() {
  // step one revolution  in one direction:
  myStepper.step(stepsPerRevolution);
}
```

This code initializes a 4-phase stepper motor and sets its speed to 60 rpm. In the main loop, the motor is instructed to rotate one revolution in one direction.

Remember, stepper motor control requires a balance between speed and torque, as faster speeds typically reduce the motor's torque. The specific speed-torque characteristics depend on the specific motor design and drive circuitry.