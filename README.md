# Audio Effects

Multiple types of audio effects will be described and implemented in python.

**Table of Contents**

- [Getting Started](#getting-started)
- [Playing Files](#playing-files)
- [Using Pyaudio](#using-pyaudio)
- [Effects](#effects)
- [Blocking](#blocking)
- [Callback](#callback)
- [Visualization with Pyplot](#visualization-with-Pyplot)

## Getting Started

All of these implementations will be in python and therefore will utilize the pyaudio module.
I would suggest to use python 2.7 since some of the other modules I will be using will not be compatible with the 3+ version.
By default, ``pip`` and ``setuptools`` will already be installed however they will need to be upgraded: <br>

**For windows:** <br>
```sh
python -m pip install -U pip setuptools
```

**For Linux or OSX:** <br>
```sh
sudo pip install -U pip setuptools
```

**For those with faith:** <br>
You can download this [python script](https://github.com/Souloist/Audio-Effects/blob/master/pip-lazy/get-pip.py) which should install pip upon running:
```sh
python get-python.py
```

Now, in order to install the pyaudio module simply type the following into the terminal:
```sh
sudo pip install pyaudio
```

If you run into an error, you may have to install manually by downloading the corresponding wheel and using pip.
The wheels can be found at http://www.lfd.uci.edu/~gohlke/pythonlibs/ <br>

In order to install, simply download the wheel and move it to your current directory. Then type:
```sh
pip install (Name of your wheel).whl
```

## Playing files

Initialize:
```python
p = pyaudio.PyAudio()

stream = p.open(format      = pyaudio.paInt16,
                channels    = num_channels,
                rate        = Fs,
                input       = False,
                output      = True )

```

Reading/Editing/Playing:
```python
input_string = wf.readframes(1)          # Get first frame
while input_string != '':

    # Convert string to number
    input_tuple = struct.unpack('h', input_string)  # One-element tuple
    input_value = input_tuple[0]                    # Extract number from tuple

    # Compute output value
    output_value = gain * input_value               # Multiple value by set gain

    # Convert output value to binary string
    output_string = struct.pack('h', output_value)  

    # Write output value to audio stream
    stream.write(output_string)                     

    # Get next frame
    input_string = wf.readframes(1) 
```

## Using Pyaudio

## Effects

- [Amplitude modulation](https://github.com/Souloist/Audio-Effects/tree/master/Effects/Amplitude_Modulation)
- [Complex Amplitude modulation](https://github.com/Souloist/Audio-Effects/tree/master/Effects/Complex_Amplitude_Modulation)
- [Delay](https://github.com/Souloist/Audio-Effects/tree/master/Effects/Simple_delay)
- [Delay with Feedback](https://github.com/Souloist/Audio-Effects/tree/master/Effects/delay_with_feedback)
- [Ping-pong effect](https://github.com/Souloist/Audio-Effects/tree/master/Effects/Ping_Pong_Effect)
- [Virbrato](https://github.com/Souloist/Audio-Effects/tree/master/Effects/Vibrato)

## Blocking

## Callback

## Visualization with Pyplot
