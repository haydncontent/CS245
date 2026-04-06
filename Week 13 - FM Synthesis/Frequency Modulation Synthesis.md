Q: Why is it used?
A: Easier to produce computationally

#### FM Synthesis
 method for producing complex (many partials in freq. spectrum) sounds inexpensively

###### Simple FM Synthesis
$$ f_c = \text{carrier freq; }f_m = \text{modulation freq; } \alpha_m = \text{amplitude of modulation }$$
$$ y(t) = sin(2\pi f_c t + \alpha_m sin(2\pi f_m t)) $$
partial expansion of ^
$$  y(t) = sin(2\pi f_c t + \alpha_m sin(2\pi f_m t)) = \sum_{n \in Z} J_n(\alpha_m)sin(2\pi (f_c+f_m) t) $$
in particular, the frequency of the partial at index 'n' is 
$$ f_n = f_c + nf_m $$
**Ex.**
```
f_c = 200 Hz
f_m = 100 Hz

n =  0: f_0    = f_c + (0) f_m  = 200  Hz
n =  1: f_1    = f_c + (1) f_m  = 300  Hz
n =  2: f_2    = f_c + (2) f_m  = 400  Hz
n =  3: f_3    = f_c + (3) f_m  = 500  Hz

n = -1: f_(-1) = f_c + (-1)f_m  = 100  Hz
n = -2: f_(-2) = f_c + (-2)f_m  = 0    Hz
n = -3: f_(-3) = f_c + (-3)f_m  = -100 Hz ( heard as |100 Hz| *)

* this gives 100 Hz an amplitude boost because it is repeated
```

#### Bessel Functions
$$ J_n(x) = \text{n-th order Bessel function of the first kind} $$
it can be defined by:
$$ J_n(t) = \frac{1}{\pi} \int_0^\pi cos ( nx - t sin(x)) dx $$

occurs in a drum, head fixed around the rim, membrane is free.
Bessel function describes the movement

###### Bessel Function Properties
1) $$  J_{-n}(t) = (-1)^n J_n(t) $$
2) $$ J_{n+1}(t) = \frac{2n}{t} J_n(t) - J_{n-1}(t) $$
**Consequences:**
- from 1): know negative-indexed Bessel function from positive indexed functions
- from 2): know any positive-indexed Bessel function from J_0 and J_1

###### Asymptotic formulas
- for small values of t: $$ J_n (t) = \frac{t^n}{2^n n!} $$
- for larger values of t: $$ J_n (t) = \sqrt{\frac{2}{\pi t}} cos(t - \frac{n \pi}{2} - \frac{\pi}{4}) $$
###### Compute Bessel Function (rational function approximation)
$$ \sum_{n \in Z} J_n(\alpha_m) sin (2\pi (f_c+f_m)t) $$
$$ J_{-n}(t) = (-1)^n J_n(t) $$n=0: $$ \text{ampl. } J_0 = (\alpha_m) $$
n=1: $$ \text{ampl. } J_1 = (\alpha_m) $$