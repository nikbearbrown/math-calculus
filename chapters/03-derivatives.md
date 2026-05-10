# Chapter 3 — Derivatives

## 3.1 Opening: Zero to two hundred

In 2014 a Hennessey Venom GT — a 1,244-horsepower, hand-built American hypercar — accelerated from a standstill to 200 miles per hour in 14.51 seconds. The same car set a top-speed record of 270.49 mph. Roll those numbers in your head. From rest to two hundred mph in less time than it takes most people to read this paragraph.

What was the car's *acceleration*? The natural temptation is to divide: 200 mph in 14.51 seconds, so the average acceleration was about 13.78 mph per second. Multiply by the conversion factor (5,280 feet per mile, 3,600 seconds per hour), and the average acceleration works out to roughly 20.2 ft/s², or about 0.63 g — six-tenths of the acceleration due to gravity, sustained for fourteen seconds. That's the *average*.

But average is not what was actually happening at any specific instant. The acceleration at the instant of launch — when the clutch engaged and the rear tires spun against the asphalt — was higher. The acceleration at the instant of crossing 200 mph, with most of the engine's torque already overcome by aerodynamic drag, was lower. The number we want is not the average over 14.51 seconds. It is the *instantaneous* rate of velocity change at any chosen moment.

The natural strategy for finding it: shrink the time interval. Compute the average acceleration over the first 7 seconds, then over the first 1 second, then 0.1 second, then 0.01 second. As the interval shrinks, the average becomes a tighter and tighter approximation of the instantaneous rate. The *limit* of the average rate of change as the interval shrinks to zero — that's the instantaneous rate. That limit has a name. It is the *derivative*.

This chapter is about the derivative. By the end of it, you should be able to:

- *Compute* the derivative of a function from the limit definition.
- *Apply* the differentiation rules: power, sum, difference, constant multiple, product, quotient, chain.
- *Differentiate* the standard families of functions — polynomials, rational functions, trigonometric functions, exponentials, logarithms.
- *Interpret* the derivative as a slope, a velocity, an instantaneous rate of change, and a marginal quantity.
- *Recognize* when a function is differentiable and when it is not.
- *Compute* higher-order derivatives — the derivative of the derivative — and interpret them physically.

You walk in with the limit machinery from Chapter 2. You walk out with the central computational tool of differential calculus.

Why does it matter? Because *every* rate of change in physics, engineering, biology, economics, and statistics is a derivative. Velocity is the derivative of position. Acceleration is the derivative of velocity. Marginal cost is the derivative of total cost. Population growth rate is the derivative of population. Reaction rate is the derivative of concentration. The vocabulary of change in mathematics is the derivative; this chapter is where you learn to speak it.

## 3.2 The derivative as a limit

The setup. Let $f$ be a function. Pick a point $x = a$ in its domain. We want the *instantaneous rate of change* of $f$ at $a$.

The strategy. Pick a small number $h$. Compute the *average rate of change* of $f$ over the interval $[a, a+h]$:

$$\text{avg rate} = \frac{f(a+h) - f(a)}{h}$$

This is the slope of the *secant line* through the two points $(a, f(a))$ and $(a+h, f(a+h))$ on the graph of $f$. The slope is the rise over run, the change in output divided by the change in input.

Now shrink $h$ toward zero. The two points get closer together. The secant line tilts toward the *tangent line* at $(a, f(a))$. The average rate of change tilts toward the instantaneous rate.

The limit, when it exists, is the *derivative* of $f$ at $a$:

$$f'(a) = \lim_{h \to 0} \frac{f(a+h) - f(a)}{h}$$

The derivative measures the slope of the function's graph at a single point. It is the answer to "how fast is $f$ changing right here?"

A worked example. Compute $f'(2)$ for $f(x) = x^2$.

$$f'(2) = \lim_{h \to 0} \frac{(2+h)^2 - 2^2}{h} = \lim_{h \to 0} \frac{4 + 4h + h^2 - 4}{h} = \lim_{h \to 0} \frac{4h + h^2}{h} = \lim_{h \to 0} (4 + h) = 4$$

The derivative of $x^2$ at $x = 2$ is 4. Geometrically: the slope of the parabola $y = x^2$ at $x = 2$ is 4. Mechanically: a tangent line touching the parabola at $(2, 4)$ has slope 4 and equation $y - 4 = 4(x - 2)$.

A few notational variants. The derivative of $f$ at $a$ can be written several ways, all denoting the same thing:

$$f'(a), \quad \frac{df}{dx}\bigg|_{x=a}, \quad \frac{d}{dx}f(x)\bigg|_{x=a}, \quad Df(a)$$

The first is *Lagrange* notation; the second and third are *Leibniz* notation; the last is *operator* notation. Different fields prefer different conventions. Leibniz notation $df/dx$ — read "dee-eff dee-ex" — has the advantage of carrying the variable of differentiation in the symbol, which is essential when working with multivariable functions or chain-rule compositions.

If we let $a$ vary across the domain, the derivative becomes a *function*:

$$f'(x) = \lim_{h \to 0} \frac{f(x+h) - f(x)}{h}$$

Same definition, with $x$ replacing $a$. Now $f'$ is a new function — its input is a point in the domain of $f$, its output is the instantaneous rate of change of $f$ at that point. The derivative of a function is itself a function.

For $f(x) = x^2$:

$$f'(x) = \lim_{h \to 0} \frac{(x+h)^2 - x^2}{h} = \lim_{h \to 0} \frac{2xh + h^2}{h} = \lim_{h \to 0} (2x + h) = 2x$$

The derivative function is $f'(x) = 2x$. Plug in any specific value of $x$ — like $x = 2$, giving $f'(2) = 4$ — to recover the slope at that point. The derivative function is the more general object; specific derivatives are samples of it.

The trade-off in the limit definition: it is *the* definition (every other rule comes from it) at the cost of *being slow* (every derivative computation is a from-scratch limit). The differentiation rules that follow in §3.3-3.4 mechanize the routine cases; the limit definition is what proves the rules are correct.

A common misconception: that the derivative measures the *change* in the function. It doesn't. It measures the *rate* of change — how fast the function is changing per unit of input. A function changing slowly has a small derivative; a function changing quickly has a large one.

## 3.3 Differentiability and continuity

The derivative is a limit. Limits don't always exist. So derivatives don't always exist.

A function is *differentiable* at a point $a$ if $f'(a)$ exists — that is, if the limit definition produces a finite number. A function can fail to be differentiable at $a$ in three structural ways.

*The function is not continuous at $a$.* If $f$ is not continuous, the average rate of change blows up — the numerator $f(a+h) - f(a)$ has a discontinuous spike that doesn't shrink to zero as $h$ does. Differentiability requires continuity. The reverse is not true.

*The function has a corner at $a$.* The function is continuous, but the slope from the left differs from the slope from the right. Example: $f(x) = |x|$ at $x = 0$. The left-hand derivative is $-1$; the right-hand derivative is $+1$. The two-sided limit does not exist; the function is not differentiable at $0$, even though it is continuous there.

*The function has a vertical tangent at $a$.* The slope is "infinite" — the function is changing arbitrarily quickly. Example: $f(x) = x^{1/3}$ at $x = 0$. The derivative is $\frac{1}{3}x^{-2/3}$, which blows up as $x \to 0$.

*Differentiability implies continuity*, but continuity does not imply differentiability. A continuous function can have corners and vertical tangents that block differentiability. The implication arrow goes one way.

The trade-off in differentiability: it is *stronger* than continuity (the function must be smooth, not just unbroken) at the cost of *applying to fewer functions* (corners and vertical tangents are excluded). The standard families — polynomials, rationals on their domains, trig, exp, log — are differentiable everywhere they're defined. Pathological functions are excluded.

## 3.4 The differentiation rules

Computing every derivative from the limit definition is impractical. The differentiation rules, each provable from the definition, mechanize the routine cases.

### The constant rule

If $f(x) = c$ (a constant), then $f'(x) = 0$. A constant doesn't change; its rate of change is zero.

### The power rule

If $f(x) = x^n$ for any real number $n$, then $f'(x) = n x^{n-1}$.

This is the most-used rule in calculus. For positive integer $n$, it follows from the binomial expansion of $(x+h)^n$ in the limit definition. For other $n$ (negative, fractional, irrational), the proof requires more machinery, but the formula holds.

Examples: $\frac{d}{dx}(x^3) = 3x^2$. $\frac{d}{dx}(x^{1/2}) = \frac{1}{2}x^{-1/2} = \frac{1}{2\sqrt{x}}$. $\frac{d}{dx}(x^{-2}) = -2x^{-3} = -2/x^3$.

### Sum, difference, and constant-multiple rules

If $f$ and $g$ are differentiable and $c$ is a constant:

$$\frac{d}{dx}[f(x) + g(x)] = f'(x) + g'(x)$$
$$\frac{d}{dx}[f(x) - g(x)] = f'(x) - g'(x)$$
$$\frac{d}{dx}[c \cdot f(x)] = c \cdot f'(x)$$

Differentiation distributes over addition, subtraction, and scalar multiplication. Combined with the power rule, these handle every polynomial.

Example: $\frac{d}{dx}(3x^4 - 5x^2 + 7x - 1) = 12x^3 - 10x + 7$.

### The product rule

The product rule does *not* follow the simple pattern. The derivative of a product is *not* the product of the derivatives. The correct rule:

$$\frac{d}{dx}[f(x) g(x)] = f'(x) g(x) + f(x) g'(x)$$

In words: the derivative of a product equals the derivative of the first times the second, plus the first times the derivative of the second.

Example: $\frac{d}{dx}(x^2 \sin x) = 2x \sin x + x^2 \cos x$.

The product rule is a frequent source of error. Students intuitively want $\frac{d}{dx}[fg] = f' g'$, which is wrong. Memorize: *first derivative times second, plus first times second derivative*.

### The quotient rule

Similarly, the derivative of a quotient is *not* the quotient of the derivatives:

$$\frac{d}{dx}\left[\frac{f(x)}{g(x)}\right] = \frac{f'(x) g(x) - f(x) g'(x)}{[g(x)]^2}$$

Memorization mnemonic: "low d-high minus high d-low over low squared." The numerator has *bottom times top's derivative minus top times bottom's derivative*; the denominator is the bottom *squared*.

Example: $\frac{d}{dx}\left[\frac{x^2}{x+1}\right] = \frac{2x(x+1) - x^2 \cdot 1}{(x+1)^2} = \frac{x^2 + 2x}{(x+1)^2}$.

### The chain rule

The most powerful — and, for many students, the most error-prone — differentiation rule is for *compositions*. If $f$ and $g$ are differentiable, then

$$\frac{d}{dx}[f(g(x))] = f'(g(x)) \cdot g'(x)$$

In words: differentiate the outer function, evaluated at the inner function, times the derivative of the inner function.

In Leibniz notation, the chain rule has its cleanest form:

$$\frac{dy}{dx} = \frac{dy}{du} \cdot \frac{du}{dx}$$

where $y$ depends on $u$ and $u$ depends on $x$. The notation suggests the rule visually — $du$'s "cancel" symbolically (though the manipulation is not algebraic; it's a notational coincidence that works because of the chain rule's structure).

Example: differentiate $y = (x^2 + 3)^5$. The outer function is $u^5$ with derivative $5u^4$. The inner function is $u = x^2 + 3$ with derivative $2x$. Chain rule:

$$\frac{dy}{dx} = 5(x^2 + 3)^4 \cdot 2x = 10x(x^2 + 3)^4$$

Without the chain rule, you'd have to expand $(x^2 + 3)^5$ as a polynomial and differentiate term-by-term — five terms times five derivatives, all combined. With the chain rule, two derivatives and a multiplication.

Compositions of three or more functions iterate the chain rule. For $y = f(g(h(x)))$:

$$\frac{dy}{dx} = f'(g(h(x))) \cdot g'(h(x)) \cdot h'(x)$$

Each level peels off one layer of composition.

The trade-off across the differentiation rules: each is a structural shortcut at the cost of *requiring memorization*. Students who skip the rules and try to differentiate everything from the limit definition lose a hundred-fold efficiency advantage. Students who learn the rules without understanding why they're correct lose the ability to handle non-routine cases. Both pieces are needed.

## 3.5 Derivatives of the standard transcendental functions

The differentiation rules apply to any differentiable functions. To use them, you need the derivatives of the standard transcendentals.

*Trigonometric*. The unit-circle definitions of sine and cosine give

$$\frac{d}{dx}(\sin x) = \cos x \quad\quad \frac{d}{dx}(\cos x) = -\sin x$$

These hold *only when $x$ is in radians* — which is why radian measure was emphasized in Chapter 1. The proofs use the limit definition combined with the trig identities $\sin(x+h) = \sin x \cos h + \cos x \sin h$ and the limits $\lim_{h \to 0} \sin h / h = 1$ and $\lim_{h \to 0} (\cos h - 1)/h = 0$.

From these two and the quotient rule, the derivatives of the other four follow:

$$\frac{d}{dx}(\tan x) = \sec^2 x, \quad \frac{d}{dx}(\cot x) = -\csc^2 x$$
$$\frac{d}{dx}(\sec x) = \sec x \tan x, \quad \frac{d}{dx}(\csc x) = -\csc x \cot x$$

*Exponential*. The natural exponential has the cleanest derivative of all functions:

$$\frac{d}{dx}(e^x) = e^x$$

The function equals its own derivative. This is the property that *defines* $e$ — it is the unique base for which $\frac{d}{dx}(b^x) = b^x$. For other bases:

$$\frac{d}{dx}(b^x) = b^x \ln b$$

The factor $\ln b$ accounts for the fact that bases other than $e$ are growing at a rate slightly off from their own value.

*Logarithmic*. The natural log:

$$\frac{d}{dx}(\ln x) = \frac{1}{x} \quad \text{for } x > 0$$

For other bases:

$$\frac{d}{dx}(\log_b x) = \frac{1}{x \ln b}$$

The change-of-base relationship $\log_b x = \ln x / \ln b$ produces the $\ln b$ in the denominator.

The trade-off in working with transcendentals: each function has a derivative formula that has to be memorized at the cost of *not following the simple algebraic pattern of polynomials*. The compensating gain: once memorized, transcendental derivatives plug into the chain, product, and quotient rules just like any other.

## 3.6 Higher-order derivatives

The derivative $f'$ is itself a function. So you can differentiate it. The result is the *second derivative*, written $f''$ (or in Leibniz notation $d^2 f / dx^2$ — read "dee-squared-eff dee-ex-squared"). And the derivative of the second derivative is the *third derivative*, $f'''$ or $d^3 f / dx^3$. Higher derivatives keep stacking.

For $f(x) = x^4$:

- $f'(x) = 4x^3$
- $f''(x) = 12x^2$
- $f'''(x) = 24x$
- $f^{(4)}(x) = 24$
- $f^{(5)}(x) = 0$, and all higher derivatives are zero.

(For derivatives beyond the third, the prime notation gets unwieldy and the parenthesized superscript notation $f^{(n)}$ takes over.)

The physical interpretations are revealing. If $s(t)$ is position as a function of time, then:

- $s'(t)$ is *velocity* — the rate of change of position.
- $s''(t)$ is *acceleration* — the rate of change of velocity.
- $s'''(t)$ is *jerk* — the rate of change of acceleration.
- $s^{(4)}(t)$ is *snap* (or *jounce*) — the rate of change of jerk.

Each derivative answers a question about a different kind of change. Velocity tells you how fast you're moving. Acceleration tells you how quickly your velocity is changing — what you feel as you press the gas pedal. Jerk is what you feel when the acceleration changes suddenly — the lurch of a car shifting gears, the stomach-flip on a roller coaster. Engineers designing elevators and amusement-park rides minimize jerk to make the ride feel smooth.

## 3.7 Synthesis: the Hennessey Venom GT, computed

Return to the cold open. The Venom GT goes 0 to 200 mph in 14.51 seconds. *Average* acceleration: 200/14.51 ≈ 13.78 mph/s ≈ 20.2 ft/s² ≈ 0.63 g.

But the actual acceleration was not constant. Suppose — as a model — that the velocity as a function of time follows the simple form $v(t) = v_{\max}(1 - e^{-t/\tau})$ for some characteristic time $\tau$. This is the standard form of velocity for an object whose acceleration falls off exponentially as drag overcomes engine power — a reasonable first-order approximation for high-speed automotive acceleration. We don't have the actual $\tau$ for the Venom from the source; the worked-example structure is the point.

To get acceleration as a function of time, differentiate the velocity:

$$a(t) = \frac{dv}{dt} = v_{\max} \cdot \frac{1}{\tau} e^{-t/\tau} = \frac{v_{\max}}{\tau} e^{-t/\tau}$$

At $t = 0$ the acceleration is $v_{\max}/\tau$ — the maximum, set by the engine's launch torque. As $t$ grows, acceleration decays exponentially toward zero — the car asymptotically approaches its top speed.

If we knew the actual $\tau$ for the Venom, we could compute the launch acceleration in g's, the time at which the acceleration dropped to half its initial value, and the time at which 95% of top speed was reached. The chapter's tool — the derivative — is what turns an observed velocity history into the underlying acceleration profile.

The pattern recurs everywhere change is studied. Cell biology measures the rate of cell division (the derivative of cell count). Climate science measures the rate of $\text{CO}_2$ accumulation (the derivative of atmospheric concentration). Finance measures volatility (the derivative-flavored measure of stock-price change). Physics measures momentum and force (derivatives of position, integrated against mass). The derivative is not a math curiosity. It is the language of change.

## 3.8 Exercises

### Warm-up

1. **Use the limit definition to compute $f'(x)$ for $f(x) = 3x^2 + 2$.**

2. **Apply the power rule to differentiate:** (a) $x^7$; (b) $x^{-3}$; (c) $x^{1/4}$; (d) $\sqrt[3]{x^2}$.

3. **State the product rule, quotient rule, and chain rule** without looking them up.

### Application

4. **Differentiate:** (a) $f(x) = 5x^4 - 3x^2 + 7x - 1$; (b) $f(x) = x^2 \cos x$; (c) $f(x) = (3x + 1)/(x^2 + 1)$; (d) $f(x) = (x^2 + 1)^{10}$.

5. **Differentiate:** (a) $f(x) = e^{2x}$; (b) $f(x) = \ln(x^2 + 1)$; (c) $f(x) = \sin(3x + \pi/4)$; (d) $f(x) = e^{x^2}$.

6. **Find the equation of the tangent line to $f(x) = x^3 - 2x + 1$ at $x = 1$.**

### Synthesis

7. **A particle's position is $s(t) = t^3 - 6t^2 + 9t$ (in meters, $t$ in seconds).** Find the velocity and acceleration as functions of $t$. At what times is the velocity zero? At what times is the acceleration zero?

8. **Use the chain rule to differentiate $f(x) = \ln(\cos(x^2))$.** Identify each layer of the composition and its individual derivative.

### Challenge

9. **The function $f(x) = x|x|$ is differentiable at $x = 0$, but $g(x) = |x|$ is not.** Compute $f'(x)$ for $x > 0$ and $x < 0$, then determine whether the limit exists at $x = 0$. Compare with $g(x) = |x|$, where the analogous limit fails.

10. **For the velocity model $v(t) = v_\text{max}(1 - e^{-t/\tau})$ from §3.7,** show that $\lim_{t \to 0^+} a(t) = v_\text{max}/\tau$ and $\lim_{t \to \infty} a(t) = 0$. What does the second limit say about the car's acceleration as it approaches top speed?

## 3.9 Chapter summary

You walked into this chapter knowing how to compute limits. You walk out with the central computational tool of differential calculus.

The *derivative* of a function at a point is the limit of the average rate of change as the interval shrinks to zero. Geometrically, it's the slope of the tangent line at that point. Physically, it's the instantaneous rate at which the function is changing.

The *differentiation rules* — power, sum, difference, constant multiple, product, quotient, chain — mechanize the routine cases. With the rules and the standard transcendental derivatives in hand, almost any function from Chapter 1 can be differentiated in a few lines.

*Differentiability* is stronger than continuity. A differentiable function must be continuous; the reverse is not true. Corners and vertical tangents block differentiability.

*Higher-order derivatives* iterate. The second derivative is the rate of change of the rate of change; the third derivative is the rate of change of *that*. Each has physical meaning — velocity, acceleration, jerk — for any function describing a quantity changing in time.

The single most important idea: every rate of change is a derivative, and every derivative is a limit of average rates of change as the averaging interval shrinks. The rules are shortcuts; the limit definition is the definition. Whenever a derivative looks strange, return to the limit.

The common mistake to watch for: treating the derivative of a product, quotient, or composition as if it followed the simple algebraic rules for sums. It doesn't. The product rule, quotient rule, and chain rule have their own forms, and they're the most common source of differentiation errors.

## 3.10 Implicit differentiation, in brief

A common situation: a curve is defined not as $y = f(x)$ but by an equation like $x^2 + y^2 = 25$ (a circle of radius 5). Solving for $y$ gives two functions ($y = \pm\sqrt{25 - x^2}$), each describing half the circle. To find the slope of the curve at a given point, *implicit differentiation* differentiates both sides of the original equation with respect to $x$, treating $y$ as a function of $x$ that we don't bother to solve for explicitly.

Differentiating $x^2 + y^2 = 25$:

$$2x + 2y \cdot \frac{dy}{dx} = 0$$

The chain rule produced the $dy/dx$ on the second term — $y$ depends on $x$, so differentiating $y^2$ pulls out $dy/dx$. Solving:

$$\frac{dy}{dx} = -\frac{x}{y}$$

At the point $(3, 4)$ on the circle, the slope is $-3/4$. The technique generalizes to any equation defining $y$ implicitly as a function of $x$, and to inverse-function derivatives (which is how $\frac{d}{dx}(\arcsin x) = 1/\sqrt{1-x^2}$ and other inverse-trig formulas are derived).

## 3.11 Connections forward

Chapter 4 puts the derivative to work. Maxima and minima, optimization problems, related rates, mean-value theorem, curve sketching, L'Hôpital's rule for indeterminate forms — all are applications of the derivative as a tool. The derivative tells you where a function is increasing or decreasing, where it has peaks and troughs, where its concavity changes. Chapter 4 turns those observations into solutions to real problems: finding the cheapest way to manufacture a can, the most efficient angle to throw a projectile, the optimal price to maximize revenue.
