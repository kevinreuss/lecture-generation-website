# Fundamentals of Semiconductor Physics

Semiconductors are materials that have properties of both conductors and insulators. They are key components in many electronic devices due to their unique properties.

## Energy Bands

In semiconductors, energy bands are crucial. The two main bands are the **Valence Band**, the highest range of electron energies where electrons are normally present at absolute zero temperature, and the **Conduction Band**, the band of electron energy above the valence band where electrons can move freely.

The gap between these two bands is called the **Band Gap** or **Energy Gap**. The size of the energy gap determines whether a material is a conductor, insulator, or semiconductor.

## Intrinsic Semiconductors

An **Intrinsic Semiconductor** is a pure semiconductor with no impurity. Here, the number of free electrons (n) is equal to the number of holes (p). Silicon and germanium are common intrinsic semiconductors.

Example:

```python
def intrinsic_concentration(T, Eg):
    """
    T : Absolute temperature (Kelvin)
    Eg : Band Gap energy (eV)
    """
    k = 8.6173e-5 # Boltzmann constant (eV/K)
    return (2 * (2*3.14159*k*T)**(3/2) * (1.05e10)**3 * exp(-Eg/(2*k*T)))
```

## Extrinsic Semiconductors

**Extrinsic Semiconductors** are created by adding impurity atoms to an intrinsic semiconductor. This process is known as **Doping**. The impurity atoms create additional energy levels within the bandgap.

There are two types of extrinsic semiconductors: **N-Type** (where free electrons are majority carriers) and **P-Type** (where holes are majority carriers).

Example:

```python
def extrinsic_concentration(T, Nd, Na, ni):
    """
    T : Absolute temperature (Kelvin)
    Nd : Donor concentration
    Na : Acceptor concentration
    ni : Intrinsic concentration
    """
    n = ((Nd - Na) / 2) + sqrt((((Nd - Na) / 2)**2) + ni**2)
    p = ni**2 / n
    return n, p
```

## Carrier Transport

Electrons and holes move through a semiconductor due to **Drift** (motion under an electric field) and **Diffusion** (motion from high concentration to low concentration).

The collective motion of these carriers under the influence of an external electric field results in current in a semiconductor.

## Conclusion

Understanding the fundamentals of semiconductor physics is crucial for software engineers working on electronic devices or semiconductor manufacturing processes. This foundation enables you to understand how electronic components function and how to optimize your software for these components.