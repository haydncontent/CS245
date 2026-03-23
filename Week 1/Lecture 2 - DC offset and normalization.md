**DC offset:**
the *average value* of the samples in a signal

**Normalization**
Normalized audio data has
- DC offset of 0
- volume set to a maximum value

#### **Ex.**
```
normalize values:
47, -102, 63, 95
to a maximum of 200

DC offset is:
(47 - 102 + 63 + 95) / 4 = 25.75
	
Remove the DC offset from the samples:		
47 - 25.75 = 21.25, -102 - 25.75 = -127.75
63 - 25.75 = 37.25, 95 - 21.25 = 69.25
```
**why normalize when we can't hear it?**
- to maximize the values we can use for sampling data

Now scale the data with the DC offset removed to a maximum of 200. I.E. the largest *absolute* value of the data is 200.
```
scale samples by m = 200 / 127.75 to maximize (using 127.75 b/c it is the largest abs val). m = 1.5656
21.25   * m    = 33.27, 
-127.75 * m    = -200,
37.25   * m    = 58.32,
69.25   * m    = 108.41
(these should add up to 0)

using 16-bit resolution, we should round to nearest integer:
33, -200, 58, 108
```


### Decibel Scale
 decibels measure the change in voltage between 2 values
 $$ dB = 20log(\frac{v_1}{v_0}) $$
 for change in energy: $$ dB = 10log(\frac{e_1}{e_0}) $$
 energy is proportional to the square of the voltage $$ e_0 = kv_0^2 $$
#### **Ex.**
```
voltage change from 300 to 500
corresponding decibel change is 
20 log(500 / 300) = 4.44dB
``` 


```
(Linear) gain factor 'g' applied to a voltage value, multiplies the value by g
i  :  x(t)
o  :  y(t) = g * x(t)

gain can be measured in dB : 20 log(g)
```


#### **Ex. gain**
```
g = 0.75
corresponding gain in decibels is
20 log(0.75) = -2.50 dB

If the gain is 5 dB, what is the linear gain factor?
dB = 20 log(g) <-> g = dB / 20
5 dB -> g = 10^(5/20) = 1.78
```


A maximum voltage can be specified in dB relative to the max possible value.
#### **Ex. gain voltage**
```
for 16-bit audio, the max voltage val is 2^15 - 1 (32767)

for a target voltage of -3 dB,
target_v = max_v * 10^(-3/20) 
= 23197.3
```