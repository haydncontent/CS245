## Interpolation of audio data

**Input:** audio samples
```
x_0, x_1, x_2, ... , x_n-1
k is the fractional index
where x_k is the sample value at time t_k = k/R; k = Rt_k
```
**Output:**
```
y_0, y_1, y_2, ... , y_m-1
values possibly interpolated from input value
```

**Ex. Input:**
```
x_0 = 16, x_1 = 55, x_2 = -20, x_3 = 34
R = 10Hz

Find the interpolated sample value at time t = 0.14s
index k = Rt = 10 * 0.14 = 1.4 

interpolate between index 1 and 2
x_i = x_k + (i - k)(x_k - x_k+1)

so
x_1.4 = (x_1) + (0.4)(x_2 - x_1) = 55 + (0.4)(-20-55) = 25
```

**Ex. ^ Same Input. Speed playback by a factor of alpha=1.2**
```
(playback sampling rate stays the same)

in
|---|---|---|---|--- t
t0  t1  t2  t3  t4

out
|---|---|---|---|--- t
y0   y1   y2

y_1=x_1.2
y_2=x_2.4
```

**In General Speeding Up:**
the n-th output sample after speed up is 
y_n = x_(alpha * n)

```
so 
y_0 = x_(1.2)(0) = 16
y_1 = x_(1.2)(1) = 40
y_2 = x_(1.2)(2) = 1.6
```

## Applications of interpolation
- Speed-up effect (keep the same sampling rate)
	- y_n = x_(alpha * n)
- Change sampling rate (keep the same pitch)
	- use effective speed up factor alpha=oldR/newR

**Ex. Resample from 8Hz to 10Hz**
```
x_0 = 40, x_1 = 14, x_2 = -26, x_3 = 8
R = 8Hz

0	1	2	3	4
|---|---|---|---|--- t

speed up factor = R/R' => 8/10 => 0.8
```