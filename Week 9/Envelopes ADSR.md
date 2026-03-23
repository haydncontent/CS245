**Re:** exponential decay envelopes
$$ y(t) = e^{-kt}$$
$$ k = \text{decay rate (units: }s^{-1})$$
**Related quantities**
$$ \lambda = \text{half life (time to decay to 1/2 of current envelope value)}$$
$$ \tau = \text{decay time (time to decay from 0dB to -96dB)} $$
$$ \rho = \text{decay factor (ratio of envelope values between successive time steps)} $$
$$ \rho = e^{-k/R} $$

**Ex., Exponential decay envelope with decay rate k = 0.8 s^-1, sampled at rate R = 5Hz**
```
k = 0.8
R = 5

decay factor (rho) = e^(-k/R) ~= 0.8521

first four envelope values
y(0)   = e^0             = 1
y(1/5) = (rho) * y(0)   ~= 0.8521
y(2/5) = (rho) * y(1/5) ~= 0.8521 * 0.8521 ~= 0.7261
y(3/5) = (rho) * y(2/5) ~= 0.6188
```

###### Exponential Sine envelope
$$ y(t) = e^{-kt}sin(2\pi ft) $$
$$ f = \text{LFO frequency (optional parameter)}$$
... variation on exponential decay used for bell-like sounds

#### ADSR Envelope 
**Attack - Decay - Sustain - Release**
![[Pasted image 20260302153905.png|452]]

**ADSR**
- common envelope used in digital audio
- attack; decay; sustain; release **}** four phases of the envelope

![[sd.png]]
###### Incremental update algorithm for ADSR with linear ramps
keep track of:
- current value = e
- current envelope phase = P

```
R = rate

-- Attack Phase -- 
e = 0, P = A (attack)
A = time (s) of the attack phase
increment e by 
dA = 1/aR 
!until! e >= 1

-- Decay Phase --
e = 0, P = D (decay)
D = time (s) of the decay phase
decrement e by 
dD = (1 - (sustain_level)) / (D * R) 
!until! e <= sustain_level

-- Sustain Phase --
e = s (sustain_level), P = S (sustain)
e stays unchanged at this value s 
!until! told to enter release phase 

-- Release Phase --
P = R (release)
R' = time (s) of release phase
decrement e by 
dR = s / (R R`)
!until! e <= 0
set e = 0
```

###### DLS-Style ADSR envelope
**DLS** - downloadable sound font (standardization for wavetable synths)
- uses exponential decay envelopes for decay and release phases

**Parameters**
a = duration (seconds) of attack phase
d = decay *time* (seconds) ... (not duration) ... 0dB to -96dB
s = sustain level
r = release *time* (seconds) ... (not duration) ... 0dB to -96dB







