# mdo NotATypeWriter
My version of the fantastic Adafruit Learning project "Not A Typewriter".

The original is here:
- https://learn.adafruit.com/not-a-typewriter
- Ruiz Brothers and Liz Clark

I am happy to provide Attribution to Adafruit and to the Ruiz Brothers (3D design) and to Liz Clark (author of the code) !

<img src="https://cdn-learn.adafruit.com/assets/assets/000/137/815/medium640/3d_printing_hero-ipad.jpg?1750171571" width="400" alt="Original Adafruit Learning Not A Typewriter">

**Table Of Contents**
* [Top](#mdo-notatypewriter "Top")
* [Introduction](#introduction "Introduction")
* [Differences from Original Adafruit Learning Not A Typewriter](#differences-from-original-adafruit-learning-not-a-typewriter "Differences from Original Adafruit Learning Not A Typewriter")
* [RP2040 and Dual USB](#rp2040-and-dual-usb "RP2040 and Dual USB")
* [The Code - Derived from Adafruit Learning](#the-code-\--derived-from-adafruit-learning "The Code - Derived from Adafruit Learning")
* [Schematic](#schematic "Schematic")
* [Parts List - Work-in-Progress](#parts-list-\--work\-in\-progress "Parts List - Work-in-Progress")
* [License](#license "License")

## Introduction
[Top](#mdo-notatypewriter "Top")<br>
The "Not A Typewriter" project was so great I had to make a copy for myself.

## Differences from Original Adafruit Learning Not A Typewriter
[Top](#mdo-notatypewriter "Top")<br>
Some parts were unavailable at this time and others I chose to do in a slightly different manner.
- The I2C Solenoid Driver https://www.adafruit.com/product/6318 was not available at the time I ordered
  - ... so I replaced it with a non-I2C version https://www.adafruit.com/product/970
- The original project includes files for a beautiful 3D-printed typewriter/project-box
  - ... I chose to use a "dollhouse" typewriter https://www.amazon.com/dp/B0B86HYR6P and some cardboard boxes and scrap I had on hand
  - <img src="https://github.com/Mark-MDO47/mdoNotATypeWriter/blob/master/resources/images/DollhouseTypewriter.png" width="200" alt="Dollhouse Typewriter">

Here is an image of most of the cast of characters for this project.<br>
<img src="https://github.com/Mark-MDO47/mdoNotATypeWriter/blob/master/resources/images/CastOfCharacters_NOT.jpg" width="500" alt="My cast of characters for Not A Typewriter">

## RP2040 and Dual USB
[Top](#mdo-notatypewriter "Top")<br>
The RP2040 is a new experience for me, as is the use of two USB interfaces. I gather that the "device" USB port is used to program the RP2040 and implemented by its native hardware USB facilities while the "host" USB port is implemented by software bit-banging, requiring one of the two M0 ARM cores of the RP2040 and both PIO peripherals. Still learning about this.
- https://www.adafruit.com/product/5723	https://learn.adafruit.com/adafruit-feather-rp2040-with-usb-type-a-host
- https://github.com/adafruit/Adafruit-Feather-RP2040-USB-Host-PCB/blob/main/Adafruit_Feather_RP2040_USB_Host_PrettyPins.pdf

This area contains information about the dual USB usage.
- https://github.com/adafruit/Adafruit_TinyUSB_Arduino/tree/master/examples/DualRole

Here is a work-in-progress list of things I need to keep in mind regarding this Dual USB technique and the RP2040.

For Arduino-style programming:
- RP2040: "pio_usb.h" must not be included, otherwise pio-usb will be used as host controller

For CircuitPython-style programming:
- nothing yet

## The Code - Derived from Adafruit Learning
[Top](#mdo-notatypewriter "Top")<br>
Here is a link to the area with my version of the code and a description of the changes I made.
- https://github.com/Mark-MDO47/mdoNotATypeWriter/blob/master/code/USB_Host_Not_A_Typewriter/README.md

## Schematic
[Top](#mdo-notatypewriter "Top")<br>
Below is the schematic for my version of the Not A Typewriter project.
- The main difference from the original version is the use of the ULN2803A chip instead of the I2C Solenoid Driver module
  - My favorite explanation of how to use ULN2803A are posts from pcmanbob starting at "Aug 15, 2023 9:13 am": https://forums.raspberrypi.com/viewtopic.php?t=354993
- I chose to use some regular GPIO pins to control the solenoids instead of the ones on the I2C connector
  - Saving the I2C connector in case I have another use for it
- I have some LEDs that flash when the solenoids activate and a switch that disables the solenoids but allows the LEDs to still work. This lets me type quietely when my family is asleep.

<img src="https://github.com/Mark-MDO47/mdoNotATypeWriter/blob/master/resources/images/mdoNotATypeWriter_schem.png" width="500" alt="Schematic Diagram">

Here is an assembly diagram. I will probably add wire-lengths as I determine the physical layout.
<img src="https://github.com/Mark-MDO47/mdoNotATypeWriter/blob/master/resources/images/mdoNOT_assy.png" width="500" alt="Schematic Diagram">

At first I had a circuit mistake: connected ULN2803A COM with GROUND instead of +5V. After spending an unjustifiable amount of time, I corrected it. The following shows a depiction similar to my debugging efforts.
- https://x.com/MakerIO/status/1953442023186305311

With the addition of the LEDs, resistors, and switch it got complicated enough to use a StripBoard for part of the circuit. By not including the Feather RP2040 on the StripBoard I was able to keep the board quite small. Here is an indication of how it is assembled.
- Squares starting with F are connections from the Feather RP2040, SOL from the solenoids, SW a connection to the switch, R and C for resistor and capacitor, L for LED, and W for wire.
- The center dark area is the ULN2803A.

| Connections | Image |
| --- | --- |
| <img src="https://github.com/Mark-MDO47/mdoNotATypeWriter/blob/master/resources/images/mdoNOT_StripPerfBoard.png" width="200" alt="StripBoard Connections"> | <img src="https://github.com/Mark-MDO47/mdoNotATypeWriter/blob/master/resources/images/mdoNOT_image_StripPerfBoard.png" width="200" alt="StripBoard Picture"> |

## Parts List - Work-in-Progress
[Top](#mdo-notatypewriter "Top")<br>

| Price (each) | Num | Description | URL or similar |
| --- | --- | --- | --- |
| $17.50 | 1 | Adafruit Feather RP2040 with USB Type A Host | https://www.adafruit.com/product/5723<br>https://learn.adafruit.com/adafruit-feather-rp2040-with-usb-type-a-host<br>https://github.com/adafruit/Adafruit-Feather-RP2040-USB-Host-PCB/blob/main/Adafruit_Feather_RP2040_USB_Host_PrettyPins.pdf |
| $9.60 | 1 | Toyvian Dollhouse Miniature Typewriter Typewriter Mini Office Typewriter Tiny Wooden Typewriter Decor Miniature Antique Typewriter Classic Manual Typewriter Dollhouse Decor Accessories | https://www.amazon.com/dp/B0B86HYR6P |
| $2.50 | 1 | 2 PCS Small Call Bell, 2.56 Inch Service Bell, Ring Bell for Service, Dinner Bell, Counter Bell, Desk Bell | https://www.amazon.com/dp/B0DYDWRYZT |
| $4.00 | 1 | ULN2803: 8 Channel Darlington Driver (Solenoid/Unipolar Stepper) - ULN2803A | https://www.adafruit.com/product/970<br>https://www.openhacks.com/uploadsproductos/uln2803a.pdf<br>https://www.ic-components.com/blog/Your-Guide-to-ULN2803A-Transistor-Array.jsp |
| N/A | 1 | 100uF 16V Electrolytic capacitor | https://www.amazon.com/dp/B081PT78Y5 |
| $5.00 | 2 | Mini Push-Pull Solenoid - 5V | https://www.adafruit.com/product/2776 |
| $0.70 | 2 | 10 PCS (5@M 5@F) Upgraded Tiny Whoop JST-PH 2.0 Male and Female Connector Cable for Battery | https://www.amazon.com/dp/B07NWD5NTN |
| $0.95 | 1 | Breadboard-friendly SPDT Slide Switch | https://www.adafruit.com/product/805 |
| $0.15 | 2 | LED Green Diffused 3mm Round | https://www.digikey.com/en/products/detail/w%C3%BCrth-elektronik/151031VS06000/4489988 |
| $0.10 | 2 | 330-Ohm 1/4 watt through-hole resistors | https://www.digikey.com/en/products/detail/yageo/CFR-25JB-52-330R/1636 |
| $2.00 | 1 | small StripBoard | https://www.amazon.com/dp/B0778G64QZ |
| ??? | * | various angle brackets, scrap wood, screws and bolts | from my parts bin |

## License
[Top](#mdo-notatypewriter "Top")<br>
I am using the MIT license for this project since that is what Adafruit Learning uses.

There may be code included that I have modified from other open sources (such as Arduino, Espressif, SparkFun, Seeed Studio, DFRobot, RandomNerds, etc.). These other sources may possibly be licensed using a different license model. In such a case I will include some notation of this. Typically I will include verbatim the license in the included/modified source code, but alternatively there might be a LICENSE file in the source code area that points out exceptions to the MIT License.
