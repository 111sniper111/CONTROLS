# Excersice 2.4

## Part-1

### Equilibrium at (1,0)

![Equilibrium at (1,0)](results/(1,0).png)

### Equilibrium at (0,0)

![Perturbation near (1,0)](results/(0,0).png)

## Part 2 — Attractivity and Stability of the Equilibria

### Setting up the analysis: two invariant quantities


**Radial rate** — how fast the state moves toward/away from the origin:

$$\frac{1}{2}\frac{d}{dt}(x_1^2+x_2^2) = x_1\dot x_1 + x_2\dot x_2$$

Solving the given dynamics:

$$\dot r = r(1-r), \qquad r = |\mathbf x|$$

**Rotational rate** — how fast the state sweeps around the origin:

$$L = x_1\dot x_2 - x_2\dot x_1 = \frac{r(r-x_1)}{2}$$

Since $r \geq x_1$ always (the norm is never less than one component), $L \geq 0$
everywhere, with equality only when $x_2=0, x_1\geq0$.

### Equilibrium at (0,0): Unstable

From $\dot r = r(1-r)$, near $r=0$: $\dot r \approx r > 0$. Any nonzero
perturbation grows in magnitude — the state moves strictly *away* from the
origin. This is confirmed by simulation:

![Perturbation near origin](results/(0.05,0).png)

Starting from $\mathbf x(0) = [0.05, 0]$, the trajectory moves outward along
the $x_1$-axis toward the unit circle, visually confirming instability. The
background streamlines also show vectors diverging outward in every direction
around $(0,0)$ — the graphical signature of an unstable fixed point.

**Conclusion: $(0,0)$ is unstable** (fails even the weakest, i.s.L., definition).

### Equilibrium at (1,0): Attractive, but not stable i.s.L.

**Radially**, from $\dot r = r(1-r)$: for $r$ slightly below 1, $\dot r > 0$
(pulled up); for $r$ slightly above 1, $\dot r < 0$ (pulled down). So $r \to 1$
from any nonzero starting radius — the equilibrium is **radially attracting**.

**Angularly**, since $L \geq 0$ everywhere and $L=0$ only on the positive
$x_1$-axis, the state can *never* rotate clockwise, and stops rotating only
exactly at the equilibrium itself. This means a trajectory starting near
$(1,0)$ but off the $x_1$-axis (i.e., with $x_2 \neq 0$) is forced to keep
sweeping counterclockwise — it cannot simply sit near $(1,0)$; it must
travel most of the way around the unit circle before finally slowing its
rotation and returning close to $(1,0)$.

This means: for a small $\epsilon$-ball around $(1,0)$, a trajectory starting
inside that ball will *leave* the ball (traveling around the loop) before
eventually coming back — violating the definition of stability i.s.L., even
though the trajectory does converge to $(1,0)$ in the limit $t\to\infty$.

*(Note: the on-axis simulations below, with $x_2=0$, sit exactly on the
invariant line where $L=0$, so they show only the radial attraction and not
the rotational sweep — this is expected, since $x_2=0$ is a degenerate special
case of the dynamics.)*

![Trajectory toward (1,0) along the x1-axis](results/(0.9,0).png)

Starting from $\mathbf x(0) = [0.9, 0]$, the trajectory moves monotonically
along the $x_1$-axis toward $(1,0)$, confirming radial attraction. The
background streamlines show the spiral pattern converging toward $(1,0)$
from off-axis starting points, which is the graphical picture of the
attractive-but-unstable behavior described above.

**Conclusion: $(1,0)$ is attractive but not stable i.s.L.** — every
trajectory converges to it as $t\to\infty$, but nearby trajectories do not
remain close to it for all time, since they must first sweep around the
near-unit circle.

## Part-3 

The dynamical system is very close to the example 2.3 which says about 

**Unstable equilibrium point that attracts all trajectories**

where,
$$\dot r = r(1-r), \qquad \dot\theta=sin^2\left(\frac{\theta}{2}\right)$$

the given cartisiansystem is exactly this polar system, re-expressed using the stadard substitution 

$x_1 = r\cos\theta$,

 $x_2 = r\sin\theta$
 
### Derivation 

Starting from the polar-to-Cartesian relations, the chain rule gives:

$$\dot x_1 = \dot r\cos\theta - r\sin\theta\,\dot\theta, \qquad
\dot x_2 = \dot r\sin\theta + r\cos\theta\,\dot\theta$$

Inverting these (multiply the first by $\cos\theta$, the second by $\sin\theta$,
and add; then similarly for $\dot\theta$):

$$\dot r = \cos\theta\,\dot x_1 + \sin\theta\,\dot x_2, \qquad
r\dot\theta = -\sin\theta\,\dot x_1 + \cos\theta\,\dot x_2$$

**Computing $\dot r$:** substitute the given Cartesian dynamics into the first
expression:

$$\dot r = (1-r)(x_1\cos\theta + x_2\sin\theta) + \frac{x_1-r}{2r}(x_2\cos\theta - x_1\sin\theta)$$

Using $x_1=r\cos\theta,\ x_2=r\sin\theta$:

$$x_1\cos\theta+x_2\sin\theta = r\cos^2\theta+r\sin^2\theta = r$$
$$x_2\cos\theta-x_1\sin\theta = r\sin\theta\cos\theta - r\cos\theta\sin\theta = 0$$

So the second term vanishes entirely, leaving:

$$\dot r = (1-r)\cdot r = r(1-r)$$

**Computing $\dot\theta$:** substitute into the second expression:

$$r\dot\theta = (1-r)(-x_1\sin\theta+x_2\cos\theta) - \frac{x_1-r}{2r}(x_2\sin\theta+x_1\cos\theta)$$

Again using $x_1=r\cos\theta,\ x_2=r\sin\theta$:

$$-x_1\sin\theta+x_2\cos\theta = -r\cos\theta\sin\theta+r\sin\theta\cos\theta = 0$$
$$x_2\sin\theta+x_1\cos\theta = r\sin^2\theta+r\cos^2\theta = r$$

So the first term vanishes, leaving:

$$r\dot\theta = -\frac{x_1-r}{2r}\cdot r = \frac{r-x_1}{2} = \frac{r - r\cos\theta}{2}$$

$$\dot\theta = \frac{1-\cos\theta}{2}$$

Using the half-angle identity $\sin^2(\theta/2) = \dfrac{1-\cos\theta}{2}$:

$$\dot\theta = \sin^2\left(\frac{\theta}{2}\right)$$

### Conclusion

This confirms $\dot r = r(1-r)$ and $\dot\theta = \sin^2(\theta/2)$ exactly —
the given Cartesian system **is** the polar-coordinate example from the
chapter, just written out in $x_1,x_2$ instead of $r,\theta$. This also
explains why our earlier direct-Cartesian analysis (computing $\dot r$ via
$x_1\dot x_1+x_2\dot x_2$ and the rotational quantity $L$) reproduced the
same $\dot r=r(1-r)$ relationship without ever performing the substitution —
it's the same underlying dynamics viewed two different ways.


