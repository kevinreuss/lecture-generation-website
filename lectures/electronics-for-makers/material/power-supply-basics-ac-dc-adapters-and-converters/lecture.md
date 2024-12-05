# Power Supply Basics: AC/DC, Adapters, and Converters

## AC/DC

Alternating Current (AC) and Direct Current (DC) are two basic types of electric current. AC periodically changes its direction while DC flows consistently in one direction. For instance, household outlets supply AC power, while batteries provide DC power.

## Adapters

An adapter is a device used to convert one type of electrical signal into another. For example, an AC adapter converts the AC from your wall outlet into a DC that can be used by your laptop, smartphone, or other electronic devices.

```python
class Adapter:
    def __init__(self, input_type):
        self.input_type = input_type

    def convert(self, output_type):
        # Conversion process here
        return converted_output
```
Above, we have a simple Python class modeling an adapter converting input into desired output.

## Converters

Converters are devices that convert electrical energy from one form to another. Common types include AC-to-DC, DC-to-DC, and DC-to-AC converters. Converters find applications in numerous electronic devices, from power supplies to motor drives.

```python
class Converter:
    def __init__(self, input_energy):
        self.input_energy = input_energy

    def convert(self, desired_form):
        # Conversion process here
        return converted_energy
```
In the Python class above, a converter is modeled that takes input energy and converts it into a desired form.

In conclusion, understanding power supply basics is vital for software engineers working closely with hardware. These elements constitute the fundamental building blocks of powering and operating electronic devices.