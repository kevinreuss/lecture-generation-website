# DC Motors: Basics and Control

## Basics of DC Motors

Direct Current (DC) motors convert electrical energy into mechanical energy. They consist of two primary components: the stator and the rotor. The stator is the stationary outer frame, which provides a consistent magnetic field. The rotor, or armature, is the inner part that rotates and is responsible for output torque and speed.

DC motors are classified into three types: series, shunt, and compound, depending on the connection of the field winding with respect to the armature.

## Control of DC Motors

The control of DC motors is a critical aspect to adjust speed and position. There are two primary methods:

1. **Armature Control**: This method involves varying the armature voltage while keeping the field current constant. It is suitable for controlling the speed above the rated speed.

2. **Field Control**: This involves varying the field current while keeping the armature voltage constant. It is used for controlling speed below the rated speed.

In software, the control of a DC motor is typically achieved using Pulse Width Modulation (PWM). By adjusting the duty cycle, you can control the effective voltage and, consequently, the speed of the motor.

Here is an example using Arduino:

```C++
int motorPin = 3; // Pin connected to the motor
void setup() {
  pinMode(motorPin, OUTPUT);
}

void loop() {
  for (int speed = 0; speed <= 255; speed++) {
    analogWrite(motorPin, speed); // Change duty cycle
    delay(10);
  }
}
```

In this code, the `analogWrite` function generates a PWM signal on the motorPin. The duty cycle of the PWM signal is adjusted by changing the second parameter to the `analogWrite` function, which effectively changes the speed of the DC motor.

Remember, while DC motors are simple to understand and control, they require adequate protection circuitry to prevent damage and ensure safe operation.