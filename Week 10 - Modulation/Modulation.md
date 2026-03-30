#### Modulation wheel (vibrato)
- gives a periodic small change in pitch
- note pitch determined by **three** factors
	- target pitch: from MIDI pitch index - S_0
	- pitch bend/shift: from pitch wheel - S_1
	- additional shift/vibrato: from modulation wheel - S_2
	- net speed-up factor: S = S_0 * S_1 * S_2

$$ s_0 = \text{MIDI index}$$
$$ s_1 = 2^{(\frac{p}{1200})} $$
$$ s_2 = 2^{\frac{pv}{1200}} $$
$$ P_v = \text{vibrato shift in cents} = d_v sin(2{\pi}f_vt) $$
$$ sin(2{\pi}f_vt) = \text{LFO element - Low Freq. Oscillator}$$
 $$ f_v = \text{vibrato rate (fixed 5Hz)} $$$$ d_v = \text{vibrato depth (in cents)} $$
 **Ex. Mod wheel message with control value 87. What is the vibrato shift 9.415s into the LFO cycle**
```
control value = 87
assume
f_v = 4.3 Hz 
max vibrato depth = 200 cents

d = (max_v_depth) (volume from control) 
d = (200)         (87/127)
d = 137 cents

P_v = d sin (2pi(f_v)t)
~= (137)(sin(2pi(4.3)(9.415))
~= 13 cents

```
