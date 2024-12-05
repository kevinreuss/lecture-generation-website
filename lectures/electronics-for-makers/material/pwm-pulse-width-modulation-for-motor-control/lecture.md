# PWM: Pulse Width Modulation for Motor Control

Pulse Width Modulation (PWM) is a technique used to control analog devices using digital outputs. In motor control, PWM enables us to vary the motor's speed and direction.

## PWM Basics

PWM signals are digital square waves, where the ratio of the period of time the signal is ON (high) to the total period it is ON plus OFF (low) is varied to control power. This ratio is referred to as the duty cycle. A higher duty cycle will cause the motor to spin faster, while a lower duty cycle will slow it down.

```python
duty_cycle = Time_ON / (Time_ON + Time_OFF)
```

## Controlling Motors

In motor control, changing the duty cycle of the PWM signal will change the speed of the motor.

For example, to make a DC motor turn, we can use a microcontroller's digital output and a transistor. The digital output is connected to the base of the transistor, while the motor is connected to the collector. The emitter goes to ground.

When the digital output is high, the transistor allows current to flow, turning the motor. When it is low, no current flows and the motor stops. By rapidly switching the output (PWM signal), we can control the speed of the motor.

```c
pinMode(MOTOR_PIN, OUTPUT);
analogWrite(MOTOR_PIN, duty_cycle);
```

## Direction Control

For direction control, H-bridge circuits are used. An H-bridge is an electronic circuit that enables a voltage to be applied across a load in either direction.

By controlling which transistors are ON (high) and OFF (low), we can change the direction of the current flow, consequently changing the direction of the motor.

```c
digitalWrite(Hbridge_PIN1, HIGH); // Turn on Transistor 1
digitalWrite(Hbridge_PIN2, LOW);  // Turn off Transistor 2
```

Remember that the key to using PWM for motor control is understanding how duty cycles work and how changing the PWM signal can affect a motor's speed and direction.
