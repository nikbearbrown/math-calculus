# Chapter 4 — Applications of Derivatives

## 4.1 Opening: Tilting a camera up at a rocket

A rocket lifts off from a launch pad. A video camera sits on the ground a fixed distance from the pad. As the rocket climbs, the camera operator must tilt the camera upward to keep the rocket framed in the viewfinder. The angle the camera makes with the ground — call it $\theta$ — increases over time. So does the height of the rocket above the pad — call it $h(t)$. The two quantities are linked by simple geometry: if the camera sits a horizontal distance $D$ from the pad, then $\tan\theta = h/D$.

The question the operator faces is not "what is $\theta$?" — that's just trigonometry. It's "how *fast* does $\theta$ change?" If the rocket is climbing at 100 feet per second when it's 500 feet high, and the camera is 1000 feet from the pad, what angular rate does the camera need to track at? The answer is a derivative — but a derivative tied to *another* derivative through the geometric relationship. As $h$ changes with time, $\theta$ must change with time, and the relationship between $dh/dt$ and $d\theta/dt$ is governed by the equation linking them.

Differentiating $\tan\theta = h/D$ with respect to $t$ — using the chain rule on both sides — gives

$$\sec^2\theta \cdot \frac{d\theta}{dt} = \frac{1}{D} \cdot \frac{dh}{dt}$$

When the rocket is at $h = 500$ ft and the camera at $D = 1000$ ft, $\tan\theta = 0.5$ so $\sec^2\theta = 1 + \tan^2\theta = 1.25$. With $dh/dt = 100$ ft/s:

$$\frac{d\theta}{dt} = \frac{1}{1000 \cdot 1.25} \cdot 100 = 0.08 \text{ rad/s}$$

The camera must tilt at 0.08 radians per second — about 4.6° per second — at that instant. Later, as the rocket climbs higher, the rate slows; at the moment of launch, when $\theta = 0$, the rate is at its peak.

This is one application of derivatives — a *related rate*. There are many. Optimization (find the maximum or minimum of a function under constraints), linear approximation (estimate function values without computing them exactly), curve sketching (use first and second derivatives to draw the graph of a function), L'Hôpital's rule (resolve indeterminate limits using derivatives), Newton's method (find roots of equations by iteration). Each is a structural pattern in which the derivative is the key computational tool.

By the end of this chapter, you should be able to:

- *Solve* related-rates problems by relating the derivatives of two quantities through their geometric or physical link.
- *Apply* the Mean Value Theorem and its corollaries.
- *Locate* absolute and local extrema using the first and second derivative tests.
- *Sketch* the graph of a function by analyzing its derivatives.
- *Apply* L'Hôpital's rule to resolve indeterminate limits.
- *Use* Newton's method to approximate the roots of equations.
- *Compute* antiderivatives — the operation that will become the foundation of integration in Chapter 5.

## 4.2 Related rates

The pattern is general. Two (or more) quantities depend on time. They are linked by an equation. Differentiate the equation with respect to time and you get a relationship among the rates. Plug in known values and solve for the unknown rate.

The structural moves in any related-rates problem:

1. *Identify* what's changing and what's constant. Label the changing quantities with variable names.
2. *Write* the equation that relates them — usually from geometry (Pythagorean, similar triangles, area formulas) or physics.
3. *Differentiate* both sides of the equation with respect to time, treating each variable as a function of $t$. The chain rule fires on every variable that depends on $t$.
4. *Substitute* the known values and the known rates, then *solve* for the unknown rate.

A worked example. A 13-foot ladder leans against a wall. The bottom of the ladder slides outward at 2 ft/s. How fast is the top sliding down when the bottom is 5 feet from the wall?

Let $x$ be the distance from the wall to the bottom, $y$ be the height of the top up the wall. The Pythagorean theorem gives $x^2 + y^2 = 13^2 = 169$.

Differentiate: $2x \frac{dx}{dt} + 2y \frac{dy}{dt} = 0$.

When $x = 5$: $y = \sqrt{169 - 25} = 12$. With $dx/dt = 2$:

$$2(5)(2) + 2(12) \frac{dy}{dt} = 0 \implies \frac{dy}{dt} = -\frac{20}{24} = -\frac{5}{6} \text{ ft/s}$$

The top is sliding down at 5/6 ft/s. The negative sign indicates downward motion (decreasing $y$).

Trade-off in related rates: the technique buys *systematic handling of any geometric setup* at the cost of *requiring the right equation to start*. Most errors come from setting up the wrong relationship. Drawing a picture is almost always worth the time.

## 4.3 Linear approximation and differentials

The tangent line to a function at a point is the best straight-line approximation to the function near that point. For $f$ differentiable at $a$, the tangent line is

$$L(x) = f(a) + f'(a)(x - a)$$

Near $x = a$, $L(x) \approx f(x)$ — the difference goes to zero faster than $(x - a)$. This is *linear approximation*: replace a complicated function by its tangent line for inputs near a known point.

A worked example. Estimate $\sqrt{4.1}$ without a calculator.

Let $f(x) = \sqrt{x}$. Pick $a = 4$, where $f(4) = 2$ exactly. $f'(x) = 1/(2\sqrt{x})$, so $f'(4) = 1/4$.

$$L(x) = 2 + \frac{1}{4}(x - 4)$$

$$L(4.1) = 2 + \frac{1}{4}(0.1) = 2.025$$

The actual value is $\sqrt{4.1} \approx 2.0248$, so the error is about 0.0002 — about 0.01% — using only mental arithmetic.

The linear approximation written in *differential* form: let $dx$ denote a small change in $x$, and let $dy = f'(x) \, dx$ denote the corresponding change predicted by the tangent line. The actual change in $f$ over the interval is $\Delta y = f(x + dx) - f(x)$. The differential $dy$ is the linear estimate of $\Delta y$. For small $dx$, $\Delta y \approx dy$.

The trade-off: linear approximation buys *simple computation* at the cost of *accuracy degrading with distance from $a$*. The further from the anchor point, the worse the approximation. For $f(x) = \sqrt{x}$ anchored at $a = 4$, $L(5) = 2.25$ but $\sqrt{5} \approx 2.236$ — the error is now 0.6%, sixty times what it was at $x = 4.1$.

## 4.4 Maxima, minima, and the critical-point theorem

Find the highest and lowest values of a function on a given domain. This is *optimization* — one of the most-used applications of calculus.

A function $f$ has an *absolute maximum* at $c$ on a domain $D$ if $f(c) \geq f(x)$ for every $x \in D$. *Absolute minimum*: $f(c) \leq f(x)$ for every $x$. The maximum and minimum values are the extreme values of the function.

A function has a *local maximum* at $c$ if $f(c) \geq f(x)$ for every $x$ in some open interval around $c$. *Local minimum*: $f(c) \leq f(x)$ for every $x$ in some open interval. Local extrema are extremes within a neighborhood, not necessarily across the whole domain.

The connecting theorem: at an interior local extremum, $f'(c) = 0$ or $f'(c)$ does not exist. The points where this happens are *critical points*. Every interior local extremum is a critical point; not every critical point is a local extremum.

To find the absolute maximum and minimum of a continuous function $f$ on a closed interval $[a, b]$:

1. Compute $f'(x)$.
2. Find all critical points: where $f'(x) = 0$ or $f'$ is undefined.
3. Evaluate $f$ at every critical point in $(a, b)$ and at the endpoints $a$ and $b$.
4. The largest value is the absolute max; the smallest is the absolute min.

A worked example. Find the absolute maximum and minimum of $f(x) = x^3 - 3x + 1$ on $[-2, 2]$.

$f'(x) = 3x^2 - 3 = 3(x^2 - 1)$. Critical points: $x = \pm 1$. Both lie in $(-2, 2)$, so include them.

Evaluate:
- $f(-2) = -8 + 6 + 1 = -1$
- $f(-1) = -1 + 3 + 1 = 3$
- $f(1) = 1 - 3 + 1 = -1$
- $f(2) = 8 - 6 + 1 = 3$

Absolute max is 3 (achieved at $x = -1$ and $x = 2$). Absolute min is $-1$ (achieved at $x = -2$ and $x = 1$).

## 4.5 The Mean Value Theorem

The Mean Value Theorem (MVT) is the structural backbone of differential calculus's applications. *If $f$ is continuous on $[a, b]$ and differentiable on $(a, b)$, then there exists at least one $c \in (a, b)$ such that*

$$f'(c) = \frac{f(b) - f(a)}{b - a}$$

In words: somewhere on the interval, the instantaneous rate of change equals the average rate of change. Geometrically: the tangent line at some point $c$ is parallel to the secant line connecting the endpoints.

The special case where $f(a) = f(b)$ is *Rolle's theorem*: under the same continuity and differentiability conditions plus equal endpoint values, there exists $c$ with $f'(c) = 0$. A function that returns to its starting value must have at least one moment where its instantaneous rate is zero.

The MVT is what proves several familiar facts:

- *If $f'(x) = 0$ for all $x$ on an interval, then $f$ is constant on that interval.* If two points had different values, the MVT would force some $c$ with non-zero derivative — contradiction.
- *If $f'(x) > 0$ on an interval, then $f$ is increasing on that interval.* The MVT applied to any two points gives a positive secant slope.
- *If $f'(x) = g'(x)$ on an interval, then $f$ and $g$ differ by a constant.* Apply the first corollary to $f - g$.

The third corollary becomes critical in Chapter 5: it tells us that *all antiderivatives of a function differ by a constant*, the basis for the constant of integration $+C$.

## 4.6 The first and second derivative tests, and curve sketching

How to tell which critical points are maxima and which are minima.

*First derivative test*. If $f$ is continuous and $c$ is a critical point:

- If $f'$ changes from positive to negative at $c$, then $c$ is a local maximum.
- If $f'$ changes from negative to positive at $c$, then $c$ is a local minimum.
- If $f'$ doesn't change sign, $c$ is neither.

*Second derivative test*. If $f'(c) = 0$ and $f''(c)$ exists:

- If $f''(c) < 0$, then $c$ is a local maximum (concave down at $c$).
- If $f''(c) > 0$, then $c$ is a local minimum (concave up).
- If $f''(c) = 0$, the test is inconclusive — fall back to the first derivative test.

*Concavity*. A function is *concave up* on an interval if its graph lies above all its tangent lines (or equivalently, $f''(x) > 0$). It's *concave down* if its graph lies below all its tangent lines ($f''(x) < 0$). An *inflection point* is where concavity changes — typically where $f''(x) = 0$ and changes sign.

The curve-sketching procedure. To produce an accurate graph of $f$:

1. Find the domain.
2. Find $x$- and $y$-intercepts.
3. Determine symmetry (even, odd, neither).
4. Find vertical asymptotes ($f$ blows up) and horizontal asymptotes (limits at $\pm\infty$).
5. Compute $f'(x)$, find critical points, determine intervals of increase/decrease.
6. Apply first or second derivative test to classify critical points.
7. Compute $f''(x)$, find candidate inflection points, determine intervals of concavity.
8. Plot the gathered information and sketch.

Done carefully, this produces a remarkably accurate picture from a derivative analysis alone.

## 4.7 Optimization in applied contexts

Optimization problems take a real situation and turn it into a max-or-min computation. The pattern:

1. *Identify* what's being optimized (the objective: cost, revenue, area, time, etc.).
2. *Identify* the constraint (a fixed amount of material, a fixed time budget, a geometric relationship).
3. *Write* the objective as a function of one variable, using the constraint to eliminate any others.
4. *Apply* the critical-point method to find candidate optima.
5. *Verify* using the second derivative test or by checking endpoints.
6. *Interpret* the answer in the original problem's context.

A worked example. A rectangular field is to be enclosed by 100 feet of fencing, with one side being a wall (which doesn't need fencing). Find the dimensions that maximize the area.

Let $x$ be the length of the side parallel to the wall, $y$ the length perpendicular. Total fencing: $x + 2y = 100$, so $x = 100 - 2y$.

Objective: maximize $A = xy = (100 - 2y) y = 100y - 2y^2$.

Differentiate: $A'(y) = 100 - 4y$. Set to zero: $y = 25$. Second derivative $A''(y) = -4 < 0$, confirming maximum.

When $y = 25$, $x = 50$. Maximum area = $25 \times 50 = 1250$ square feet.

The shape of the answer (one side twice the other) is characteristic of fencing-against-a-wall problems and recurs in many optimization contexts. The optimal proportions are not always intuitive; the calculus gets them right.

## 4.8 L'Hôpital's rule, Newton's method, and antiderivatives

Three more applications, briefly.

*L'Hôpital's rule*. If $\lim_{x \to a} f(x) = \lim_{x \to a} g(x) = 0$ (or both $\pm\infty$), and the limit $\lim_{x \to a} f'(x)/g'(x)$ exists, then

$$\lim_{x \to a} \frac{f(x)}{g(x)} = \lim_{x \to a} \frac{f'(x)}{g'(x)}$$

The rule resolves $0/0$ and $\infty/\infty$ indeterminate forms by replacing them with derivatives. It also handles forms that can be rewritten as 0/0 or $\infty/\infty$ — products of $0 \cdot \infty$, differences of $\infty - \infty$, exponential forms $0^0$, $1^\infty$, $\infty^0$ — typically by taking logarithms or rewriting as fractions.

Example: $\lim_{x \to 0} (\sin x)/x$ is $0/0$. Apply L'Hôpital: $\lim_{x \to 0} \cos x / 1 = 1$.

*Newton's method*. To find a root of $f(x) = 0$ — a value of $x$ where the function crosses zero — start with a guess $x_0$ and iterate:

$$x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}$$

Geometrically: at the current guess, draw the tangent line; the root of the tangent line is the next guess. The method converges to a root, often quadratically (the number of correct digits roughly doubles each iteration).

Example: find $\sqrt{2}$ by solving $f(x) = x^2 - 2 = 0$. Start with $x_0 = 1$. $f'(x) = 2x$.

- $x_1 = 1 - (1^2 - 2)/(2 \cdot 1) = 1 - (-1)/2 = 1.5$
- $x_2 = 1.5 - (2.25 - 2)/(2 \cdot 1.5) = 1.5 - 0.0833 = 1.4167$
- $x_3 = 1.4167 - (2.0070 - 2)/(2.8333) \approx 1.4142$

Three iterations from a poor starting guess get $\sqrt{2}$ correct to four decimals.

*Antiderivatives*. The reverse operation of differentiation: given $f$, find $F$ such that $F'(x) = f(x)$. $F$ is called an antiderivative of $f$.

By the MVT corollary in §4.5, antiderivatives of a given function differ only by a constant. The general antiderivative is denoted

$$\int f(x) \, dx = F(x) + C$$

— the *indefinite integral* of $f$, where $C$ is the *constant of integration*, an arbitrary additive constant.

Standard antiderivatives by reversal of standard derivatives:

- $\int x^n \, dx = \frac{x^{n+1}}{n+1} + C$ for $n \neq -1$
- $\int x^{-1} \, dx = \ln|x| + C$
- $\int e^x \, dx = e^x + C$
- $\int \cos x \, dx = \sin x + C$
- $\int \sin x \, dx = -\cos x + C$

The antiderivative is the bridge to Chapter 5's integration. The Fundamental Theorem of Calculus, which we'll meet there, will reveal that the integral (in its original meaning, an accumulation of small contributions) and the antiderivative (the formal reverse of differentiation) are the same operation.

## 4.9 Synthesis: rocket and camera, fully

Return to §4.1's rocket. With the camera at distance $D = 1000$ ft from the pad and the rocket's height $h(t)$ a function of time, $\tan\theta(t) = h(t)/1000$.

Suppose the rocket's height follows $h(t) = 16 t^2$ (a uniformly accelerating ascent, the standard Galilean form). Then $h'(t) = 32 t$ and the camera's required angular rate is

$$\sec^2\theta \cdot \theta' = \frac{32 t}{1000} = 0.032 t$$

When $h = 500$: $16 t^2 = 500$, so $t = 5.59$ seconds. At that moment $\tan\theta = 0.5$, $\sec^2\theta = 1.25$, and

$$\theta' = \frac{0.032 \cdot 5.59}{1.25} \approx 0.143 \text{ rad/s}$$

(The opening's $0.08$ rad/s used $dh/dt = 100$ ft/s as a snapshot; this synthesis derives $dh/dt$ from the assumed model and gets a different number consistent with that model.)

The angular rate $\theta'$ is itself a function of time. Its derivative is the *angular acceleration* — the rate the camera operator's tilt-rate must change. This is where the second derivative comes in. If the operator's hand cannot smoothly accelerate the camera, *jerk* — the third derivative — becomes the limiting variable. Engineers designing camera mounts for live launch broadcasts compute exactly this kind of derivative chain.

Optimization: at what altitude does the angular rate peak? Differentiating $\theta'(t)$ with respect to time, setting equal to zero, and solving — a single critical-point computation — gives the answer.

Linear approximation: if the operator is tracking the rocket and wants to predict where the angle will be 0.1 second from now, multiply the current angular rate by 0.1 and add to the current angle. The accuracy is excellent for short forecasts.

L'Hôpital: at $t = 0$ (launch), both $h$ and $\tan\theta$ are zero. The ratio $\theta(t)/t$ is $0/0$ as $t \to 0$. L'Hôpital resolves it as $\theta'(0)/1$, the launch angular rate.

Antiderivatives: knowing the angular rate over time, integrate to recover the angle. This is what Chapter 5 makes systematic.

Every section of the chapter shows up in the application. The derivative is not a single tool but a family of tools, each suited to a particular question about how things change.

## 4.10 Exercises

### Warm-up

1. **A 10-foot ladder slides down a wall.** When the bottom is 6 feet from the wall, it's moving outward at 1 ft/s. How fast is the top sliding down?

2. **Use linear approximation** to estimate $\sqrt[3]{27.1}$.

3. **Find the critical points of $f(x) = x^3 - 12x + 5$** and classify each using the second derivative test.

### Application

4. **Find the absolute extrema of $f(x) = x^4 - 8x^2 + 16$ on $[-3, 3]$.**

5. **A box with a square base and open top must hold 32 cubic feet.** Find the dimensions that minimize the surface area.

6. **Apply L'Hôpital's rule:** (a) $\lim_{x \to 0} (e^x - 1)/x$; (b) $\lim_{x \to \infty} \ln x / x$; (c) $\lim_{x \to 0^+} x \ln x$.

### Synthesis

7. **Sketch the graph of $f(x) = x^3 - 3x^2 + 1$** by analyzing its derivatives. Identify intercepts, critical points, intervals of increase/decrease, concavity, and inflection points.

8. **Apply two iterations of Newton's method** starting from $x_0 = 2$ to estimate the positive root of $f(x) = x^2 - 5$. Compute the error against $\sqrt{5}$.

### Challenge

9. **A right triangle has legs of length $a$ and $b$ with $a + b = 10$.** Find $a$ and $b$ that maximize the area. Then find $a$ and $b$ that maximize the hypotenuse. Discuss why the two answers differ.

10. **For the rocket-and-camera setup of §4.9** with $h(t) = 16t^2$, $D = 1000$ ft, find the time at which the angular tilt-rate $\theta'(t)$ reaches its maximum. (You'll need to differentiate $\theta'$ as a function of $t$ — the chain rule applied through $\sec^2\theta$.)

## 4.11 Chapter summary

You walked into this chapter knowing how to differentiate. You walk out knowing what to *do* with derivatives.

*Related rates* link the time-derivatives of two quantities through their geometric or physical relationship. *Linear approximation* uses the tangent line to estimate function values. *Maxima and minima* — local and absolute — are found at critical points where the derivative is zero or undefined. The *Mean Value Theorem* connects the average rate of change over an interval to the instantaneous rate at some point in the interval, and its corollaries underpin the basic facts about increasing and decreasing functions.

The *first and second derivative tests* classify critical points. *Curve sketching* uses derivative analysis to produce accurate graphs without point-by-point plotting. *Optimization* turns real problems — minimum cost, maximum area, fastest route — into critical-point computations.

*L'Hôpital's rule* resolves indeterminate limits using derivatives. *Newton's method* finds roots of equations by iterating along tangent lines. *Antiderivatives* — the reverse of differentiation — are the bridge to Chapter 5's integration.

The single most important idea: the derivative is not just a slope. It's a unit of measurement for change, deployable wherever a question of rate, optimization, approximation, or accumulation arises. Each section of this chapter is one structural pattern in which the derivative is the answer.

The common mistake to watch for: applying L'Hôpital's rule without first checking that the form is genuinely indeterminate. The rule fails for forms that aren't $0/0$ or $\infty/\infty$. Substitute first; only apply the rule if substitution gives an indeterminate result.

## 4.12 Connections forward

Chapter 5 takes the antiderivative of §4.8 and turns it into the *integral* — the second great operation of calculus. The integral arose historically as a method for computing accumulated quantities: areas under curves, total distances from velocity, total works from forces. The Fundamental Theorem of Calculus, which Chapter 5 develops, will show that this accumulation operation and the antiderivative are the same thing. Differentiation and integration are inverse operations. Chapter 5 closes the loop.
