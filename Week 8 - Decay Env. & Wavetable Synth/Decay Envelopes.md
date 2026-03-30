#### Wavetable Synthesis
- uses one or more pre-recorded audio samples
- resampling is used to sound a target pitch
- articulate the note 
	- sustain: use loop points
	- dynamics: use envelope

#### Envelope
apply multiplicatively to signal
###### Exponential Decay
k = decay rate (units: s^-1)
y = e^(-kt)

How do we specify the decay rate?
- one way is half-life: time for amplitude to reach half of its current value

Remark: the half-life is a constant 

**Ex., decay**
```
half-life is l = 0.3s
what is the decay rate?

y(t) = e^(-kt)
y(0) = 1
y(l) = 1/2

1/2 = y(l) = e^(-lk)
e^(lk) = 1/2
ln(e^(-lk)) = ln(1/2)
-lk * ln(e) = ln(1) - ln(2)
-lk = -ln(2)

l * k = ln(2) 
k = ln(2)/l 
ln(2)/0.3 ~= 2.31 s^-1
```
**Follow up,**
```
at what time after envelope starts does it have the value -10dB ?

g = 10^(-dB/20)

e^(-kt) = 10^(-10/20)
ln(e^(-kt)) = ln(10^(-10/20))
-kt = -10/20ln(10)
t = -10/20 * ln(10)/k
t = -1/2 * ln(10) * 2.31 ~= 0.498s
```

###### Another Way to Decay
Recall: for 16-bit audio, SNR is 96dB.

So $$ 10^{-96/20}$$is the "effective zero" for 16-bit audio (-96dB)
The *decay time* is the time to go from unity gain to the effective zero.

*decay rate:* k
*decay time:* 0dB to -96dB
*decay factor:* 

**Ex., decay time = 7.42s = T**
```
decay rate = ?

e^(-kT) = 10^(-96/20)
ln(e^(-kT)) = ln(10^(-96/20))
-kT = -96/20 * ln(10)
k = 96/20 * ln(10)/T
k ~= 1.49 s^-1

how long does it take the envelope to go from 0.8 to 0.3

0.8e^(-kt) = 0.3
e^(-1.49t) = 0.3/0.8
ln(e^(-1.49t)) = ln(0.3/0.8)
-1.49t = ln(0.3/0.8)
t = -(ln(0.3) - ln(0.8))/1.49
t ~= 0.656s
```

the *decay factor* is the ratio of envelope values between successive samples.

R = sampling rate
y(t) = e^(-kt) ->

decay factor:
$$y(t + 1/R) = e^{-kt+k/R}$$
$$y(t + 1/R) = y(t) * e^{-k/R}$$


