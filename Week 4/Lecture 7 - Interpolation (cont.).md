#### Re: linear interpolation
fractional index: 
$$i = Rt$$
#### Applications
- speed up effect
- change sampling rate
	-  ration of source_rate/target_rate


## Pitch

**Frequency:** 
absolute measurement in Hertz (Hz) (*linear scale*)

**Sound an octave above:** 
	multiply frequency by two
	$$ F_\text{octave-above} = 2F_\text{original} $$

**Cents:**
relative measurement of the *change* in pitch (*logarithmic scale*)
- 100 cents in a semitone
- 1200 cents in an octave

changing frequency F_old by P cents...
$$
F_\text{new} = 2^{({\frac{P}{1200}})} * F_\text{old}
$$

**Ex. Change frequency by P cents**
```
f_0 = 300Hz
- shift by 2 semitons
	  P = 2 * 100 = 200 cents
- freq. multiplier
	  m = 2^(200/1200) ~= 1.122
- shifted freq.
	  f_new = (1.122)(300) ~= 337Hz
```

**Ex. freq. change from 312Hz to 275Hz**
```
- freq. multiplier
	  m = f_new/f_old = 275/312 ~= 0.881Hz
- change in cents
	  m = 2^(P/1200) => log m = log (2^(P/1200))
	=>P = 1200 * (logm/log2) ~= 1200 * (log0.881/log2)
	=>-219 cents
```

**Remark:**
For the tape speed up effect, the speed up factor is the same as the frequency multiplier

