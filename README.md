# mdo NotATypeWriter
My version of the fantastic Adafruit Learning project "Not A Typewriter".

The original is here:
- https://learn.adafruit.com/not-a-typewriter
- Ruiz Brothers and Liz Clark

<img src="https://cdn-learn.adafruit.com/assets/assets/000/137/815/medium640/3d_printing_hero-ipad.jpg?1750171571" width="400" alt="Original Adafruit Learning Not A Typewriter">

**Table Of Contents**
* [Top](#mdo-notatypewriter "Top")
* [License](#license "License")

## Introduction
[Top](#mdo-notatypewriter "Top")<br>
The "Not A Typewriter" project was so great I had to make a copy for myself.

### Differences from Original Adafruit Learning Not A Typewriter
[Top](#mdo-notatypewriter "Top")<br>
Some parts were unavailable at this time and others I chose to do in a slightly different manner.
- The I2C Solenoid Driver https://www.adafruit.com/product/6318 was not available at the time I ordered
  - ... so I replaced it with a non-I2C version https://www.adafruit.com/product/970
- The original project includes files for a beautiful 3D-printed typewriter/project-box
  - ... I chose to use a "dollhouse" typewriter https://www.amazon.com/dp/B0B86HYR6P and some cardboard boxes and scrap I had on hand
  - <img src="https://github.com/Mark-MDO47/mdoNotATypeWriter/blob/master/resources/images/DollhouseTypewriter.png" width="200" alt="Dollhouse Typewriter">

### RP2040 and Dual USB
[Top](#mdo-notatypewriter "Top")<br>
The RP2040 is a new experience for me, as is the use of two USB interfaces. I gather that the "device" USB port is used to program the RP2040 and implemented by its native hardware USB facilities while the "host" USB port is implemented by software bit-banging, using one of the two M0 cores of the RP2040. Still learning about this.
- https://www.adafruit.com/product/5723	https://learn.adafruit.com/adafruit-feather-rp2040-with-usb-type-a-host
- https://github.com/adafruit/Adafruit-Feather-RP2040-USB-Host-PCB/blob/main/Adafruit_Feather_RP2040_USB_Host_PrettyPins.pdf

This area contains information about the dual USB usage.
- https://github.com/adafruit/Adafruit_TinyUSB_Arduino/tree/master/examples/DualRole

Here is a work-in-progress list of things I need to keep in mind regarding this Dual USB technique and the RP2040
- RP2040: "pio_usb.h" must not be included, otherwise pio-usb will be used as host controller

### Parts List - Work-in-Progress
[Top](#mdo-notatypewriter "Top")<br>

| Price (each) | Num | Description | URL |
| --- | --- | --- | --- |
| $17.50 | 1 | Adafruit Feather RP2040 with USB Type A Host | https://www.adafruit.com/product/5723 |
| $4.50 | 1 | Snap-on Enclosure for Adafruit Feather RP2040 USB Host | https://www.adafruit.com/product/6057 |
| $4.00 | 1 | ULN2803: 8 Channel Darlington Driver (Solenoid/Unipolar Stepper) - ULN2803A | https://www.adafruit.com/product/970 |
| $5.00 | 2 | Mini Push-Pull Solenoid - 5V | https://www.adafruit.com/product/2776 |
| $9.60 | 1 | Toyvian Dollhouse Miniature Typewriter Typewriter Mini Office Typewriter Tiny Wooden Typewriter Decor Miniature Antique Typewriter Classic Manual Typewriter Dollhouse Decor Accessories | https://www.amazon.com/dp/B0B86HYR6P |
| $5.00 | 1 | 2 PCS Small Call Bell, 2.56 Inch Service Bell, Ring Bell for Service, Dinner Bell, Counter Bell, Desk Bell | https://www.amazon.com/dp/B0DYDWRYZT |
| $0.75 | 1 | HiLetgo 10pcs 4 Channels IIC I2C Logic Level Converter Bi-Directional 3.3V-5V Shifter Module | https://www.amazon.com/HiLetgo-Channels-Converter-Bi-Directional-3-3V-5V/dp/B07F7W91LC |



## License
[Top](#mdo-notatypewriter "Top")<br>
I am using the MIT license for this project since that is what Adafruit Learning uses.

There may be code included that I have modified from other open sources (such as Arduino, Espressif, SparkFun, Seeed Studio, DFRobot, RandomNerds, etc.). These other sources may possibly be licensed using a different license model. In such a case I will include some notation of this. Typically I will include verbatim the license in the included/modified source code, but alternatively there might be a LICENSE file in the source code area that points out exceptions to the MIT License.
