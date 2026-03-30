#### Other Deconstructions
- Instead of sinusoids, other functions can be used to construct and deconstruct sounds
- For deconstruction, we need a (complete) collection of functions satisfying an orthogonality relation
- For construction, orthogonality (and completeness) is not necessary
	- Amounts to mixing of sounds

#### Amusement: Chebyshev Polynomials
- Chebyshev polynomials of the first kind are a complete collection of orthogonal polynomials
$$T_0 , T_1 , T_2 , \text{… on the interval }[-1,1] $$
- the polunomials are solutions of $$ \frac{d^2}{dx^2}T_n - x\frac{d}{dx}T_n+n^2 T_n = 0$$ for n = 0, 1, 2, ...
- alternatively, the Chebysev polynomials satisfy the recurrence relation $$ T_0(x) = 1, T_1(x)=x,T_n(x)=2xT_{n-1}(x)-T_{n-2}(x) $$
- orthogonality relation $$ \int_{-1}^1 T_m(x)T_n(x) \frac{dx}{\sqrt{1-x^2}} = \frac{\pi}{2}\gamma_{mn}$$
- every function on (-1, 1) can be expressed as a sum of Chebyshev polynomials $$ f(x) = \sum_{n=0}^{\infty} A_n T_n (x) $$
- the coefficients are determined by $$ A_n = \frac{2}{\pi} \int_{-1}^{1} f(x)T_n(x)\frac{dx}{\sqrt{1-x^2}} $$
