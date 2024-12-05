# Introduction to Robotics: Building Simple Systems

Robotics is a multidisciplinary field involving mechanical engineering, electronics, computer science, artificial intelligence, and more. In this discussion, we will focus on building simple robotic systems.

## Basic Components of a Robotic System

A simple robotic system is composed of sensors, actuators, and a control unit. 

- **Sensors**: These are devices that measure physical quantities and convert them into signals. For example, a temperature sensor in a robot might measure the heat of an object and convert it into an electrical signal.

- **Actuators**: These are devices that move or control a mechanism in the robot. For example, motors that move the robot's wheels.

- **Control Unit**: This is a computer or microcontroller that processes the signals from the sensors and controls the actuators.

## Building a Simple Robotic System

Consider a basic obstacle-avoiding robot. Here, we will use an Arduino board as the control unit, an ultrasonic sensor to detect obstacles, and DC motors as actuators.

### Ultrasonic Sensor

The ultrasonic sensor emits high-frequency sound waves and measures the time taken for the echo to return, calculating the distance of the object. The sensor has two main components: the transmitter (sends the sound waves) and the receiver (receives the echo).

### Arduino Control Unit

The Arduino receives the distance data from the ultrasonic sensor. If the distance is less than a certain threshold, the Arduino sends a signal to the motor drivers to change the robot's direction.

### Motor Driver and DC Motors

Motor drivers receive signals from the Arduino and control the speed and direction of the motors. If an obstacle is detected, the motor driver changes the direction of the motors, causing the robot to turn.

### Code Snippet

Here is a simple Arduino code that uses an ultrasonic sensor to avoid obstacles:

```c++
#define trigPin 9
#define echoPin 10
#define motor1 6
#define motor2 7

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(motor1, OUTPUT);
  pinMode(motor2, OUTPUT);
}

void loop() {
  long duration, distance;
  digitalWrite(trigPin, LOW);  
  delayMicroseconds(2); 
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10); 
  digitalWrite(trigPin, LOW);
  duration = pulseIn(echoPin, HIGH);
  distance = (duration/2) / 29.1;
  
  if (distance < 20) { // if distance is less than 20cm
    digitalWrite(motor1, HIGH); // turn right
    digitalWrite(motor2, LOW); 
  } else {
    digitalWrite(motor1, LOW); // move forward
    digitalWrite(motor2, HIGH);
  }
}
```
This code initiates the ultrasonic sensor and the motors. It then continuously checks for obstacles, and if an object is detected within 20cm, it turns the robot right.