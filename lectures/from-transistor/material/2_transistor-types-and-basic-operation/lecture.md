# Transistor Types and Basic Operation

Transistors, the basic building blocks of electronic devices, come in various types. The main types include Bipolar Junction Transistors (BJT), Junction Field Effect Transistors (JFET), and Metal Oxide Semiconductor Field Effect Transistors (MOSFET).

## Bipolar Junction Transistors (BJT)
BJTs have three layers of semiconductor material with two PN junctions. It has three terminals: emitter, base, and collector. The base current IB controls the collector current IC.

Example of BJT NPN Transistor Operation:

```c
float Vbe = 0.7; // Base-emitter voltage
float Vcc = 12.0; // Supply voltage
float Rb = 10000; // Base resistance
float Re = 1000; // Emitter resistance
float beta = 100; // Base current amplification factor

float Ib = (Vcc - Vbe) / Rb; // Base current
float Ie = (beta + 1) * Ib; // Emitter current
float Ic = Ie - Ib; // Collector current
```

## Junction Field Effect Transistors (JFET)
A JFET operates by controlling the current between two points: source and drain. It has three terminals: gate, source, and drain. The gate voltage VG controls the drain current ID.

Example of JFET operation:

```c
float Vgs = -1.0; // Gate-source voltage
float Idss = 10.0; // Saturation current
float Vp = -4.0; // Pinch-off voltage

float Id = Idss * (1 - Vgs/Vp)^2; // Drain current
```

## Metal Oxide Semiconductor Field Effect Transistors (MOSFET)
A MOSFET operates by varying the width of a channel along which charge carriers flow. It has four terminals: gate, source, drain, and body. The gate voltage VG controls the drain current ID.

Example of MOSFET operation:

```c
float Vgs = 3.0; // Gate-source voltage
float Vth = 1.0; // Threshold voltage
float Kn = 0.5; // Transconductance parameter
float Vds = 5.0; // Drain-source voltage

if (Vgs > Vth) {
    float Id = Kn * (Vgs - Vth)^2; // Drain current in saturation
} else {
    float Id = 0; // Drain current in cutoff
}
```
Remember, these are simplified models of transistor operation. In reality, other factors such as temperature, frequency, and device construction can significantly affect the behavior of transistors.