**Multi-channel audio**
- normalize each channel separately because each channel has its own DC offset.
- target max in dB is relative to max value of 1:
**E.g.,**
```
-3dB => target max: gain_factor = 10^(-3/20) ~= 0.708
=> scale by m = 0.708 / (larges abs. value)
```
- scaling factor applies to *all* channels uniformly



**Recall**
digital audio data quality is determined by
- sampling rate **R**
- bit resolution (typically 8-bit or 16-bit)

### Nyquist Limit
For sampling rate **R**, we can represent frequencies up to
$$ f_\text{ny} = \frac{R}{2} $$
```
tick = 1 / R

1
|t t t t ...
|- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
|
-1
```

CD - 44100
DVD - 96000

**Aliasing**
frequencies above Nyquist sound a different frequency

### Bit Resolution
- bit resolution determines noise level
	 this level measured by signal to noise ratio **(SNR)**
	 SNR	= (range of possible values / smallest difference in values)
	 measured in dB
**E.g., 8-bit audio:**
```
SNR = 2^8 / 1

20 * log(2^8) ~= 48dB
```

**E.g., 16-bit audio:**
```
SNR = 2^16 / 1

20 * log(2^16) ~= 96dB
```



