**Sounds:** represented using voltages.
### Analog recording/playback
- voltage is converted to a magnetic field 
- recorded with oxide particles glued to the surface of the plastic tape
- all this while tape passes over the record head
**Bad:**
- tapes can be stretched and subject to mechanical limitations
- distortion/noise from metal particles
- degrades with playback
**Good:** 
- analog records a *continuous* voltage signal

### Digital recording/playback
- input voltage is sampled at regular intervals
- information is always lost (*not continuous*)
**Sampling rate (Hz):** *let R = sampling rate*
$$
t_n = \frac{n}{R}
$$
**Sample resolution:**
- voltages are assigned integer values (quantization)
- fixed number of bits for each sample, called bit resolution

### 8 vs 16 Bit Sampling
**8 Bit:**
- Unsigned integer values [0, 255]
- midpoint is 128 (when voltage is 0)
Example: *let R = 5Hz*
$$ V(t) = 135(7t^2 - 1) $$
```
V(0) = -135 -> -135+128 = -7(<0) -> 0
V(1/5) = -97.2 -> -97.2+128 = 30.8 -> 31
V(2/5) = 16.2 -> 16.2+128 = 144.2 -> 144
V(3/5) = 205.2 -> 205.2+128 = 332.2(>255) -> 255
```
**16 bit:**
- Signed integer values [-(2^15), (2^15) -1]
- midpoint is 0
Example: *let R = 5Hz*
$$ V(t) = 23456(7t^2 - 1) $$
V(0), V(1/5), V(2/5), V(3/5) are the values for t.
If value exceeds max value for 16-bit, clamp to the max value.

