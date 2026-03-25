#### Harmonic Functions
- sine and cosine functions form the basis of harmony
- the cosine is a *phase shift* of the sine by pi/2: $$ cos(x) = sin(x+\pi/2) $$
- a sine wave with frequency *f* has angular frequency: $$ \omega = 2\pi f $$$$ y(t) = sin(2\pi f) = sin(\omega t) $$
###### string sound 
$$ f_n = n f_1 $$
$$ y(t) = \sum A_n sin(2\pi f_n t) $$
each summand:
$$ A_n sin(2\pi f_n t) $$
is called a *partial*.
if fn = nf1, we say the partial is *harmonic*.

if this condition is not met, the partial is *inharmonic*.
#### Discretized Sine Function
- if R is the sampling rate (so that T = 1/R is the time between samples), the n-th sample if a sine wave is: $$ y_n = sin(\frac{2\pi f n}{R}) $$ where $$ y_n = y(n/R) $$
Typically in freq. spectrum, amplitudes are given in decibels
To convert to ta partial, we need to convert dB to a linear gain factor
**Ex., f_1 = 550Hz; A_1 = -2.8dB **
$$ 10^{-2.8/20} = 0.72 $$
```
0.72 - dominant partial

f_2 = 1100Hz
A_2 = -5.8dB -> 10^(-5.8/20) = 0.51

y(t) = 0.72 sin(2 pi 550 t) + 0.51 sin(2 pi 1100 t)
```

###### Transposition: same amplitudes
**Ex., shift all frequencies by the same factor**
```
transpose so the dominant partial is now 275Hz

A_1' = 0.72
f_1' = 1/2 * 550 = 275Hz
A_2' = 0.51
f_2' = 1/2 * 1100 = 550Hz

```

