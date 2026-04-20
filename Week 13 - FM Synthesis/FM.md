#### Recap
$$ y(t) = sin ( 2 \pi f_c t + \alpha_msin (2\pi f_m t) ) $$
f_c = carrier
f_m = modulator frequency
a_m = amplitude of modulation

$$ \sum_{n \in Z} J_n(\alpha_m) sin(2 \pi (f_c + nf_m) t) $$
$$J_n = \text{n-th order Bessel function}$$
 
$$J_{-n}(t) = (-1)^n J_n(t) $$
recurrence relation:
$$ J_{n+1}(t) = \frac{2n}{t}J_n(t) - J_{n-1}(t) $$
###### Example
```
f_c = 200Hz
f_m = 150Hz
a_m = 1

J0(1) ~= 0.7652
J1(1) ~= 0.4401

for n=0 :
F0 = 200 + (0 * 150) = 200Hz
A0 = J0(1) ~= 0.7652 -> 20log(0.7652) ~= -2.3245dB

for n=1 :
F1 = 200 + (1 * 150) = 350Hz
A1 = J1(1) ~= 0.4401 -> 20log(0.4401) ~= -7.13dB

for n=-1
F-1 = 200 + (-1 * 150) = 50Hz
A-1 = |J-1(1)| ~= 0.4401 -> 20log(0.4401) ~= -7.13dB



```