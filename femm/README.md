# FEMM magnetostatic study of the LDR II motor

A 2D finite-element study of the driver's magnet system, used to put numbers on the motor-topology choices discussed in the main report. The aim is comparative, not absolute: how much force-producing field each topology delivers, measured against the same geometry.

## Method

- **Solver:** FEMM, 2D magnetostatic, modelling the motor cross-section (the section A plane of the assembly drawing).
- **Yoke:** 1018 low-carbon steel (real B-H curve; the yoke does not saturate, so grade is not critical).
- **Magnets:** three NdFeB bars, 50 x 10 x 5 mm at ~5 mm pitch, magnetised in alternating directions (N-S-N).
- **Magnetic gap:** 2.0 mm from the pole faces to the conductor plane (1.5 mm air plus the 0.5 mm FR board; FR laminate is non-magnetic, so it counts as air).
- **Front side:** no ferrous material in the baseline (the real front plate is aluminium); steel return structure is added only in the cage variants.
- **Boundary:** open circular region, mesh refined in the gap.
- **Measured quantity:** **B.t**, the in-plane (tangential) field component, taken along a line at the conductor plane. Only this component produces forward force on the conductor; the normal component (B.n) peaks over the bar centres and does no useful work, which is exactly where the original driver places its undriven dummy traces.

## Results

Peak in-plane field (B.t) at the conductor plane.

**Magnet grade (single-ended):**

| Grade | Peak B.t |
|---|---|
| N35 | ~0.38 T |
| N42 | ~0.41 T |
| N52 | ~0.46 T |

**Motor topology (all N35, same geometry):**

| Topology | Peak B.t |
|---|---|
| Push-pull (mirrored array, both sides) | ~0.65 T |
| Single-ended (the driver's actual design) | ~0.38 T |
| Partial steel cage | ~0.25 T |
| Full steel cage | ~0.18 T |

## What the numbers say

- **Grade is a modest lever.** N35 to N52 buys about 20%, which is just the remanence ratio. Worth having, not transformative.
- **Push-pull is the big lever.** Mirroring the array on the second face roughly doubles the field, and it also symmetrises the force across the diaphragm's travel (the linearity benefit that matters for a higher-excursion midrange, less so for a barely-moving tweeter).
- **A ferrous return *around* the array backfires.** More cage gives less useful field, monotonically (0.38 to 0.25 to 0.18 T). The steel offers the flux a low-reluctance loop that bypasses the gap entirely, so it behaves as a **keeper**: the field collapses into the iron instead of crossing the air where the conductor sits. The density plots show this directly, with flux hugging the steel and the gap region going pale.

The practical lesson: in this topology, field is won with **magnets, not iron**. A return path only helps if it routes flux *through* the gap; a full ferrous surround routes it *around* the gap and roughly halves the output. This validates the driver's actual design, an open, single-ended motor with a non-magnetic aluminium front, which sidesteps the keeper trap and provides ample field for a low-excursion tweeter. Push-pull is the only modification here that beats the open baseline.

## Caveat

This is a 2D model with an idealised conductor and geometry measured to roughly +/- 0.5 mm. The **trends and comparisons** are trustworthy; the absolute tesla values are not precise to a decimal. The study is built to be read comparatively, which is what it is used for.

## Files

Each topology has a B.t line plot (`*_btplot`), a flux-density plot (`*_field`), and the model geometry (`*_drawing`):

- single-ended baseline (also the N35/N42/N52 grade sweep)
- mirrored / push-pull
- partial cage
- full cage
