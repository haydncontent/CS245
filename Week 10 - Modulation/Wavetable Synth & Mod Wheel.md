#### Re: determining output pitch from audio sample
depends on:
1. target pitch: given MIDI pitch index. determine speed-up factor to sound target pitch; combines resampling factor (WAVE file rate to synth rate) & speed up from sample pitch to target pitch
2. pitch bend offset: given MIDI pitch wheel event, determine shift from target pitch
3. vibrato (mod wheel) offset: given MIDI mod wheel event & place in LFO cycle, determine additional shift from target pitch

Combine 2 & 3 for net offset

Net speed-up - The product of shift and resample
$$ s_0 * 2^{p_1/1200}*2^{p_2/1200} = s_0 * 2^{(p_1 + p_2)/1200} $$

**Ex. Wavetable synth using audio sample that sounds 354Hz**
```
Receives three messages:
0) note on, midi pitch index 60
1) pitch wheel msg with -124 cenets shift
2) mod wheel msg with 86 cent shift depth

Assume vibrato rate at 5Hz & 7.395s into the LFO cycle
What net speed-up factor to apply to the audio sample (assume sampling rate is the same as the sample)

target_freq / sample_freq
s_0 = (440 * 2^((60-69)/12)) / 354 ~= 0.7391

P = p_1 + p_2 = -124 + 86sin(2pi(t)(7.395)) ~= -137 cents

net speed-up = s_0 * 2^(P/1200) = 0.7391 * 2^(-137/1200) ~= 0.826

orrr
s_0 = 2^(P_0/1200)
p_0 = net shift from original sample

s = s_0 * s_1 * s_2 = 2^((p_0 + p_1 + p_2)/1200)
```