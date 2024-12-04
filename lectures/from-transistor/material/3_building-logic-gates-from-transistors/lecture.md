# Building Logic Gates from Transistors

Transistors, the fundamental building blocks of modern electronic devices, can be used to construct logic gates, which are the building blocks of digital circuits.

## NPN Transistors

An NPN transistor has three layers of semiconductor—a negative layer, sandwiched between two positive layers. The three terminals are emitter (E), base (B), and collector (C). Through these, you can control the flow of current. 

A simple representation of NPN transistor:

```
       B
       |
    -------
   |       |
E--| NPN   |---C
   |       |
    -------
```

## NOT Gate

A NOT gate can be built using a single NPN transistor. It inverts the input—when input (A) is high (1), output (Q) is low (0), and vice versa.

```
        Vcc (5V)
         |
         R
         |
    B----|------ A
    |    |
 -------  |
|      |  |
| NPN  |  |
|      |  |
 -------  |
    |     |
   ---    ---
    -     -
    GND   Q (Output)
```

In the above circuit, when A is high, base current flows, the transistor is ON, and Q is virtually shorted to ground making it LOW. When A is low, the transistor is OFF, and Q is virtually connected to Vcc through the resistor, making it HIGH.

## AND Gate

An AND gate can be realized using two NPN transistors in series. It gives a high output (1) only if all its inputs are high.

```
         Vcc (5V)
          |
          R
          |
    B-----|------ A
    |     |
 -------  |
|      |  |
| NPN  |  |
|      |  |
 -------  |
    |     |
    B     |
    |     |
 -------  |
|      |  |
| NPN  |  |
|      |  |
 -------  |
    |     |
   ---    ---
    -     -
    GND   Q (Output)
```

In this circuit, if A and B are high, both transistors are ON, and Q is LOW. If either A or B or both are low, the corresponding transistor(s) is OFF, and Q is virtually connected to Vcc through the resistor, making it HIGH.

These are basic examples. More complex gates like OR, NAND, NOR, XOR, XNOR can also be built using a combination of transistors. Note that these are simple, idealized examples. Real-world circuits would require additional components to function reliably.