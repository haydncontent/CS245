#### Re:
```
0     1     2     3
[H|L] [H|L] [H|L] [H|L]

- 4-bytes structure 
- byte @ index 0
	- Higher order : message #
	- Lower order  : channel #
- Remaining bytes are message dependent 
```

#### Port MIDI - cross platform MIDI API
**patch change msg**
```
message # 0xC = patch change
byte @ index 1 = patch #
(bytes @ 2 + 3 unused)
```

**message union**
```
union MidiMessage 
// stored together in memory 
// send as message // access as char array
{
	long message;
	unsigned char byte[4];
};
```

**note on msg**
```
message # 0x9 = note on
byte @ index 1 = pitch index
byte @ index 2 = velocity (0-127)
```
**note:** can also turn off a note with this *note on* msg by setting velocity=0.

**note off msg**
```
message # 0x8 = note off
byte @ index 1 = pitch index
```



#### Band-Limited Interpolation
**linear interpolation**
simple and efficient but can introduce "artifacts"

**band-limited interpolation**
minimizes "artifacts" but is inefficient to compute.

$$ y(t) \sum_{m=0}^{N-1}  {x_m sinc(Rt-m)} $$
where
 $$ sinc(x) = \frac{sin(\pi x)}{\pi x} \text{ if x!= 1} $$ $$ sinc(x) = 1 \text{ if x == 0}$$

**Upsampling:**
change the sampling rate to a higher value (e.g., 44100Hz -> 48000Hz)

**Downsampling:**
change the sampling rate to a lower value (e.g., 44100Hz -> 8000Hz)

**Ideal behavior:**
upsampling - frequency spectrum is exactly the same
downsampling - frequency spectrum is exactly the same *up to the nyquist limit*

