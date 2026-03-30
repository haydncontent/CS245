###### Ex. bottle.wav -sound modeling-
###### 1st attempt: using dominant partials
1st dominant partial:
  f1 = 1001Hz
  A1 = -20.8dB -> 0.0912

2nd dominant partial:
  f2 = 1138Hz
  A2 = -31.1dB -> -0.0279

problem... did not capture the dynamics with such a small number of partials
###### 2nd attempt: use dynamic envelopes for amplitude
...
? extract the envelope at a particular frequency
break into blocks on the interval 0-L
0 to h, h to 2h, 2h to 3h
$$ A_n(0) = \int_{0}^{h} x(t) sin (\frac{n\pi t}{L})dt $$

