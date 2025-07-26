# My version of Adafruit Learning USB_Host_Not_A_Typewriter
The "Not A Typewriter" project was so great I had to make a copy for myself.

**Table Of Contents**
* [Top](#my-version-of-adafruit-learning-usb_host_not_a_typewriter "Top")
* [Attributions](#attributions "Attributions")
* [My Modifications](#my-modifications "My Modifications")
* [License](#license "License")

## Attributions
[Top](#my-version-of-adafruit-learning-usb_host_not_a_typewriter "Top")<br>
This code is derived from Adafruit Learning "Not A Typewriter". The original is here:

- https://learn.adafruit.com/not-a-typewriter
- Ruiz Brothers and Liz Clark

I am not sure if I am required to provide Attribution to Adafruit and to Liz Clark (author of the code) but I am happy to do it!

## My Modifications
[Top](#my-version-of-adafruit-learning-usb_host_not_a_typewriter "Top")<br>
I am using the USB Host version of the code. In this version the keyboard connects to the Feather via a "host-mode" USB-A port and keystrokes are forwarded toe the "device-mode" USB-C port while also affecting the solenoids to give sound effects.

<img src="https://cdn-learn.adafruit.com/assets/assets/000/137/815/medium640/3d_printing_hero-ipad.jpg?1750171571" width="400" alt="Original Adafruit Learning Not A Typewriter">

I am using a non-I2C solenoid driver instead of the I2C version that the original code expects.
- https://www.adafruit.com/product/970

This will be my first significant project using CircuitPython, although I have done a fair bit of Python coding. Fortunately I don't think the changes I will want to make will require any drastic coding effort.

## License
[Top](#my-version-of-adafruit-learning-usb_host_not_a_typewriter "Top")<br>
The original Adafruit Learning code uses the MIT license, so I am allowed to modify it. 




