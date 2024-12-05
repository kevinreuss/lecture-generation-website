# Essential Electronic Components: Resistors, Capacitors, Diodes

## Resistors

Resistors are passive components that limit or regulate the flow of electrical current in a circuit. They follow Ohm’s law (`V = I * R`), where V is voltage, I is current, and R is resistance. For example, a 10 Ohm resistor connected to a 5V power supply will allow a current of 0.5 Amps to flow. 

Resistors come in different types including fixed, variable, and thermistor (temperature sensitive). The resistance value is usually indicated using a color code system on the resistor body.

## Capacitors

Capacitors store and release electrical energy. They're characterized by their capacitance (`C = Q / V`), where C is capacitance, Q is charge, and V is voltage. 

For instance, a 1 Farad capacitor charged with 1 Volt will store a charge of 1 Coulomb. Capacitors can be used in timing circuits because they charge and discharge at predictable rates. For example, in a simple RC (Resistor-Capacitor) circuit, the time taken to charge a capacitor to about 63.2% of the supply voltage is given by the formula `t = R * C`.

## Diodes

Diodes allow current to flow in one direction only, acting like a one-way valve. They are characterized by their forward voltage drop and reverse breakdown voltage. A standard silicon diode has a forward voltage drop of about 0.7V. 

The basic function of a diode is demonstrated in a simple rectifier circuit. Consider a 5V AC signal applied to a diode in series with a resistor. The output will be a 5V DC signal (minus the 0.7V forward voltage drop of the diode). The diode effectively removes the negative half of the AC waveform.

```c++
/*
This simple Arduino code demonstrates the use of a diode in a digital circuit. The diode prevents backflow of current which could cause unexpected behaviour or damage.
*/

#define INPUT_PIN 2
#define OUTPUT_PIN 13

void setup() {
  pinMode(INPUT_PIN, INPUT);
  pinMode(OUTPUT_PIN, OUTPUT);
}

void loop() {
  if (digitalRead(INPUT_PIN) == HIGH) {
    digitalWrite(OUTPUT_PIN, HIGH);  // LED on
  } else {
    digitalWrite(OUTPUT_PIN, LOW);   // LED off
  }
}
```

In this code, a diode could be placed between the input pin and the output pin to ensure current only flows from the input to the output, not in the reverse direction.