# Pirate Audio

Pirate Audio is a range of audio output boards for the Raspberry Pi.

Each board includes an ST7789 240x240 pixel LCD display, four buttons and some form of audio output (except for the Pirate Audio: Dual Mic which offers two microphones instead of audio output).


## Hardware

* st7789 display (see [Python library](https://github.com/pimoroni/st7789-python))
* four buttons, active low connected to BCM 5, 6, 16, and 24 (A, B, X, Y respectively)

## Installation

You'll need to add the following lines to `/boot/config.txt` to get audio up and running:

```
dtoverlay=hifiberry-dac
gpio=25=op,dh
```

You can also disable onboard audio if you're not going to use it, this sometimes helps applications find the right audio device without extra prompting:

```
dtparam=audio=off
```

And for Dual Mic, you'll need:
```
dtoverlay=adau7002-simple
```
(See [Clip Recorder](./clip-recorder) for further example of use.)


```
sudo apt update
sudo apt install python-rpi.gpio python-spidev python-pip python-pil python-numpy
```

And then you'll need the st7789 library:

```
sudo pip install st7789
```

For more display examples see the [st7789 Python library examples](https://github.com/pimoroni/st7789-python/tree/master/examples).

