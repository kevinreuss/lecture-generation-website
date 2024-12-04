# Real-Time Audio Processing Algorithms

Real-time audio processing algorithms deal with the real-time transformation of audio signals. The goal is to execute these algorithms within a time frame that seems immediate to the user.

## FFT (Fast Fourier Transform)

FFT is a very efficient algorithm for computing the Discrete Fourier Transform (DFT) and its inverse. It's widely used in real-time audio processing to convert a signal from its original domain (often time or space) to a representation in the frequency domain and vice versa.

```python
import numpy as np
import scipy.fftpack

# Sample rate and duration
fs = 44100  # sample rate 
T = 1.0    # seconds
t = np.linspace(0, T, int(T*fs), False)  # time variable

# generate a 440 Hz sinusoidal signal
x = 0.5*np.sin(2*np.pi*440*t)

# Perform FFT
yf = scipy.fftpack.fft(x)
xf = np.linspace(0.0, 1.0/(2.0*T), int(T*fs/2))

# Only take the positive half of the spectrum
yf = 2.0/int(T*fs) * np.abs(yf[0:int(T*fs/2)])
```

## FIR (Finite Impulse Response) Filters

FIR filters are a type of digital filters which are widely used in real-time audio processing applications. They are characterised by a finite duration response to an impulse input. 

```python
import numpy as np
import scipy.signal as signal

# Number of taps and cut off frequency
numtaps = 64
cutoff = 0.1

# Design the filter
taps = signal.firwin(numtaps, cutoff)

# Filter the signal
filtered_signal = signal.lfilter(taps, [1.0], x)
```

## Real-Time Convolution

Convolution is a mathematical operation that merges two signals to form a third signal. In the context of audio processing, it's often used to apply the impulse response of a system to an input signal.

```python
import numpy as np
from scipy.signal import convolve

# Generate an impulse response
h = signal.firwin(numtaps, cutoff)

# Convolve the input signal with the impulse response
y = convolve(x, h, mode='same')
```

These are basic building blocks of real-time audio processing. Other techniques such as spectral subtraction, phase vocoding, and dynamic range compression build upon these foundations. For more advanced explorations, consider learning about machine learning applications in audio processing, such as audio classification and music synthesis.