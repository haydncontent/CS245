**Bit Resolution**
When stored in a file, audio data is typically stored in either 8-bit or 16-bit integer format.

However, for manipulation of audio data, usually floating point format is used.

**Floating Point Conventions**
- values nominally in the range [-1, 1]
- it's okay for *intermediate* values to exceed this range
- values are only clamped to [-1, 1] when written to a file that uses integer format

**Ex.**
```
16-bit value (range [-2^15, 2^15 - 1]
-6329

Convert to standard floating point format in the range [-1, 1]

Divide by 2^15
-6329 / 2^15 ~= 0.19315
```

**Ex. 16-bit->float**
```
Convert -32768 (-2^15) to floating point
-32768 / 2^15 = -1
```

**Ex. float->16-bit**
```
Convert floating point value 0.43 to 16-bit 
Multiply by (2^15 - 1) so we don't go out of range
0.43 * (2^15 - 1) = 14089.81 -> 14089
```

**Ex. 8-bit->float**
```
Convert 8-bit value 37 to float
8-bit voltage value = 37 - 128 = -91

Divide by 2^7 (128)
-91 / 128 ~= -0.7109
```

**Ex. float->8-bit**
```
Convert float value 0.5312 to an 8-bit value

Multiply by (2^7 -1) 127
0.5312 * 127 ~= 67.46 (voltage value)
67.46 + 128 = 195.46 -> 195
```


## Storing Audio Data

**Mono**
```
0   1   2    - array index
[s0][s1][s0] - sample index
```

**Multiple**
```
[   0  ][   1  ][   2  ] - frame index
[L0][R0][L1][R1][L2][R2] - samples
0   1   2   3   4   5    - array index
```
An audio frame consists of all channels at a given time point (sample index)
Within a frame of multiple channels, there is a channel index (**L & R** as **0 & 1**)

If the data is stored in an array of audio sample values, the array index != frame index

**Ex. 6-channel audio**
```
stored in a single array

find the array index of channel #3 frame #57

(array index) = (# of channels)(frame index) + (channel index)
= (6)(57) + (3)
= 345
```

**Remark:**
the word "sample" can mean either an audio frame (multiple "samples") or a single channel within an audio frame
*"sampling rate"* means frames per second
and *"audio sample"* mean a single channel within a frame

**Ex.**
```
find the frame and channel indices for the array at index 832
832 / 6 = 138 index 4
```