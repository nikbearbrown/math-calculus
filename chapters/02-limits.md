# Chapter 2 — Limits

## 2.1 Opening: The speed Einstein said you cannot reach

In 1905, Albert Einstein published the relativity equation that fixed the upper limit of motion in the universe. The mass of an object moving at speed $v$, measured by a stationary observer, is

$$m = \frac{m_0}{\sqrt{1 - \dfrac{v^2}{c^2}}}$$

where $m_0$ is the object's *rest mass* and $c$ is the speed of light. Watch what this formula does.

At everyday speeds — even an aircraft at 600 mph, even the International Space Station at 17,500 mph — the ratio $v/c$ is tiny, so $v^2/c^2$ is microscopically small, the denominator is almost exactly 1, and the moving mass is almost exactly the rest mass. Relativistic effects are present; they are unmeasurably small. Push $v$ up. At 0.1 $c$ — about 67 million mph — the denominator is $\sqrt{1 - 0.01} \approx 0.995$, so the moving mass is about 0.5% larger than rest mass. Real, but mild. At 0.5 $c$ the denominator drops to $\sqrt{0.75} \approx 0.866$, and moving mass is about 15% larger. At 0.9 $c$, the denominator is $\sqrt{0.19} \approx 0.436$, so moving mass is roughly 2.3 times rest mass. At 0.99 $c$, the denominator is about 0.141 and the mass ratio about 7.1. At 0.999 $c$, mass ratio about 22. At 0.9999 $c$, about 71.

The mass *grows without bound* as $v$ approaches $c$. To accelerate the object further requires more force, because force equals mass times acceleration, and the mass keeps climbing. The energy required to push a finite-rest-mass object all the way to the speed of light is *infinite*. That is the speed limit Einstein discovered.

Notice what the equation never says. It never says "at $v = c$, the mass is $\infty$." It says: as $v$ approaches $c$, the mass grows without bound. The equation has no value at $v = c$ — the denominator is zero, and division by zero is undefined. There is no point on the graph at $v = c$. There is only an asymptote that the curve approaches and never reaches.

This is what a *limit* is. Not a value the function takes at a particular input. A value the function approaches as the input approaches a particular target. The two ideas are different — and the difference between them is what makes calculus possible. By the end of this chapter, you should be able to:

- *Define* the limit of a function intuitively and (in §2.6) precisely with $\epsilon$ and $\delta$.
- *Evaluate* limits using direct substitution, the limit laws, factoring, rationalization, and the squeeze theorem.
- *Distinguish* one-sided limits from two-sided limits, and infinite limits from limits at infinity.
- *Identify* points of discontinuity and classify them as removable, jump, or infinite.
- *Apply* the Intermediate Value Theorem to argue about the existence of solutions to equations.

You walk in with the function vocabulary from Chapter 1. You walk out with the foundational concept of calculus.

Why does this chapter matter? Because every concept that follows — the derivative, the integral, infinite series, continuity in higher dimensions — is defined in terms of a limit. If "limit" stays a fuzzy idea, every subsequent chapter is built on sand. The intuition develops in §2.2 and §2.3; the computational toolkit lands in §2.4; continuity and the IVT close the conceptual loop in §2.5; the precise $\epsilon$-$\delta$ definition that lets us *prove* limit statements waits in §2.6 for those who want the rigor.

## 2.2 The intuitive idea

Consider the function $f(x) = (x^2 - 4)/(x - 2)$. At $x = 2$, the formula collapses: numerator $0$, denominator $0$, undefined. The function has no value at $x = 2$. But what does $f(x)$ do as $x$ gets close to 2?

Compute. At $x = 1.9$, $f(1.9) = (3.61 - 4)/(-0.1) = (-0.39)/(-0.1) = 3.9$. At $x = 1.99$, $f(1.99) = 3.99$. At $x = 1.999$, $f(1.999) = 3.999$. From the right side: $x = 2.1$ gives $4.1$; $x = 2.01$ gives $4.01$; $x = 2.001$ gives $4.001$. From both sides, the function is converging on 4.

Algebraically, the reason is visible: $(x^2 - 4) = (x-2)(x+2)$, so $f(x) = (x+2)$ for $x \neq 2$. The function is identical to $x + 2$ everywhere except at $x = 2$, where the original formula's $(x-2)/(x-2)$ cancellation cannot legally happen because both pieces are zero. But for *any* $x$ near 2 but not equal to 2, the function reads $x + 2$, which approaches 4.

The *limit* of $f(x)$ as $x$ approaches 2 is 4. We write

$$\lim_{x \to 2} \frac{x^2 - 4}{x - 2} = 4$$

The function is undefined at $x = 2$. The limit exists anyway. Existence of a limit is a question about behavior *near* a point, not a question about value *at* a point.

The *intuitive definition*: the limit of $f(x)$ as $x$ approaches $a$ is $L$, written

$$\lim_{x \to a} f(x) = L$$

if $f(x)$ can be made arbitrarily close to $L$ by taking $x$ sufficiently close to $a$ (but not equal to $a$).

Three structural features of this definition matter.

*The value $f(a)$ is irrelevant.* The function might be undefined at $a$, defined and equal to $L$, or defined and equal to something else entirely. None of those affect the limit. The limit asks only about $x$ near $a$, not $x$ at $a$.

*Approach from both sides.* The limit exists only if $f(x)$ approaches the same value $L$ from the left ($x < a$) and from the right ($x > a$). If the two sides disagree, the two-sided limit does not exist.

*The limit might not exist at all.* The function might oscillate (like $\sin(1/x)$ near $x = 0$, which oscillates infinitely often as $x \to 0$). It might blow up to $\pm\infty$. It might approach different values from the two sides. In each case, the two-sided limit fails.

A worked example of all three. Consider

$$g(x) = \begin{cases} x + 1 & \text{if } x < 1 \\ 5 & \text{if } x = 1 \\ x + 2 & \text{if } x > 1 \end{cases}$$

What is $\lim_{x \to 1} g(x)$? Approach from the left: $g(x) = x + 1$, so $g(0.999) = 1.999$, approaching 2. Approach from the right: $g(x) = x + 2$, so $g(1.001) = 3.001$, approaching 3. The two sides disagree. The two-sided limit *does not exist*. The fact that $g(1) = 5$ is irrelevant. The function takes a value at $x = 1$; that value just happens to match neither one-sided limit.

The trade-off in the intuitive definition: it buys *immediate accessibility* (you can see what's going on by computing values close to $a$) at the cost of *precision* (it relies on the imprecise word "close"). The $\epsilon$-$\delta$ definition in §2.6 fixes this; it allows formal proofs at the cost of substantially heavier notation. The intuitive definition is what most calculus students reason with day-to-day; the formal one matters when something must be *proven* rather than computed.

## 2.3 One-sided limits, infinite limits, and the existence question

When the two sides of an approach disagree, the two-sided limit fails — but the one-sided limits may each exist. We write

$$\lim_{x \to a^-} f(x) = L_1$$

for the left-hand limit (approach from below), and

$$\lim_{x \to a^+} f(x) = L_2$$

for the right-hand limit (approach from above). The two-sided limit exists if and only if both one-sided limits exist *and are equal*.

For the piecewise $g(x)$ above: $\lim_{x \to 1^-} g(x) = 2$, $\lim_{x \to 1^+} g(x) = 3$. Each one-sided limit exists; the two-sided limit does not.

The *Heaviside step function* — $H(x) = 0$ for $x < 0$ and $H(x) = 1$ for $x \geq 0$ — is the canonical example. $\lim_{x \to 0^-} H(x) = 0$; $\lim_{x \to 0^+} H(x) = 1$. The two-sided limit at $x = 0$ does not exist. The function defines an instantaneous on/off switch at the origin.

*Infinite limits*. Sometimes a function grows without bound as $x$ approaches $a$. The textbook notation:

$$\lim_{x \to a} f(x) = \infty$$

means that $f(x)$ grows arbitrarily large as $x$ approaches $a$. Strictly speaking, the limit *does not exist* (the value $\infty$ is not a number). The notation is a useful shorthand for *how* the limit fails — by blowing up rather than by oscillating or by disagreeing across sides. Similarly $\lim_{x \to a} f(x) = -\infty$ for unbounded negative growth.

The Einstein equation from §2.1 is a perfect example. $\lim_{v \to c^-} m_0 / \sqrt{1 - v^2/c^2} = \infty$. The mass blows up as the speed approaches the speed of light from below.

*Limits at infinity*. The $x$ doesn't have to approach a finite value. We can ask what $f(x)$ does as $x$ grows without bound:

$$\lim_{x \to \infty} f(x) = L$$

means $f(x)$ approaches $L$ as $x$ grows arbitrarily large. For $f(x) = 1/x$, $\lim_{x \to \infty} 1/x = 0$. For $f(x) = (3x^2 + x)/(x^2 + 1)$, dividing numerator and denominator by $x^2$ gives $(3 + 1/x)/(1 + 1/x^2)$, which approaches $3/1 = 3$ as $x \to \infty$.

The four cases of "limit existence" worth keeping straight:

1. *Two-sided limit equals a finite number $L$.* Function approaches $L$ from both sides.
2. *Two-sided limit is $\pm\infty$.* Function blows up. By strict definition, the limit "does not exist," but the notation captures the way it fails.
3. *One-sided limits exist but disagree.* Two-sided limit does not exist; finite jump.
4. *Function oscillates* (like $\sin(1/x)$ near $0$). Neither one-sided nor two-sided limit exists.

The trade-off in this taxonomy: separating "limit doesn't exist" into named subtypes (jumps, blow-ups, oscillations) buys *diagnostic specificity* (a jump is a different problem from a blow-up) at the cost of *more terminology to keep straight*. Most calculus problems in practice fall into case 1; the others are useful for classifying the failures.

A worked example. Find $\lim_{x \to 0} \frac{|x|}{x}$.

For $x > 0$: $|x| = x$, so $|x|/x = 1$. Right-hand limit is 1.
For $x < 0$: $|x| = -x$, so $|x|/x = -1$. Left-hand limit is $-1$.

The two sides disagree. The two-sided limit does not exist. (The function is the *sign function*, with a jump discontinuity at the origin.)

## 2.4 Computing limits: the limit laws and the standard techniques

The intuitive definition is fine for understanding, but slow for computing. The *limit laws* let you decompose limits algebraically.

If $\lim_{x \to a} f(x) = L$ and $\lim_{x \to a} g(x) = M$, then:

1. $\lim_{x \to a} [f(x) + g(x)] = L + M$ (sum)
2. $\lim_{x \to a} [f(x) - g(x)] = L - M$ (difference)
3. $\lim_{x \to a} [f(x) \cdot g(x)] = L \cdot M$ (product)
4. $\lim_{x \to a} [f(x) / g(x)] = L/M$ provided $M \neq 0$ (quotient)
5. $\lim_{x \to a} [c f(x)] = cL$ for any constant $c$ (scalar)
6. $\lim_{x \to a} [f(x)]^n = L^n$ (power)
7. $\lim_{x \to a} c = c$ (constant)
8. $\lim_{x \to a} x = a$ (identity)

Combined, these laws say: limits commute with sums, differences, products, quotients (when the denominator's limit is nonzero), and integer powers. As long as nothing pathological happens, you can compute a complicated limit by computing simpler ones and combining.

The first thing to try, always: *direct substitution*. If $f(x)$ is a polynomial, a rational function whose denominator doesn't vanish at $a$, or any combination of standard functions that's defined at $a$, the limit equals $f(a)$. For example,

$$\lim_{x \to 3} (x^2 + 2x - 1) = 9 + 6 - 1 = 14$$

Direct substitution works. The function is *continuous* at $x = 3$ — a concept §2.5 will pin down formally.

Direct substitution fails when it produces an *indeterminate form* — most commonly $0/0$. The earlier example $\lim_{x \to 2} (x^2 - 4)/(x - 2)$ direct-substitutes to $0/0$, which gives no information. The technique to apply: *factor and cancel*. $(x^2 - 4)/(x-2) = (x-2)(x+2)/(x-2)$, and for $x \neq 2$ this equals $x + 2$. Now substitute: $\lim_{x \to 2} (x + 2) = 4$.

Three standard techniques handle most $0/0$ indeterminates.

*Factor and cancel*, as above. Usually the first move when the indeterminate involves polynomials.

*Multiply by a conjugate*. For limits involving radicals, multiplying numerator and denominator by the conjugate often clears the indeterminate. Example: $\lim_{x \to 0} (\sqrt{x+1} - 1)/x$. Direct substitution gives $0/0$. Multiply top and bottom by $\sqrt{x+1} + 1$:

$$\frac{\sqrt{x+1} - 1}{x} \cdot \frac{\sqrt{x+1} + 1}{\sqrt{x+1} + 1} = \frac{(x+1) - 1}{x(\sqrt{x+1}+1)} = \frac{x}{x(\sqrt{x+1}+1)} = \frac{1}{\sqrt{x+1}+1}$$

Now substitute: $\lim_{x \to 0} 1/(\sqrt{x+1}+1) = 1/(1+1) = 1/2$.

*The squeeze theorem*. If $g(x) \leq f(x) \leq h(x)$ near $a$, and $\lim_{x \to a} g(x) = \lim_{x \to a} h(x) = L$, then $\lim_{x \to a} f(x) = L$. The function is "squeezed" between two functions that both approach $L$. The classic application: $\lim_{x \to 0} x^2 \sin(1/x)$. The sine factor oscillates between $-1$ and $1$; the $x^2$ factor goes to 0. So $-x^2 \leq x^2 \sin(1/x) \leq x^2$, and both bounds approach 0 as $x \to 0$. The squeeze gives $\lim_{x \to 0} x^2 \sin(1/x) = 0$. Direct substitution would give "0 times an undefined value" — the squeeze theorem is the rigorous workaround.

The trade-off in the limit laws: they buy *systematic computability* (any standard limit can be evaluated by mechanical rules) at the cost of *not handling indeterminate forms directly* (when substitution gives 0/0 or $\infty/\infty$, you need additional algebraic manipulation). Most of a first-year calculus student's limit-evaluation practice is in recognizing which technique disposes of which indeterminate.

## 2.5 Continuity and the Intermediate Value Theorem

A function $f$ is *continuous at $a$* if three conditions hold:

1. $f(a)$ is defined.
2. $\lim_{x \to a} f(x)$ exists.
3. $\lim_{x \to a} f(x) = f(a)$.

In words: the function is defined at $a$, has a limit at $a$, and the limit equals the function value. All three pieces are required. Removing any one of them gives a *discontinuity*.

Three flavors of discontinuity:

*Removable discontinuity*. The limit exists, but $f(a)$ is undefined or doesn't match the limit. Example: $f(x) = (x^2 - 4)/(x - 2)$ from §2.2 has a removable discontinuity at $x = 2$. The limit is 4; the value is undefined. We could *redefine* $f(2) = 4$ and the new function would be continuous. The discontinuity is "removable" because patching the value fixes it.

*Jump discontinuity*. The one-sided limits exist but disagree. The Heaviside step function from §2.3 has a jump discontinuity at the origin. No redefinition of $f(0)$ can make the function continuous because the limits from the two sides land at different values.

*Infinite discontinuity*. The function blows up at $a$. Example: $f(x) = 1/x$ at $x = 0$. The function approaches $-\infty$ from the left and $+\infty$ from the right. Not patchable.

A function is *continuous on an interval* if it is continuous at every point of the interval. All polynomials are continuous everywhere. Rational functions are continuous everywhere except where the denominator vanishes. Trigonometric functions $\sin x$ and $\cos x$ are continuous everywhere; $\tan x$ is continuous except at the points where $\cos x = 0$ ($\pi/2 + k\pi$ for integer $k$). Exponential functions $b^x$ are continuous everywhere; logarithmic functions $\log_b x$ are continuous on $(0, \infty)$.

Continuity is the property that lets *direct substitution* compute limits. If $f$ is continuous at $a$, then $\lim_{x \to a} f(x) = f(a)$. The first move in any limit problem — substitute and see what happens — is asking implicitly whether the function is continuous at the target point.

The big theorem about continuity is the *Intermediate Value Theorem* (IVT): if $f$ is continuous on a closed interval $[a, b]$, and $N$ is any number between $f(a)$ and $f(b)$, then there exists at least one $c$ in $[a, b]$ with $f(c) = N$.

Stated geometrically: a continuous function whose graph crosses from one height to another must pass through every intermediate height somewhere. There can be no jumps. The IVT is the formalization of the intuitive idea that "you can't get from here to there without passing through the points in between" — provided your path is continuous.

A worked example. Show that $f(x) = x^3 - x - 1$ has a real root between $x = 1$ and $x = 2$.

$f(1) = 1 - 1 - 1 = -1$.
$f(2) = 8 - 2 - 1 = 5$.

$f$ is a polynomial, hence continuous on $[1, 2]$. The IVT applied to $N = 0$, which lies between $-1$ and $5$, guarantees that some $c$ in $[1, 2]$ has $f(c) = 0$. We don't know what $c$ is exactly, but we know it exists. Numerical methods (bisection, Newton's method) can locate $c$ to any desired precision; the IVT just guarantees it's there.

The trade-off in the IVT: it buys *existence proofs* (we can show solutions exist before we know how to find them) at the cost of *not telling us what the solution is*. The IVT is the most common tool for proving that an equation has a solution; algebra and numerical methods are then needed to find that solution.

A second consequence of continuity, useful for limits. If $f$ and $g$ are continuous at $a$, so is any polynomial combination of them — sums, products, quotients (where defined), compositions. This is what powers the limit laws of §2.4: when you decompose a complicated limit into simpler ones using the laws, you're implicitly using the fact that the operations preserve continuity for the standard families.

## 2.6 The precise $\epsilon$-$\delta$ definition

The intuitive definition of §2.2 is enough for most calculus practice. It is not enough for *proof*. Mathematicians spent the better part of two centuries — from Newton and Leibniz in the 1670s to Cauchy and Weierstrass in the 1820s and 1860s — getting to a definition rigorous enough to do mathematics with. The result is the $\epsilon$-$\delta$ ("epsilon-delta") definition.

*Definition*: $\lim_{x \to a} f(x) = L$ means that for every number $\epsilon > 0$, there exists a number $\delta > 0$ such that for all $x$ with $0 < |x - a| < \delta$, we have $|f(x) - L| < \epsilon$.

In words. Pick any tolerance $\epsilon$ on the output side — however small. The limit statement says we can find a tolerance $\delta$ on the input side such that whenever $x$ is within $\delta$ of $a$ (but not equal to $a$ — that's what the strict $0 < |x - a|$ inequality ensures), the function value $f(x)$ is within $\epsilon$ of $L$.

The structure is a quantifier challenge: for *every* $\epsilon$, there *exists* a $\delta$. To prove a limit equals $L$, you have to provide a recipe for finding a working $\delta$ given any $\epsilon$.

A worked $\epsilon$-$\delta$ proof. Show that $\lim_{x \to 3} (2x + 1) = 7$.

We need to show: for every $\epsilon > 0$, there exists $\delta > 0$ such that $0 < |x - 3| < \delta$ implies $|(2x + 1) - 7| < \epsilon$.

Simplify the conclusion: $|(2x + 1) - 7| = |2x - 6| = 2|x - 3|$.

So we need $2|x - 3| < \epsilon$, i.e., $|x - 3| < \epsilon/2$.

Choose $\delta = \epsilon/2$. Then if $0 < |x - 3| < \delta = \epsilon/2$, we have $|(2x+1) - 7| = 2|x - 3| < 2 \cdot \epsilon/2 = \epsilon$. ✓

The proof works for every $\epsilon$, with the explicit recipe $\delta = \epsilon/2$.

For more complicated functions the algebra gets harder, but the pattern is the same. Pick an arbitrary $\epsilon$. Manipulate the inequality $|f(x) - L| < \epsilon$ to express it as a constraint on $|x - a|$. Read off the $\delta$ that works.

The trade-off in the $\epsilon$-$\delta$ definition: it buys *mathematical rigor* (limit statements can now be proven, not just inferred) at the cost of *substantial notational and conceptual overhead*. Most introductory calculus courses introduce the definition for completeness and use it sparingly afterward. The intuitive definition does most of the day-to-day work. Real analysis — typically a year-three or year-four math course — develops the $\epsilon$-$\delta$ machinery in full.

## 2.7 Synthesis: closing the speed-of-light loop

Return to the Einstein equation from §2.1:

$$m(v) = \frac{m_0}{\sqrt{1 - v^2/c^2}}$$

Apply the chapter's full machinery. As $v \to c^-$ (approaching the speed of light from below), the denominator $\sqrt{1 - v^2/c^2}$ approaches $\sqrt{1 - 1} = 0$. The numerator $m_0$ is constant. The function blows up:

$$\lim_{v \to c^-} m(v) = \infty$$

This is an infinite one-sided limit — the limit does not exist in the strict sense, but the notation captures the way it fails: by unbounded growth.

The function is *not defined* at $v = c$ (denominator zero). It is also not defined for $v > c$ (the radicand becomes negative; we take the convention that real masses don't allow imaginary values). The natural domain is $-c < v < c$ — the function lives in the open interval between $-c$ and $c$, with infinite asymptotes at both endpoints. On the open domain, the function is continuous everywhere, since the denominator is positive throughout and the radical, division, and constant operations preserve continuity.

The Intermediate Value Theorem applies on any closed sub-interval: between $v = 0$ (where $m = m_0$) and $v = 0.99c$ (where $m \approx 7.1 m_0$), the function takes every intermediate mass value. There exists some $v$ between 0 and $0.99c$ at which the moving mass equals exactly $2 m_0$, $3 m_0$, $5 m_0$ — anything up to the upper bound. Numerical solution gives those $v$ values; the IVT just guarantees they exist.

Why does any of this matter beyond physics? Because the structural pattern recurs throughout calculus. A physical or geometric setup produces a function. Limits identify where the function is continuous, where it has asymptotes, where it has discontinuities. Continuity allows the IVT and direct substitution. Limit techniques handle the points where direct substitution fails.

The ground we've covered:

- Functions can be analyzed for their behavior near a point (the limit), independent of what they do at the point.
- Limits combine through limit laws when nothing pathological happens.
- Indeterminate forms (0/0, $\infty/\infty$) require algebraic manipulation — factoring, conjugates, the squeeze theorem.
- Continuity is the formal version of "no jumps, no holes, no blow-ups" — the property that lets direct substitution compute limits.
- The Intermediate Value Theorem turns continuity into existence proofs.
- The $\epsilon$-$\delta$ definition turns limit statements into provable assertions.

This is the foundational chapter of calculus. The derivative and the integral, both of which arrive in the next chapters, are themselves limits. Without the limit concept solid, neither makes sense.

## 2.8 Exercises

### Warm-up

1. **Use the intuitive definition to argue what** $\lim_{x \to 3} (x^2 - 9)/(x - 3)$ **should be.** Verify by factoring.

2. **For the function** $f(x) = |x|/x$, **state the left-hand limit, the right-hand limit, and the two-sided limit at** $x = 0$.

3. **State the three conditions a function must satisfy to be continuous at a point** $a$.

### Application

4. **Evaluate by direct substitution where possible; otherwise, apply factoring or conjugates:** (a) $\lim_{x \to 4} (x^2 + 2x - 1)$; (b) $\lim_{x \to 1} (x^2 - 1)/(x - 1)$; (c) $\lim_{x \to 0} (\sqrt{x + 4} - 2)/x$; (d) $\lim_{x \to 2} (x^3 - 8)/(x - 2)$.

5. **Apply the squeeze theorem to evaluate** $\lim_{x \to 0} x^2 \cos(1/x)$.

6. **Identify all points of discontinuity of** $f(x) = (x^2 - 1)/((x-1)(x+2))$, **and classify each as removable, jump, or infinite.**

### Synthesis

7. **Show using the IVT that** $f(x) = x^5 + 2x - 1$ **has a real root in the interval** $[0, 1]$.

8. **Compute** $\lim_{x \to \infty} (3x^2 + 2x + 1)/(x^2 - 4)$. **Then compute** $\lim_{x \to \infty} (3x + 2x + 1)/(x^2 - 4)$ (note the change in numerator's leading term). **Discuss why the two answers differ.**

### Challenge

9. **Use the** $\epsilon$**-**$\delta$ **definition to prove** $\lim_{x \to 2} (3x - 1) = 5$. **Provide an explicit** $\delta(\epsilon)$.

10. **Returning to Einstein's equation** $m = m_0 / \sqrt{1 - v^2/c^2}$, **find the speed** $v$ **at which the moving mass equals exactly** $10 m_0$. **Express the answer as a fraction of** $c$, **and compute it numerically.** Then discuss what the IVT lets us conclude about the existence of such a $v$ before we computed it.

## 2.9 Chapter summary

You walked into this chapter with functions but no formal way to talk about behavior near a point. You walk out with the foundational concept of calculus.

A *limit* is the value a function approaches as the input approaches a target — a question about behavior near a point, independent of what the function does at the point. Limits exist when the function approaches the same value from both sides. They fail in named ways: jumps (one-sided limits disagree), blow-ups (function grows without bound), oscillations (function doesn't settle on any value).

The *limit laws* let limits be computed by decomposition — sums, differences, products, quotients, powers. *Direct substitution* works when the function is continuous at the target. When substitution gives an indeterminate form (0/0, $\infty/\infty$), algebraic techniques — factoring, conjugates, the squeeze theorem — typically resolve it.

*Continuity* is the property that direct substitution computes a limit correctly: $\lim_{x \to a} f(x) = f(a)$, with $f$ defined at $a$ and the limit equal to the value. The standard families — polynomials, rational functions on their domains, trig functions, exponentials, logs — are all continuous on their natural domains.

The *Intermediate Value Theorem* turns continuity into an existence claim: a continuous function that crosses from one height to another must pass through every intermediate height somewhere. This is the most common tool for proving solutions exist.

The $\epsilon$-$\delta$ definition gives the precise version of "approaches" — for every output tolerance $\epsilon$, there exists an input tolerance $\delta$ such that inputs within $\delta$ of $a$ produce outputs within $\epsilon$ of $L$. Most calculus practice uses the intuitive definition; rigorous proof requires the formal one.

The single most important idea: calculus does not directly compute *values* of functions. It computes *limits* — what functions approach. Every later chapter is going to define an operation (differentiation, integration, summing infinite series) as a limit. If "limit" stays solid, the rest of the course follows.

The common mistake to watch for: confusing $\lim_{x \to a} f(x)$ with $f(a)$. They can be different — the function might be undefined at $a$, or defined and equal to something other than the limit, or defined and equal to the limit. Continuity is the special case where the limit and the value coincide. Most interesting limit problems involve points where they don't.

## 2.10 Connections forward

Chapter 3 introduces the *derivative* — the rate of change of a function at a point. The derivative is itself a limit:

$$f'(x) = \lim_{h \to 0} \frac{f(x + h) - f(x)}{h}$$

The expression $(f(x+h) - f(x))/h$ is the average rate of change of $f$ over an interval of width $h$. As $h$ shrinks to zero, the average rate becomes the *instantaneous* rate of change. The chapter you just finished — limits, indeterminate forms, the squeeze theorem, continuity — is precisely the toolkit needed to compute and reason about that limit. By the end of Chapter 3 you will have the derivative in hand for all the standard functions you met in Chapter 1, and a set of differentiation rules that let you handle compositions and combinations of them.
