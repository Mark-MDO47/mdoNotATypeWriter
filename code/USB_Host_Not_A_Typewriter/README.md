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

I am happy to provide Attribution to Adafruit and to Liz Clark (author of the code) !

## My Modifications
[Top](#my-version-of-adafruit-learning-usb_host_not_a_typewriter "Top")<br>
I am using the USB Host version of the code. In this version the keyboard connects to the Feather RP2040 via a "host-mode" USB-A port and keystrokes are forwarded to the "device-mode" USB-C port (and on to the PC) while also affecting the solenoids to give sound effects. See below for an image of the original version of this from Adafruit Learning.<br>
<img src="https://cdn-learn.adafruit.com/assets/assets/000/137/815/medium640/3d_printing_hero-ipad.jpg?1750171571" width="400" alt="Original Adafruit Learning Not A Typewriter - USB Host">

I am using a non-I2C solenoid driver instead of the I2C version that the original code expects.
- https://www.adafruit.com/product/970

This will be my first significant project using CircuitPython, although I have done a fair bit of Python coding on PCs. Fortunately I don't think my changes will require any drastic coding effort.

It appears that the main point of the change will be in the strike_key_solenoid() and ring_bell_solenoid() routines. The rest will just be initializing, tidying up, and perhaps adjusting some of the configuration parameters to my liking.<br>
Here is what the original code looks like.

```Python
def strike_key_solenoid():
    """Activate the key strike solenoid briefly"""
    noid_1.value = True
    time.sleep(SOLENOID_STRIKE_TIME)
    noid_1.value = False

def ring_bell_solenoid():
    """Activate the bell solenoid briefly"""
    noid_2.value = True
    time.sleep(SOLENOID_STRIKE_TIME)
    noid_2.value = False
```

I will need to initialize some I/O pins
- NOTE: the ULN2803 chip appears to be inverting, so I might need to swap True/False below.
- Will do some experiments...
- https://cdn-shop.adafruit.com/datasheets/ULN2803A.pdf

```Python
import digitalio

# I will use the same SCL/SDA pins so I can use the I2C connector
noid1_pin = digitalio.DigitalInOut(board.D2)
noid1_pin.direction = digitalio.Direction.OUTPUT
noid1_pin.value = False

noid2_pin = digitalio.DigitalInOut(board.D3)
noid2_pin.direction = digitalio.Direction.OUTPUT
noid2_pin.value = False
```

And then replace the two routines.

```Python
def strike_key_solenoid():
    """Activate the key strike solenoid briefly"""
    noid1_pin.value = True
    time.sleep(SOLENOID_STRIKE_TIME)
    noid1_pin.value = False

def ring_bell_solenoid():
    """Activate the bell solenoid briefly"""
    noid2_pin.value = True
    time.sleep(SOLENOID_STRIKE_TIME)
    noid2_pin.value = False
```


## License
[Top](#my-version-of-adafruit-learning-usb_host_not_a_typewriter "Top")<br>
The original Adafruit Learning code uses the MIT license, so I am allowed to modify it. 




