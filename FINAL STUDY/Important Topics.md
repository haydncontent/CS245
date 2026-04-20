#### week 1
dc offset & normalization
#### week 2
bit res (float & i16 & ui8)
SNR
#### week 3
WAVE format 
#### week 4
speed-up factors
	- playback speed-up (no change in R)
		- y_n = x(speed-up)(n) = solution
pitch 
    - f_new = 2^(cents / 1200) * f_old
    - m = 2^(cents / 1200)
resampling
	- m = f_old / f_new
	
interpolation
	x_n.m = x_n * (0.m)(x_n+1 - x_n)
#### week 5
MIDI short message 
	convert from midi note to a freq.
	- 440 * 2^(n - 69 / 12)
#### week 8
y = e^(-kt)
k = decay rate (s^-1)
from half life:
	half life lambda = 0.3s
	$$ y(\lambda) = 1/2\text{   } $$
	$$ 1/2 = e^{-kt} $$
	sub lambda for t and solve with nat log
follow up... at what time after start does the envelope have values -10dB?
gain = 10^(-dB/20)
e^(-kt) = 10^(-10/20) -> solve for t
	decay envelopes
	**decay rate**   - k
	**decay factor** - e^(-k/R)
	**decay time**   - t = 96/20 log(10) / k
	continuous calculation - use decay factor
#### week 9
envelopes - a d s r
wavetable synth incrtemental algorithm - arguments to track
a = attack duration
d = decay *time* (0dB to -96dB)
s = sustain level
r = release *time*

#### week 10
modulation & mod wheel
$$ sin(2{\pi}f_vt) = \text{LFO element - Low Freq. Oscillator}$$
#### week 11
discritized sine function
$$ y_n = sin(\frac{2\pi f n}{R}) $$
 where $$ y_n = y(n/R) $$
 recurrence relation & sine lookup
 $$ R = \text{sampling rate} $$
$$ y_0=0 $$
$$ y_1=sin(\frac{2\pi f}{R}) $$
$$ y_n = \alpha y_{n-1}) - y_{n-2} $$
$$ \alpha = 2cos(\frac{2\pi f}{R}) $$
#### week 12
fourier sine series & sound modeling
every continous function on interval 0-L can be expressed as a sum of sines $$ f(t) = \sum_{n=1}^{\infty} A_nsin(\frac{n\pi t}{L}) $$
#### week 13
FM synthese & Bessel functions