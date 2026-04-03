## Re: sound modeling
###### 1st attempt: use partials with constant amplitudes
$$ y(t) = \sum_{n=1}^{N}A_n sin(2\pi f_n t) $$
```
f1 = 1001Hz
A1 = 10^(-20.8/20) ~= 0.0912

f2 = 5567Hz
A2 = 10^(-27.5/20) ~= 

f3 = 1138Hz
A3 = 10^(-31.1/20) ~= 0.0279

f4 = 1496Hz
A4 = 10^(-32.8/20) ~= 0.0209


```

###### 2nd attempt: use partials with envelopes
$$  y(t) = \sum_{n=1}^{N}A_n(t) sin(2\pi f_n t)  $$
how do we do envelopes?
try to fit using... adsr/exponential/exponential-sine
```
envelope at 1001Hz (exponential)
(1) max amplitude: -11.207dB -> 10^(-11.207/20) ~= 0.2752
(2) half life (time to half on amplitude): 0.479 seconds

envelope at 1138Hz (exponential-sine)
max ampl.: 10^(-18.426/20) ~= 0.1199
half life: 0.306s
sine period: 0.424s

envelope at 5567Hz (ADSR)
max ampl.: ~= -0.2818


```