# Chapter 1 — Functions and Graphs

## 1.1 Opening: Three numbers, no scale

In January 2010 an earthquake of magnitude 7.3 struck Haiti. In March 2011 a magnitude 9 quake shook northeastern Japan. In April 2014 an 8.2-magnitude quake struck off the coast of northern Chile. Three numbers — 7.3, 8.2, 9 — close together on the page. They look almost the same. They were not the same. Each of those single-digit increments hides a tenfold leap in shaking energy and a roughly thirty-twofold leap in released seismic energy. The Japan quake of 2011 was not slightly worse than the Haiti quake of 2010. It was hundreds of times more intense.

The reason the numbers compress that much information into so little space is that the Richter scale is not linear. It's *logarithmic*. The magnitude is the logarithm (base 10) of a measured amplitude, so each unit increase on the scale is a multiplication, not an addition, in the underlying physical quantity. To compare the three quakes you have to undo the logarithm — to apply the *inverse function*, the exponential. To know what 9 minus 7.3 means, you compute $10^{9-7.3} = 10^{1.7} \approx 50$. The Japan quake released roughly fifty times the ground-motion amplitude of the Haiti quake. To know what that means in *energy*, you raise the result to the 1.5 power (because seismic energy scales as amplitude to the 1.5), giving roughly $50^{1.5} \approx 350$. Different scales of comparison; same machinery underneath. Functions, their inverses, and the algebra of the families they live in.

This chapter is the algebraic preamble to calculus. It assumes you know what a function is in some intuitive sense and reminds you precisely what one is, what the major families of functions look like, how to combine them, how to invert them, and which inverses (logarithms in particular) collapse multiplications into additions. By the end of the chapter, you should be able to:

- *Determine* the domain and range of a function defined by a formula, a table, or a graph.
- *Combine* functions through addition, subtraction, multiplication, division, and composition.
- *Classify* a given function as polynomial, rational, algebraic, or transcendental, and identify which family it belongs to.
- *Apply* trigonometric identities and the unit-circle definitions of $\sin$, $\cos$, $\tan$, $\cot$, $\sec$, $\csc$.
- *Construct* the inverse of a one-to-one function and *recognize* when a function has no inverse on its full domain.
- *Compute* with exponential and logarithmic functions and *use* logarithms to compare quantities that span many orders of magnitude.

You walk in with high-school algebra: graphing lines, factoring polynomials, working with fractions. You walk out with the function vocabulary calculus assumes you have. Calculus itself starts in Chapter 2.

Why does this chapter matter? Because every concept in calculus — limits, derivatives, integrals — is *about* functions. If "function" remains a fuzzy idea by Chapter 2, the rest of the course is built on sand. The polynomial and trigonometric and exponential and logarithmic functions you'll meet here are the species of the calculus zoo. Knowing what each one looks like — its shape, its growth rate, its symmetries, its inverse — is what makes calculus tractable when it gets going.

## 1.2 What a function is

A *function* is a rule that assigns to each element of a set $D$ — the *domain* — exactly one element of a set $R$ — the *range*. Notation: $f \colon D \to R$, with $f(x)$ denoting the unique element of $R$ assigned to $x \in D$. The "exactly one" is the defining feature. A rule that assigns *two* outputs to a single input is not a function.

The set $D$ where the function is defined is the *domain*. The set $R$ where outputs land is the *range*. For a function defined by a formula, the *natural domain* is usually the largest set on which the formula makes sense — for $f(x) = 1/(x-2)$, every real number except $x = 2$, since division by zero is undefined.

Functions get represented four ways, and a fluent calculus student moves between them effortlessly.

*By formula*: $f(x) = x^2 + 3x - 1$. Compact, exact, computable.

*By graph*: a curve in the $(x,y)$-plane, with each $x$ in the domain associated with the height $y = f(x)$. The *vertical line test* is the visual restatement of the "exactly one output" rule — any vertical line crosses the graph of a function in at most one point.

*By table*: a finite list of input-output pairs. Useful for empirical data; incomplete in principle, since most functions have infinitely many inputs.

*By words*: "the height of a thrown ball $t$ seconds after release" or "the temperature in Boston at noon on the $n$th day of the year." Verbal definitions are how functions arise in real applications, before being given a formula.

A function $f$ has a *zero* (or *root*) at $x = a$ if $f(a) = 0$. A function is *increasing* on an interval if larger inputs give larger outputs there; *decreasing* if larger inputs give smaller outputs.

Two functions can be combined to make new ones. *Sum, difference, product, quotient*: $(f+g)(x) = f(x) + g(x)$, $(f-g)(x) = f(x) - g(x)$, $(fg)(x) = f(x)g(x)$, $(f/g)(x) = f(x)/g(x)$ where $g(x) \neq 0$. Each combination has its own domain — the intersection of the original domains, minus any zeros of $g$ for the quotient.

*Composition* is the operation that distinguishes functions from numbers: $(f \circ g)(x) = f(g(x))$. Read "f of g of x." First apply $g$ to $x$; then apply $f$ to the result. Composition is *not commutative* — $f \circ g$ and $g \circ f$ are typically different functions. Example: with $f(x) = x^2$ and $g(x) = x + 1$:

$$
(f \circ g)(x) = f(g(x)) = (x+1)^2 = x^2 + 2x + 1
$$
$$
(g \circ f)(x) = g(f(x)) = x^2 + 1
$$

Different functions.

*Symmetry*. A function $f$ is *even* if $f(-x) = f(x)$ for every $x$ in the domain — its graph is mirror-symmetric across the $y$-axis (think $f(x) = x^2$ or $\cos x$). A function $f$ is *odd* if $f(-x) = -f(x)$ for every $x$ — its graph has 180° rotational symmetry about the origin (think $f(x) = x^3$ or $\sin x$). Most functions are neither.

The trade-off in choosing which representation to use: formulas buy *exact computability* at the cost of *visual intuition*; graphs buy *intuition* at the cost of *precision*; tables buy *concreteness* at the cost of *generality*; verbal definitions buy *applicability* at the cost of *manipulability*. Real calculus problems shuttle constantly between the four representations, picking whichever serves the immediate question.

A common misconception worth flagging now: students often confuse the function $f$ with the *output* $f(x)$. The function is the rule; $f(x)$ is one specific number you get by applying the rule. Writing "the function $f(x) = x^2$" is informal but common; strictly, the function is $f$, and $f(x) = x^2$ describes the rule.

## 1.3 The families of functions

Calculus works mostly with functions that fall into a small set of standard families. Knowing the family lets you predict behavior — growth rate, periodicity, where it's defined, whether it's smooth.

### Polynomial functions

A *polynomial* of degree $n$ has the form $f(x) = a_n x^n + a_{n-1}x^{n-1} + \cdots + a_1 x + a_0$, where the $a_i$ are real numbers and $a_n \neq 0$. Every polynomial is defined for all real $x$. The leading term $a_n x^n$ controls behavior as $x \to \pm\infty$: positive even leading coefficient → both ends go up; positive odd → up on the right and down on the left; negative even → both ends down; negative odd → down on the right, up on the left.

*Linear functions* are polynomials of degree 1: $f(x) = mx + b$, with $m$ the *slope* and $b$ the $y$-intercept. The slope is the rate of change; for any two points $(x_1, y_1)$ and $(x_2, y_2)$ on the line, $m = (y_2 - y_1)/(x_2 - x_1)$.

*Quadratic functions* are degree 2: $f(x) = ax^2 + bx + c$ with $a \neq 0$. Their graphs are parabolas — opening up if $a > 0$, down if $a < 0$. The vertex sits at $x = -b/(2a)$.

### Algebraic functions

A function is *algebraic* if it can be built from polynomials using addition, subtraction, multiplication, division, and roots. *Rational functions* — quotients of polynomials, $f(x) = p(x)/q(x)$ — are algebraic. So are *root functions* like $\sqrt{x}$ and $\sqrt[3]{x^2 + 1}$. The domain of an algebraic function may be restricted: $\sqrt{x}$ is defined only for $x \geq 0$; $1/(x-2)$ is undefined at $x = 2$.

### Transcendental functions

Functions that *cannot* be built algebraically are called *transcendental* (Latin: "going beyond"). The major transcendentals in calculus are *trigonometric* ($\sin, \cos, \tan$, etc.), *exponential* ($f(x) = b^x$ for fixed base $b > 0, b \neq 1$), and *logarithmic* ($f(x) = \log_b x$). Transcendental functions transcend algebra in the sense that no finite sequence of algebraic operations can construct them.

### Piecewise-defined functions

Some functions are defined by different formulas on different parts of their domain. The *absolute value* function:

$$
|x| = \begin{cases} x & \text{if } x \geq 0 \\ -x & \text{if } x < 0 \end{cases}
$$

The graph is two rays meeting at the origin, forming a "V."

### Transformations

A small set of operations on a function $f$ produces a predictable family of related functions:

- $f(x) + c$ shifts the graph up by $c$ (down if $c < 0$).
- $f(x + c)$ shifts the graph left by $c$ (right if $c < 0$). The sign-flip is the trap; it catches everyone the first time.
- $cf(x)$ stretches vertically by factor $c$ (or compresses if $|c| < 1$, or reflects across the $x$-axis if $c < 0$).
- $f(cx)$ compresses horizontally by factor $c$ (or stretches if $|c| < 1$, or reflects across the $y$-axis if $c < 0$).

These four transformations (vertical/horizontal shift and stretch) generate, between them, every linear modification of a graph.

The trade-off in classifying a function: you gain prediction (knowing it's a degree-3 polynomial tells you everything about end behavior, smoothness, and how many roots it can have at most) at the cost of remembering the classifications. Memorizing the family templates pays for itself a hundred times over once calculus starts in Chapter 2.

A common misconception: that an exponential function $b^x$ and a power function $x^b$ are the same. They aren't. In $b^x$ the *exponent* is the variable; the function grows or decays at a constant percentage rate. In $x^b$ the *base* is the variable; the function follows a polynomial-style power law. They are radically different — exponentials eventually outgrow every polynomial.

## 1.4 The trigonometric family

The trigonometric functions arise from right-triangle ratios but are most usefully understood on the *unit circle*. Define an angle $\theta$ as the directed arc length from $(1,0)$ along the unit circle (counterclockwise positive). The point on the circle at angle $\theta$ is $(\cos\theta, \sin\theta)$. From those two basic functions, the others follow:

$$
\tan\theta = \frac{\sin\theta}{\cos\theta}, \quad \cot\theta = \frac{\cos\theta}{\sin\theta}, \quad \sec\theta = \frac{1}{\cos\theta}, \quad \csc\theta = \frac{1}{\sin\theta}
$$

Angles in calculus are measured in *radians*, not degrees. One radian is the angle subtended at the center of a unit circle by an arc of length 1. The full circle has circumference $2\pi$, so $360° = 2\pi$ radians, $180° = \pi$, $90° = \pi/2$, $60° = \pi/3$, $45° = \pi/4$, $30° = \pi/6$. Radian measure is what makes the calculus of trigonometric functions clean — derivatives like $(\sin\theta)' = \cos\theta$ hold only when $\theta$ is in radians.

The *Pythagorean identity* — $\sin^2\theta + \cos^2\theta = 1$ — comes directly from the unit circle: any point $(x, y)$ on it satisfies $x^2 + y^2 = 1$. Dividing through by $\cos^2\theta$ gives $\tan^2\theta + 1 = \sec^2\theta$. Dividing by $\sin^2\theta$ gives $1 + \cot^2\theta = \csc^2\theta$.

The *angle-sum identities*:

$$
\sin(\alpha + \beta) = \sin\alpha\cos\beta + \cos\alpha\sin\beta
$$
$$
\cos(\alpha + \beta) = \cos\alpha\cos\beta - \sin\alpha\sin\beta
$$

The angle-difference and double-angle formulas follow from these by substitution.

*Periodicity*. Every trig function repeats. $\sin\theta$ and $\cos\theta$ have period $2\pi$ — the unit-circle position returns to its starting place after a full revolution. $\tan\theta$ has period $\pi$ — the ratio $\sin/\cos$ returns to itself after only half a revolution because both $\sin$ and $\cos$ flip sign together.

The trade-off in trig: the unit-circle definitions buy *all six functions in one geometric picture* at the cost of *requiring radian measure to make calculus work cleanly*. Degree-based trig is fine for surveying or basic geometry; calculus demands radians.

A worked example. Find $\sin(7\pi/6)$ exactly. Step 1: locate the angle. $7\pi/6 = \pi + \pi/6$, so it's the standard $\pi/6$ angle rotated past the negative $x$-axis — a third-quadrant angle. Step 2: at the reference angle $\pi/6$, $\sin(\pi/6) = 1/2$. Step 3: in the third quadrant, $\sin$ is negative. So $\sin(7\pi/6) = -1/2$. The structural pattern: every trig value at a non-standard angle reduces to a reference-angle value plus a sign chosen by quadrant.

## 1.5 Inverse functions, exponentials, and logarithms

The Richter-scale story from §1.1 was about inverses. The magnitude $M$ of an earthquake is a logarithm of a measured amplitude $A$: $M = \log_{10}(A/A_0)$ where $A_0$ is a reference. To recover $A$ from $M$, you apply the inverse — the exponential — and write $A = A_0 \cdot 10^M$. The two functions undo each other.

A function $f$ has an *inverse* $f^{-1}$ if and only if $f$ is *one-to-one*: each output corresponds to exactly one input. The condition can be tested visually with the *horizontal line test* — any horizontal line should cross the graph of $f$ in at most one point. The function $f(x) = x^2$ on the full real line is *not* one-to-one (since $f(2) = f(-2) = 4$); restrict it to $x \geq 0$ and it becomes one-to-one, with inverse $f^{-1}(x) = \sqrt{x}$. Restriction is how non-one-to-one functions get inverses anyway.

The defining equations of an inverse: $f^{-1}(f(x)) = x$ for all $x$ in the domain of $f$, and $f(f^{-1}(y)) = y$ for all $y$ in the range of $f$. The graphs of $f$ and $f^{-1}$ are mirror images across the line $y = x$.

To find the inverse algebraically: write $y = f(x)$, swap $x$ and $y$, solve for $y$. The result is $y = f^{-1}(x)$.

Worked example. $f(x) = x^3 + 4$. Set $y = x^3 + 4$. Swap: $x = y^3 + 4$. Solve: $y^3 = x - 4$, so $y = \sqrt[3]{x - 4}$. So $f^{-1}(x) = \sqrt[3]{x - 4}$. Check: $f^{-1}(f(x)) = \sqrt[3]{(x^3 + 4) - 4} = \sqrt[3]{x^3} = x$. ✓

### Exponential functions

An *exponential function* has the form $f(x) = b^x$ where $b > 0$ and $b \neq 1$. The number $b$ is the *base*. The domain is all of $\mathbb{R}$; the range is $(0, \infty)$ — exponentials never reach zero or go negative. If $b > 1$, the function increases (exponential growth). If $0 < b < 1$, it decreases (exponential decay).

The natural exponential is $f(x) = e^x$ where $e \approx 2.71828$ is *Euler's number*. The choice of $e$ is not arbitrary; it is the unique base for which the derivative of $b^x$ equals $b^x$ itself. We'll see why in Chapter 3.

Exponential functions satisfy *exponent rules*:

$$
b^x \cdot b^y = b^{x+y}, \quad \frac{b^x}{b^y} = b^{x-y}, \quad (b^x)^y = b^{xy}, \quad b^0 = 1
$$

These hold for all real exponents — not just integer ones. They are what makes exponential algebra work.

### Logarithmic functions

The logarithm base $b$, written $\log_b x$, is the inverse of the exponential $b^x$. By definition: $\log_b x = y$ if and only if $b^y = x$.

Three logarithm rules follow from the exponent rules above:

$$
\log_b(xy) = \log_b x + \log_b y \quad \text{(product rule)}
$$
$$
\log_b\!\left(\frac{x}{y}\right) = \log_b x - \log_b y \quad \text{(quotient rule)}
$$
$$
\log_b(x^p) = p \log_b x \quad \text{(power rule)}
$$

These are what make logarithms useful: they convert multiplications into additions, divisions into subtractions, and powers into multiplications. Before pocket calculators, this was how all multidigit multiplications were done — convert to logarithms (look up in a table), add, convert back (look up the antilog).

The *common logarithm* is $\log_{10} x$, often written just $\log x$. The *natural logarithm* is $\log_e x$, written $\ln x$. The *change-of-base formula*:

$$
\log_b x = \frac{\ln x}{\ln b}
$$

lets any logarithm be computed from natural logs.

### Closing the earthquake loop

Back to the cold open. The Richter magnitude $M$ of an earthquake is $M = \log_{10}(A/A_0)$ where $A$ is the measured ground-motion amplitude and $A_0$ is a reference. The Japan quake had $M = 9$; the Haiti quake had $M = 7.3$. The ratio of amplitudes:

$$
\frac{A_\text{Japan}}{A_\text{Haiti}} = \frac{10^{M_\text{Japan}} A_0}{10^{M_\text{Haiti}} A_0} = 10^{9 - 7.3} = 10^{1.7} \approx 50
$$

The Japan amplitude was 50 times the Haiti amplitude. The released seismic energy scales as amplitude to the 1.5 power, so the energy ratio is $50^{1.5} \approx 350$. Two single-digit numbers on the same scale, hiding a 350-fold difference in destructive energy, separated only by the structural fact that one transformation in the chain was a logarithm. Knowing how to undo it — knowing the exponential is the inverse — is what lets you compare what the news anchor cannot.

The trade-off in logarithmic reporting: it buys *compact human-readable scales for quantities that span many orders of magnitude* at the cost of *making naive comparison misleading*. You need to know to undo the log before subtracting. The pH scale, decibels, magnitudes of stars, the Kardashev scale, the Saffir-Simpson hurricane scale — all logarithmic for the same reason. All require the same inverse step before comparison.

## 1.6 Synthesis: the pre-calculus toolkit

Pull all of this together. A function is a rule. Functions come in families — polynomial, algebraic, transcendental — and each family has predictable behavior. They can be combined arithmetically and through composition. They can be transformed by shifts, stretches, and reflections. They have inverses when they're one-to-one; the inverse undoes what the function did. The exponential and logarithmic functions are inverses of each other, and that relationship lets us compress quantities that span many orders of magnitude into manageable scales.

A worked synthesis problem. The Belgian mathematician Pierre-François Verhulst (whose name is not in the source — let me restate without that attribution): the source's running example for population dynamics uses the functional form

$$
P(t) = \frac{P_0 K e^{rt}}{K + P_0(e^{rt} - 1)}
$$

where $P_0$ is initial population, $K$ is carrying capacity, $r$ is growth rate, and $t$ is time. (Source-faithfully simplified to its general form.) This single expression combines *every* category of function the chapter covered:

- $e^{rt}$ — exponential
- $K + P_0(e^{rt} - 1)$ — polynomial in the exponential, divided in the next step
- $P(t) = \text{numerator}/\text{denominator}$ — rational *in the exponential*
- The whole thing is a *transcendental* function of $t$
- Composition is everywhere ($e^{rt}$ is itself a composition of $e^x$ with the linear function $rt$)
- It is one-to-one for $t \geq 0$ (each population corresponds to one time), so it has an inverse — *time as a function of population* — found by algebraically solving for $t$ in terms of $P$, which is a logarithm (the natural inverse of the exponential).

The chapter's whole vocabulary — polynomial, rational, exponential, composition, inverse — appears in a single working formula. Calculus needs all of it.

## 1.7 Exercises

### Warm-up

1. **State the domain of each function:** (a) $f(x) = \sqrt{x-3}$; (b) $g(x) = 1/(x^2 - 4)$; (c) $h(x) = \ln(x+1)$.

2. **Determine whether each function is even, odd, or neither:** (a) $f(x) = x^4 - 3x^2$; (b) $g(x) = x^3 + x$; (c) $h(x) = x^2 + x$.

3. **Convert to radians:** 30°, 45°, 60°, 90°, 180°.

### Application

4. **Given $f(x) = 2x + 1$ and $g(x) = x^2$, compute $(f \circ g)(x)$ and $(g \circ f)(x)$.** Verify they are different.

5. **Find the inverse of $f(x) = (x+2)/(x-1)$** on the natural domain where it is one-to-one. Verify $f(f^{-1}(x)) = x$.

6. **Two earthquakes register magnitudes 6.5 and 8.0.** Compute the ratio of their amplitudes. Then compute the ratio of their seismic energies (which scales as amplitude raised to the 1.5 power).

### Synthesis

7. **A radioactive isotope has half-life 10 years.** Write the amount remaining as an exponential function of time, given starting mass $M_0$. Then express the time to reach $M_0/100$ as a logarithm and compute it numerically.

8. **Solve $\log_2(x+1) + \log_2(x-1) = 3$** for $x$. Combine the logs first; check the resulting solutions against the original domain.

### Challenge

9. **The function $f(x) = \cos x$ is not one-to-one on its full domain.** Describe the largest interval containing 0 on which $\cos$ is one-to-one. Define the inverse cosine $\arccos$ on this restricted domain. Explain why the resulting inverse is undefined for $|x| > 1$.

10. **Express $\sin(2\theta)$ as an algebraic function of $\sin\theta$ and $\cos\theta$, then as an algebraic function of $\sin\theta$ alone for $\theta$ in $[0, \pi/2]$.** Discuss why the second expression requires the domain restriction.

## 1.8 Chapter summary

You walked into this chapter with high-school algebra and an intuitive sense of what a function is. You walk out with the precise vocabulary calculus assumes you have.

A function is a rule that assigns to each input exactly one output. Functions come in families — polynomial, algebraic, transcendental — and within those families, they have predictable graph shapes, growth rates, and behaviors. They can be combined arithmetically and by composition. They can be transformed by shifts, stretches, and reflections. They have inverses when they're one-to-one; the inverse undoes what the function did, and its graph is the original's mirror image across $y = x$.

The exponential and logarithmic functions are inverses of each other and form the bridge between additive and multiplicative scales. Trigonometric functions, defined on the unit circle in radians, are periodic and satisfy a small library of identities that the rest of calculus depends on.

The single most important idea: every concept in calculus operates on functions, not on numbers. A *limit* will be the value a function approaches; a *derivative* will be the rate of change of a function; an *integral* will be an accumulation of function values. If "function" stays a fuzzy idea, the rest of the course doesn't land.

The common mistake to watch for: confusing a function with the formula representing it, or with a particular output it produces. The function is the rule. The formula or graph is one way of writing it down. The output $f(a)$ for a specific $a$ is one number it produces. All three are useful; they aren't the same thing.

## 1.9 Connections forward

Chapter 2 introduces the *limit* — the foundational concept of calculus. With a function $f$ and an input $a$, the question "what value does $f(x)$ approach as $x$ gets close to $a$?" is a different question from "what is $f(a)$?" The two answers can differ, and the difference between them is what makes the calculus possible. By the end of Chapter 2 you'll know what a limit is, how to compute one for the standard families of functions you met here, and what it means for a function to be *continuous*.
