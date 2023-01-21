# Sprig Essentials

Useful functions to simplify the process of creating games and apps with Sprig.

_**This package is not affiliated with Sprig or HackClub in any form.**_

# Documentation

This package is intended to run on any type of `Raspberry Pi`.
Most focused on the `Raspberry Pi Pico H`.

## Display

This package assumes you're using the `ST7735` display and that you've installed `CircuitPython`.

The wiring diagram that this package assumes is intended for anyone using a Sprig, however, you can also wire this manually and achieve the same effect.

### Wiring Diagram

INSERT IMAGE HERE

### Imports

You will need to import the following to connect to the pins.

```python
import board
```

If you're using a Sprig, chances are the wiring is going to be the exact same through the board, so you can skip to [`quickStartDisplay()`](#quickstartdisplay()).

### `startBacklight()`

```python
def startBacklight(backlight_pin):
    # Create the digital output
    backlight = digitalio.DigitalInOut(backlight_pin)
    # Set it as output
    backlight.direction = digitalio.Direction.OUTPUT
    # Turn it on
    backlight.value = True
    return backlight
```

This function takes in the pin number where the `LITE` pin on the display is connected to (formatted like so: `board.GP0`), and turns the backlight on.

It returns an object of type `digitalio.DigitalInOut` which will be used in other functions.

#### Example

```python
import board
backlight = startBacklight(board.GP17)
```

### `createSPI()`

```python
def createSPI(clock_pin, MOSI_pin, MISO_pin):
    spi = busio.SPI(clock=clock_pin, MOSI=MOSI_pin, MISO=MISO_pin)
    return spi
```

This function takes in 3 pin numbers (formatted like so: `board.GP0`) and creates an SPI which will be used when creating a display bus.

It returns an object of type `busio.SPI`.

#### Example

```python
import board
spi = createSPI(board.GP18, board.GP19, board.GP16)
```
