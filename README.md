# splatter

A fork of [shinyquagsire23/Switch-Fightstick](https://github.com/shinyquagsire23/Switch-Fightstick), cleaned up and modified for Splatoon 3.

splatter is only tested on my Arduino Uno R3. Support for other platforms isn't guaranteed.

## Installation

Assuming you're on Linux, you'll need:

- a Nintendo Switch with internet access and Splatoon 3
- a board that can run splatter
- a Nintendo Switch dock (to connect the arduino to)
- Python 3 (to generate the image)
- `avr-gcc` and `avr-libc` (to build the code)
- `dfu-programmer` (to flash the code)

```sh
# convert the image into a .c file - 1bit, 320x120
$ python3 png2c.py /path/to/image.png

# build the project
# if needed, change MCU in the Makefile to match your board
$ make

# connect the arduino to your PC, and reset the 8u2/16u2
# see https://docs.arduino.cc/hacking/software/DFUProgramming8U2

# flash the board
$ sudo dfu-programmer atmega16u2 erase
$ sudo dfu-programmer atmega16u2 flash Joystick.hex
```

Now, do the following:
- Open the canvas menu
- Press L to switch to the small pen
- Using the left stick/D-pad, move to the top left of the canvas
- Unpair your controller (press the SYNC button)
- Plug the Arduino into your Switch's dock
