# Introduction to Displays: LCDs and OLEDs

When it comes to display technologies, two of the most prevalent types in today's market are Liquid Crystal Displays (LCD) and Organic Light Emitting Diodes (OLED). 

## LCDs (Liquid Crystal Displays)

LCDs create images by modulating the light passing through a layer of liquid crystals. They are comprised of several layers: the backlight, the liquid crystal layer, and two polarizing filters. The liquid crystal layer is an array of tiny cells, each containing liquid crystals that can be oriented by applying an electric field. 

Here's a simplified explanation of how an image is created:

1. The backlight emits white light.
2. The light passes through the first polarizing filter.
3. The light passes through the liquid crystal cells. When voltage is applied, the liquid crystals rotate, changing the light's polarization.
4. The rotated light then passes through the second polarizing filter, which is oriented at 90 degrees to the first one. Depending on the rotation of the light, some of it is blocked by this filter.
5. The resulting image is then colored by passing through a layer of red, green, and blue filters.

## OLEDs (Organic Light Emitting Diodes)

OLEDs, on the other hand, create images by emitting light directly from organic molecules that glow when an electric current is applied. Unlike LCDs, OLEDs do not require a backlight, which allows them to be thinner and lighter than LCD displays.

The basic structure of an OLED display is as follows:

1. When an electric current is applied, electrons move from the cathode to the anode through the organic layers.
2. In the emissive layer, the electrons recombine with holes (the absence of electrons), releasing energy in the form of light.
3. The color of the light is determined by the type of organic molecule in the emissive layer. 

In terms of code, although the underlying hardware differs, the way you interact with an LCD or OLED from a software perspective is often quite similar, usually involving setting pixel colors on a framebuffer. Here's a simple example for setting a pixel on an imaginary 128x128 display:

```python
def set_pixel(framebuffer, x, y, color):
    if 0 <= x < 128 and 0 <= y < 128:
        framebuffer[y][x] = color
```

Understanding the differences between LCDs and OLEDs can help you optimize your software for the specific display type, such as taking advantage of OLED's ability to individually turn off pixels for true black and energy savings.