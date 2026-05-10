# Chapter 5 — Integration

## 5.1 Opening: The cyclist who didn't know how far she'd ridden

A cyclist rides for an hour. Her speedometer shows the speed at every instant — she watches it climb to 22 mph at the start, stay near 18 mph for most of the ride, ease to 12 mph on a hill, drop briefly to 8 mph at a stoplight, accelerate back up. At the end of the hour she wants to know: *how far did I ride?*

The speed varied continuously. There is no single number to multiply by the time. If she had ridden at a constant 18 mph, distance would be 18 miles. If she had ridden at 12 mph, 12 miles. Her actual ride was somewhere between, and the answer depends on how long she spent at each speed.

The strategy. Slice the hour into many small intervals — say, sixty intervals of one minute each. In each minute, the speed didn't change much; treat it as approximately constant. Distance in that minute ≈ speed at that minute × (1/60 hour). Add up the sixty contributions. The total is an *approximation* to the actual distance ridden.

Now make the slices smaller. Slice the hour into 600 intervals of six seconds each. Within six seconds the speed is even more nearly constant. The approximation gets better. Slice into 6000 intervals of one second. Better still. The *limit* of these approximations as the slice width shrinks to zero is the actual distance ridden over the hour.

This is *integration*. The answer to the cyclist's question is

$$\text{distance} = \int_0^1 v(t) \, dt$$

— the *definite integral* of velocity over the time interval. The sliced-and-summed approach is the *Riemann sum*; its limit as slices shrink is the integral.

By the end of this chapter, you should be able to:

- *Compute* a definite integral as the limit of a Riemann sum.
- *Apply* the Fundamental Theorem of Calculus to evaluate definite integrals via antiderivatives.
- *Find* indefinite integrals using the basic antidifferentiation formulas.
- *Apply* substitution to integrate compositions.
- *Distinguish* the definite integral (a number) from the indefinite integral (a function).
- *Recognize* the connection between integration and accumulation, and between integration and area.

You walk in with derivatives and antiderivatives from Chapters 3 and 4. You walk out with the second great operation of calculus and the theorem that ties it to the first.

## 5.2 The Riemann sum and the definite integral

Slice an interval $[a, b]$ into $n$ subintervals of equal width $\Delta x = (b - a)/n$. Pick a sample point $x_i^*$ in each subinterval. Approximate the area under a curve $y = f(x)$ by the sum of rectangle areas:

$$S_n = \sum_{i=1}^n f(x_i^*) \, \Delta x$$

This is a *Riemann sum*. As $n \to \infty$ (and $\Delta x \to 0$), the rectangles get thinner and the approximation tightens. If the limit exists and is the same regardless of how the sample points were chosen, we call it the *definite integral* of $f$ from $a$ to $b$:

$$\int_a^b f(x) \, dx = \lim_{n \to \infty} \sum_{i=1}^n f(x_i^*) \, \Delta x$$

The notation isn't accidental. The integral sign $\int$ is a stretched-out "S" for "sum"; the $dx$ replaces $\Delta x$ to indicate the width has shrunk to a differential. The expression literally reads as "the limit of the sum of $f(x)$-times-$dx$ contributions."

Three sample-point conventions are common:
- *Left endpoint*: $x_i^* = a + (i-1)\Delta x$.
- *Right endpoint*: $x_i^* = a + i \Delta x$.
- *Midpoint*: $x_i^* = a + (i - 1/2)\Delta x$.

For a continuous function, all three converge to the same integral; the choice affects the rate of convergence and the sign of the error at finite $n$.

A worked example. Estimate $\int_0^4 x^2 \, dx$ using $n = 4$ subintervals with the right-endpoint rule.

$\Delta x = 4/4 = 1$. Right endpoints: $x = 1, 2, 3, 4$. Values: $f(1) = 1$, $f(2) = 4$, $f(3) = 9$, $f(4) = 16$.

$$S_4 = (1 + 4 + 9 + 16)(1) = 30$$

The actual integral, computed by methods we develop below, is $\int_0^4 x^2 \, dx = 64/3 \approx 21.33$. The right-endpoint estimate of 30 overestimates because $x^2$ is increasing on the interval and the right endpoints are the highest points of each subinterval. With more subintervals (larger $n$), the estimate would converge.

A function is *Riemann integrable* on $[a, b]$ if the limit defining the integral exists. Continuous functions are integrable. Functions with finitely many jump discontinuities are integrable. Pathological functions can fail.

## 5.3 The Fundamental Theorem of Calculus

The integral defined as a limit of Riemann sums is conceptually clean and computationally a nightmare. For all but the simplest functions, evaluating the limit directly is impractical. The breakthrough that makes integration tractable is a theorem so consequential it gets the modifier "Fundamental":

*Fundamental Theorem of Calculus, Part 1*. If $f$ is continuous on $[a, b]$, define

$$F(x) = \int_a^x f(t) \, dt$$

Then $F$ is differentiable on $(a, b)$, and $F'(x) = f(x)$.

In words: differentiation undoes integration. The function $F$ that accumulates $f$ from $a$ up to $x$ has $f$ as its derivative.

*Fundamental Theorem of Calculus, Part 2*. If $f$ is continuous on $[a, b]$ and $F$ is *any* antiderivative of $f$ — that is, $F'(x) = f(x)$ — then

$$\int_a^b f(x) \, dx = F(b) - F(a)$$

This is the computational engine. To evaluate a definite integral, find an antiderivative and evaluate it at the endpoints. The Riemann-sum limit is the definition; the antiderivative is the way to compute.

A worked example. Evaluate $\int_0^4 x^2 \, dx$.

An antiderivative of $x^2$ is $F(x) = x^3/3$. By FTC Part 2:

$$\int_0^4 x^2 \, dx = F(4) - F(0) = \frac{64}{3} - 0 = \frac{64}{3}$$

The Riemann-sum limit gives the same answer; the antiderivative is faster.

The notation $F(b) - F(a)$ is sometimes written $F(x) \big|_a^b$ or $[F(x)]_a^b$ — read "F of x evaluated from a to b" — to compress.

Why is this theorem so big? Because it connects two operations that *look* different. Integration is accumulation (limit of Riemann sums). Differentiation is rate of change (limit of difference quotients). The FTC says they are inverses. Knowing one solves the other.

The trade-off in the FTC: it buys *practical computability* at the cost of *requiring an antiderivative to be available*. For many functions, antiderivatives don't have a closed form — $\int e^{-x^2} dx$ has no elementary antiderivative, despite the function being smooth and well-behaved. For those, numerical methods or special-function tables fill the gap.

## 5.4 The indefinite integral and the basic antiderivatives

The *indefinite integral* of $f$:

$$\int f(x) \, dx = F(x) + C$$

where $F$ is any antiderivative and $C$ is the constant of integration. The indefinite integral is a *family of functions*, one for each value of $C$.

The basic antiderivatives, recovered by reversing the derivative formulas of Chapter 3:

$$\int x^n \, dx = \frac{x^{n+1}}{n+1} + C \quad (n \neq -1)$$

$$\int x^{-1} \, dx = \ln|x| + C$$

$$\int e^x \, dx = e^x + C$$

$$\int b^x \, dx = \frac{b^x}{\ln b} + C$$

$$\int \cos x \, dx = \sin x + C$$

$$\int \sin x \, dx = -\cos x + C$$

$$\int \sec^2 x \, dx = \tan x + C$$

$$\int \frac{1}{\sqrt{1 - x^2}} \, dx = \arcsin x + C$$

$$\int \frac{1}{1 + x^2} \, dx = \arctan x + C$$

The integration analogs of the linearity of differentiation:

$$\int [c \cdot f(x)] \, dx = c \int f(x) \, dx$$

$$\int [f(x) + g(x)] \, dx = \int f(x) \, dx + \int g(x) \, dx$$

Constant multiples and sums distribute through. The *product rule and quotient rule* of differentiation, however, do *not* have direct integration analogs — there is no formula like $\int [f(x)g(x)] \, dx = (\int f) \cdot (\int g)$. The integration of products is harder than the differentiation of products; *integration by parts* (in Chapter 7-style coverage of techniques) handles it, and the chain rule's integration analog is *substitution*, the next section's topic.

## 5.5 Integration by substitution

The chain rule says $\frac{d}{dx}[F(g(x))] = F'(g(x)) \cdot g'(x)$. Read in reverse, this gives a method for integrating compositions:

$$\int F'(g(x)) \cdot g'(x) \, dx = F(g(x)) + C$$

Or, with $u = g(x)$ and $du = g'(x) \, dx$:

$$\int F'(u) \, du = F(u) + C$$

The substitution method: identify an inner function $u = g(x)$, compute $du = g'(x) \, dx$, and rewrite the integral in terms of $u$. If you've chosen $u$ well, the integral simplifies to a basic antiderivative.

A worked example. Compute $\int 2x \cos(x^2) \, dx$.

Let $u = x^2$. Then $du = 2x \, dx$. The integral becomes

$$\int \cos u \, du = \sin u + C = \sin(x^2) + C$$

Without substitution, this integral would have required either guessing the form of the antiderivative or appealing to integration by parts. With the right $u$, it collapses.

A second worked example with definite integration. Evaluate $\int_0^1 (3x^2 + 1)\sqrt{x^3 + x + 1} \, dx$.

Let $u = x^3 + x + 1$. Then $du = (3x^2 + 1) dx$. When $x = 0$, $u = 1$; when $x = 1$, $u = 3$. The integral becomes

$$\int_1^3 \sqrt{u} \, du = \int_1^3 u^{1/2} \, du = \frac{2}{3} u^{3/2} \bigg|_1^3 = \frac{2}{3}(3^{3/2} - 1) = \frac{2}{3}(3\sqrt{3} - 1) \approx 2.797$$

Notice the substitution changed *both* the integrand *and* the limits. When working with a definite integral and substitution, the limits in the original $x$-variable convert to the corresponding $u$-values; you don't need to back-substitute at the end.

The trade-off in substitution: it buys *integrability of compositions* at the cost of *requiring you to recognize the right inner function*. Substitution is the most-used integration technique; mastering it is most of what intro calculus students drill on.

## 5.6 Properties of the definite integral

Several properties of the definite integral follow from its definition as a Riemann-sum limit and are useful for breaking complicated integrals into manageable pieces.

*Linearity*. $\int_a^b [c \cdot f(x) + d \cdot g(x)] \, dx = c \int_a^b f(x) \, dx + d \int_a^b g(x) \, dx$.

*Additivity over intervals*. For $a \leq c \leq b$: $\int_a^b f(x) \, dx = \int_a^c f(x) \, dx + \int_c^b f(x) \, dx$. The integral over a union is the sum of the integrals over the pieces.

*Reversed limits*. $\int_a^b f(x) \, dx = -\int_b^a f(x) \, dx$. Reversing the order of integration flips the sign.

*Same endpoint*. $\int_a^a f(x) \, dx = 0$. An interval of zero width has zero accumulation.

*Comparison*. If $f(x) \leq g(x)$ on $[a, b]$, then $\int_a^b f(x) \, dx \leq \int_a^b g(x) \, dx$. Bigger integrand gives bigger integral.

*Bounding*. If $m \leq f(x) \leq M$ on $[a, b]$, then $m(b-a) \leq \int_a^b f(x) \, dx \leq M(b-a)$.

These properties are the toolkit for manipulating integrals in proofs and in computation. The additivity property is particularly useful: a function defined piecewise (different formulas on different intervals) integrates piece-by-piece.

## 5.7 Synthesis: the cyclist, computed

Return to the cyclist of §5.1. Suppose her velocity over the hour follows

$$v(t) = 18 + 5\sin(2\pi t)$$

mph, where $t$ is in hours from $0$ to $1$. The sinusoidal term models speed fluctuations around the average. The total distance ridden:

$$\text{distance} = \int_0^1 (18 + 5\sin(2\pi t)) \, dt$$

By linearity:

$$= 18 \int_0^1 dt + 5 \int_0^1 \sin(2\pi t) \, dt$$

$$= 18 \cdot 1 + 5 \cdot \left[-\frac{\cos(2\pi t)}{2\pi}\right]_0^1$$

$$= 18 + 5 \cdot \left[-\frac{1}{2\pi} + \frac{1}{2\pi}\right]$$

$$= 18 + 0 = 18 \text{ miles}$$

The sinusoidal fluctuation contributed zero net distance — the time spent above 18 mph exactly cancels the time spent below, since sine has zero average over a full period. The 18 mph average gave the answer regardless of the fluctuation.

Now suppose the velocity profile is more realistic: a hill in the middle of the hour drops the cyclist's speed temporarily.

$$v(t) = 18 - 6 e^{-100(t - 0.5)^2}$$

The exponential bump centered at $t = 0.5$ drops velocity by up to 6 mph at the midpoint of the ride, recovering quickly on either side. The total distance:

$$\int_0^1 \left[18 - 6 e^{-100(t-0.5)^2}\right] dt = 18 - 6 \int_0^1 e^{-100(t-0.5)^2} dt$$

The remaining integral has *no elementary antiderivative* — it's the kind of integral the FTC's machinery alone cannot solve. Numerical integration (Simpson's rule, Gaussian quadrature, or just Riemann sums with many subintervals) gives the answer numerically. With $n = 100$ subintervals and the midpoint rule, the integral is approximately $0.177$, so the total distance is $18 - 6(0.177) \approx 16.94$ miles.

This is the structural pattern. Every accumulated quantity — distance from velocity, velocity from acceleration, work from force, mass from density, present value from cash flow rate, total dose from infusion rate — is a definite integral. When a closed-form antiderivative exists, the FTC gives the answer exactly. When it doesn't, numerical integration approximates to whatever precision is needed.

## 5.8 Exercises

### Warm-up

1. **Use a Riemann sum with 4 right endpoints** to estimate $\int_0^2 x \, dx$. Compare with the exact answer of 2.

2. **Compute** $\int (3x^2 - 2x + 5) \, dx$.

3. **Evaluate** $\int_1^3 (2x + 1) \, dx$.

### Application

4. **Use substitution to compute:** (a) $\int 3x^2(x^3 + 1)^4 \, dx$; (b) $\int \cos(2x + 1) \, dx$; (c) $\int x e^{x^2} \, dx$.

5. **Evaluate the definite integrals:** (a) $\int_0^{\pi/2} \sin x \, dx$; (b) $\int_1^e \frac{1}{x} \, dx$; (c) $\int_{-1}^1 (x^3 + x) \, dx$.

6. **The velocity of a particle is $v(t) = t^2 - 4$ ft/s** for $0 \leq t \leq 4$. Find the total distance traveled. (Be careful: the particle moves backward when $v < 0$.)

### Synthesis

7. **A function $f$ has $f(0) = 5$ and $f'(x) = 3x^2$.** Recover $f$ by integration.

8. **Use the FTC to compute** $\frac{d}{dx} \int_0^x \cos(t^2) \, dt$. Then compute $\frac{d}{dx} \int_0^{x^2} \cos(t^2) \, dt$.

### Challenge

9. **Show that** $\int_0^a f(x) \, dx + \int_a^b f(x) \, dx = \int_0^b f(x) \, dx$ **for any continuous $f$ and any $a$ in $[0, b]$.** Sketch why this property is necessary for the integral to make sense as accumulation.

10. **The cyclist's velocity is $v(t) = 18 - 6 e^{-100(t-0.5)^2}$ mph for $0 \leq t \leq 1$.** Use Riemann sums with $n = 10$ midpoints to estimate the total distance. Compare with the value of approximately 16.94 miles given in §5.7.

## 5.9 Chapter summary

You walked into this chapter with derivatives and antiderivatives. You walk out with the second great operation of calculus.

The *definite integral* $\int_a^b f(x) \, dx$ is the limit of Riemann sums — accumulations of $f(x) \, dx$ contributions across the interval. It represents accumulation, area under a curve, and the inverse of differentiation.

The *Fundamental Theorem of Calculus* connects the two operations: to compute a definite integral, find an antiderivative and evaluate at the endpoints. Differentiation and integration are inverse operations.

The *indefinite integral* is the family of all antiderivatives. The basic antiderivatives reverse the basic derivatives.

*Substitution* is the integration analog of the chain rule: identify an inner function $u = g(x)$, compute $du$, and rewrite. It's the most-used technique for handling compositions.

The single most important idea: integration is *accumulation*. A definite integral sums up infinitely many infinitesimal contributions. The FTC reveals that this sum is computable using antiderivatives — making the abstract Riemann limit into a practical calculation.

The common mistake to watch for: forgetting the constant of integration on indefinite integrals. The constant is part of the answer; omitting it is omitting the family of solutions and presenting only one specific antiderivative as if it were the unique answer.

## 5.10 Why the FTC is so big — a closer reading

The Fundamental Theorem of Calculus connects two operations that appear, on the surface, to have nothing to do with each other.

The derivative is about *rates*. It asks how fast a function is changing at a single instant. Mechanically, it's the limit of an average rate of change as the interval shrinks. Physically, it's the slope of a tangent line, or the velocity at an instant of a moving object, or the marginal cost of producing one more unit. The derivative is *local* — it depends only on what the function does in an arbitrarily small neighborhood of the point.

The integral is about *accumulation*. It asks how much of something has piled up over an interval. Mechanically, it's the limit of a Riemann sum of contributions across the interval. Physically, it's the area under a curve, or the total distance traveled given a velocity, or the total mass of an object given a density. The integral is *global* — it depends on everything the function does across the whole interval.

The FTC says these are inverse operations. The function $F(x) = \int_a^x f(t) \, dt$, which accumulates $f$ from $a$ up to $x$, has the property that $F'(x) = f(x)$. Differentiating an accumulation recovers what was being accumulated. And conversely, integrating a derivative reconstructs the function (up to the constant): $\int_a^b F'(x) \, dx = F(b) - F(a)$.

The conceptual content of this connection is enormous. It says that local rate information and global accumulation information are completely interchangeable. If you know the rate at every instant, you know the total — by integration. If you know the running total at every instant, you know the rate — by differentiation. Two different ways of describing change are *the same description* viewed from different angles.

Newton and Leibniz, working independently in the 1670s and 1680s, both arrived at versions of this theorem. The bitter priority dispute that followed obscured for decades the fact that the underlying insight — the inverse relationship of differentiation and integration — was the central achievement of seventeenth-century mathematics. Earlier mathematicians (Fermat, Cavalieri, Wallis, Barrow) had each developed methods for tangent slopes and for areas, but they had not seen the connection between the two as a single theorem. Newton and Leibniz did.

The structural lesson worth carrying forward: when two operations look unrelated but one shows up as the inverse of the other, look hard. Mathematics is full of such relationships, and they are typically the doors to deeper structure. Differentiation and integration are paired. Sums and differences are paired. Logarithms and exponentials are paired. Vectors and dual vectors. Each pairing is a fundamental theorem in waiting.

## 5.11 The integral and physical units

A practical note on dimensional analysis. The integral $\int_a^b f(x) \, dx$ has units of *(units of $f$) × (units of $x$)*. A velocity (mph) integrated against time (hours) gives miles. A force (newtons) integrated against distance (meters) gives joules of work. A density (kilograms per cubic meter) integrated against volume (cubic meters) gives kilograms of mass. The units come out right because the Riemann sum is multiplying $f(x_i^*)$ by $\Delta x$ — and the units of the product are the units of the integral.

This is one of the simplest sanity checks on integration setups. If your integrand has units of meters and you're integrating against time in seconds, the result is in meter-seconds. If you wanted meters, your integrand should have been a velocity. The units catch errors before the algebra does.

## 5.12 What integration cannot do (yet)

Some integrals do not have closed-form antiderivatives. The Gaussian integrand $e^{-x^2}$, central to probability theory, is one. The error function $\text{erf}(x) = (2/\sqrt{\pi}) \int_0^x e^{-t^2} dt$ is *defined* as the integral because no elementary function has $e^{-t^2}$ as its derivative. Similarly, $\int (\sin x)/x \, dx$ has no closed form (it defines the *sine integral* $\text{Si}(x)$). $\int e^x / x \, dx$ defines the *exponential integral*. These are not failures of mathematicians' cleverness — they have been *proven* (by Liouville in the 1830s and more rigorously since) to have no antiderivative expressible in elementary functions.

For these integrals, the FTC's promise of "find an antiderivative" doesn't deliver a usable formula. The recourses: numerical integration (Simpson's rule, Gaussian quadrature, Monte Carlo), special-function tables (the error function's values are tabulated and built into every modern computational library), or series expansions (integrate the Taylor series term-by-term and sum). Each approach trades exact closed form for some other property.

The deeper lesson: calculus did not solve the integration problem in a way that always produces clean formulas. It solved it in a way that always produces *approximations to arbitrary precision*. For physics and engineering practice, the second is sufficient. For pure mathematics, the first matters and motivates whole subjects (real analysis, complex analysis, special-function theory) devoted to extending the catalog of integrable forms.

## 5.13 Connections forward

Chapter 6 puts the integral to work, the way Chapter 4 put the derivative to work. Areas between curves, volumes of solids of revolution, lengths of curves, surface areas, work done by a variable force, hydrostatic pressure, center of mass, present value of cash streams — every accumulation problem is an integration problem. The Riemann-sum perspective from §5.2 becomes the systematic strategy: slice the quantity into infinitesimal pieces, integrate, evaluate.
