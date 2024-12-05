# Sensors: Types and Integration

## Types of Sensors

There are numerous types of sensors, each designed for a specific purpose. Here we will focus on three common types used in software engineering:

1. **Temperature Sensors**: These are used to measure the amount of heat energy that allows us to perceive how hot or cold something is. An example is the DS18B20 digital temperature sensor which operates on the 1-Wire bus.

2. **Proximity Sensors**: These are used to detect the presence or absence of objects using electromagnetic fields, light, and sound. A popular example is the HC-SR04 ultrasonic distance sensor.

3. **Motion Sensors**: These are used to detect physical movement in a given area. An example is the PIR (Passive Infrared) motion sensor.

## Integration of Sensors

The integration of sensors involves connecting them to a microcontroller or microprocessor to interpret the sensor data. The steps generally involve:

1. **Connecting the Sensor**: This typically involves understanding the sensor's pin configuration and connecting it to the appropriate GPIO pins on the microcontroller.

2. **Programming the Microcontroller**: This involves writing code that will read the data from the sensor and perform some action based on the sensor data.

Here is an example of how you might connect a DS18B20 temperature sensor to a Raspberry Pi and write a Python program to read the temperature data:

```python
import os
import glob
import time

os.system('modprobe w1-gpio')
os.system('modprobe w1-therm')

base_dir = '/sys/bus/w1/devices/'
device_folder = glob.glob(base_dir + '28*')[0]
device_file = device_folder + '/w1_slave'

def read_temp_raw():
    f = open(device_file, 'r')
    lines = f.readlines()
    f.close()
    return lines

def read_temp():
    lines = read_temp_raw()
    while lines[0].strip()[-3:] != 'YES':
        time.sleep(0.2)
        lines = read_temp_raw()
    equals_pos = lines[1].find('t=')
    if equals_pos != -1:
        temp_string = lines[1][equals_pos+2:]
        temp_c = float(temp_string) / 1000.0
        return temp_c

while True:
    print(read_temp())
    time.sleep(1)
```

This Python script continuously reads the temperature from the DS18B20 sensor and prints it out. It accesses the sensor data through the Raspberry Pi's 1-Wire interface, which is exposed via the Linux filesystem at `/sys/bus/w1/devices/`.
