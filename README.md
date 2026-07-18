## Setup

```bash
python3 -m venv drake_env
source drake_env/bin/activate
pip install --upgrade pip
pip install drake underactuated notebook ipywidgets matplotlib numpy ipykernel
```

Select the `drake_env` kernel in VS Code / Jupyter before running any notebook.

## Exercises

### 1. First Drake System — Damped Pendulum (`drake_systems.ipynb`)

Implements the dynamics $\ddot\theta+\dot\theta+10\sin\theta=u$ as a Drake
`LeafSystem`, using position and velocity as state. Includes simulation,
time-domain plots, and a phase portrait showing convergence to the stable
equilibrium at the origin.

### 2. Attractivity vs Stability (`excerisice2-4.md`)

Analysis of the system

$$\dot x_1 = x_1(1-|\mathbf x|) + x_2\frac{x_1-|\mathbf x|}{2|\mathbf x|}, \quad
\dot x_2 = x_2(1-|\mathbf x|) - x_1\frac{x_1-|\mathbf x|}{2|\mathbf x|}$$

- Equilibria found at $(0,0)$ and $(1,0)$
- $(0,0)$ shown to be unstable
- $(1,0)$ shown to be **attractive but not stable i.s.L.**, using the
  radial rate $\dot r = r(1-r)$ and rotational rate
  $L = x_1\dot x_2 - x_2\dot x_1$
- Shown to be equivalent to the polar-coordinate system
  $\dot r=r(1-r),\ \dot\theta=\sin^2(\theta/2)$ from the textbook

Supporting simulation plots in `results/`.

### 3. Pendulum with Vibrating Base (`vibrating_pendulum.ipynb`)

Design of a feedback-cancellation controller that makes a pendulum, whose
base oscillates as $h\sin(\omega t)$, spin at constant angular velocity
$\dot\theta=1$ rad/s.

- **Part (a):** designs $f(q)=k(1-q)$, an exponentially stable target
  dynamics at $q=1$
- **Part (b):** derives the control law
  $u = ml^2k(1-\dot\theta) + mgl\sin\theta - ml\omega^2h\sin(\omega t)\cos\theta$
- **Part (c):** implements and simulates the closed-loop system; verifies
  $\dot\theta(t)$ is nondecreasing and converges to within $[0.99, 1.001]$
  rad/s by $t=10$s

## Notes

- Simulation/verification is primarily done in Deepnote (course-provided
  environment with pre-configured autograders); this repo mirrors that work
  locally for development and version control.
- The Gradescope autograder cells in some notebooks may fail locally due to
  a `mistune`/`gradescope_utils` dependency issue in the Deepnote environment
  — this does not affect the correctness of the implemented solutions, which
  are verified directly via simulation plots.
