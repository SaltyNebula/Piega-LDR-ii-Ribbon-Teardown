# Measurements & Specifications

Bench data for the driver. Electrical values were confirmed during disassembly; the pre-teardown acoustic sweeps (frequency response and distortion, both units) are included in `raw/` and summarised under "Acoustic measurements" below.

## Provenance / host speaker

| Parameter | Value | Source |
|---|---|---|
| Driver | Piega LDR II (Linear Drive Ribbon, gen II) ribbon tweeter | Manufacturer designation |
| Host speaker | Piega P 4 XL MK II | Identified from purchase |
| Speaker type | 3-way bass-reflex floorstander (2× 130 mm LDB bass + LDR II tweeter) | Published spec |
| Era | Early 2000s (base P 4 XL: 1997 to 1999; MK II reviewed by 2002) | Published spec |
| Rated sensitivity | **89 dB** (whole speaker) | Published spec |
| Rated impedance | 4 Ω (whole speaker) | Published spec |
| Tweeter crossover | ~3.5 kHz | Published spec for the same 26 × 45 mm LDR II-S ribbon (sister model) |
| Acquired | Second-hand via Ricardo | |

> The 89 dB rated sensitivity supports the in-use observation that the driver played audibly quiet: a healthy unit should sit near that figure, so the reduced output is consistent with field/BL loss from magnet corrosion, not a low-sensitivity design.

## Electrical

| Parameter | Value | Notes |
|---|---|---|
| Terminal DC resistance | 2.8 Ω | Confirmed at external terminals and directly at diaphragm pads |
| Bridged-pair resistance | ~0.1 Ω | Meter floor; indicates commoned (parallel) spiral ends |
| Coil topology | Two concentric rectangular spirals, in parallel | |
| Drive | Direct-coupled (no matching transformer) | |

## Diaphragm

| Parameter | Value |
|---|---|
| Substrate | Kapton (polyimide), yellow/amber |
| Conductor | Etched aluminium, conductor-side outward |
| Conductor thickness / moving mass | ~7 µm / ~7 mg (Piega published figures, consistent with sample) |
| Active radiating area | 25.8 × 41.8 mm |
| Full patterned footprint | ~81 × 41 mm (remainder is bus routing) |
| Pleating | Fine transverse corrugation, ~4 corrugated : 1 flat, repeating |
| Dummy (unwired) strips | ~8, centred over the middle magnet |

## Magnet system

| Parameter | Value |
|---|---|
| Magnet type | Neodymium (NdFeB) bar magnets, ×3 |
| Dimensions (each) | ~50 × 10 × 5 mm |
| Spacing | ~5 mm between bars |
| Polarity | Alternating N-S-N (ferrite attraction/repulsion test) |
| Rear yoke | Soft-steel plate, common return path, ~5 mm |
| Configuration | Single-ended (magnets on one side only) |

## Mechanical stack (front to back)

| Layer | Material | Dimension |
|---|---|---|
| Front plate | Steel, windowed | 2 mm; opening ≈ 25.8 × 41.8 mm |
| Spacer / gasket | Hard rubber | ~1.6 mm (sets air gap) |
| Diaphragm | Aluminised Kapton on fibreboard frame | |
| Air gap | | ~1.6 mm to magnet faces |
| Magnets + yoke | NdFeB bars + steel yoke | ~5 mm + ~5 mm |
| Damping | Felt (between bars, behind yoke); cork-like filler above/below bars | thin |
| Frame | Translucent fibreboard, FR-type (glass-fibre/epoxy) laminate | |
| Adhesive joints | Only two: magnet-to-yoke, Kapton-to-frame | |

## Acoustic measurements

Pre-teardown sweeps of both units (REW log-swept-sine). Raw files in `raw/`; plots in `figures/`. See the report (Section 9) for full interpretation.

| Metric | Value | Notes |
|---|---|---|
| Natural roll-off knee (minus 3 dB) | ~2.7 kHz | Both units (plain ~2672 Hz, black-dot ~2709 Hz) |
| Usable passband | ~3 kHz to 20 kHz | Flat, with ribbon ripple |
| Crossover vs knee | 3.5 kHz sits ~1/3 octave above the knee | Textbook tweeter integration |
| In-band THD (≥ 3.5 kHz) | median ~0.2 to 0.4 % | Plain ~0.22 %, black-dot ~0.38 %; peaks ~1 to 2 % |
| Below-crossover THD (< 1.5 kHz) | ~45 to 170 % | Out-of-band artifact, not a fault (see below) |
| Unit-to-unit match (in band) | Near-identical | Two ~20-year-old samples track closely above 3.5 kHz |
| Shared notch | ~1.2 kHz | Present in both units, below passband |

**Reading the distortion data.** Below the ~3.5 kHz crossover the driver cannot radiate the fundamental, while that tone's harmonics land back up in the efficient band, so the harmonics-to-fundamental ratio (THD %) explodes. This is the normal below-passband artifact, it is filtered out in the speaker, and it is *not* a sign of a fault. In the real passband the driver is clean.

## Measurement caveats

- Acoustic rig: USB measurement microphone into a portable recorder, handheld, uncalibrated, 2 ms quasi-anechoic gate (≈ 500 Hz resolution floor). Trust the flat-band shape and the in-band vs out-of-band contrast; treat data below ~1.5 kHz and fine ripple detail with caution.
- Levels are relative, not calibrated SPL, so the sensitivity loss does not appear directly in the sweeps.
- In-band harmonic *breakdown* is noise-floor-limited and should not be read as a clean even/odd-order signature.
- Linear dimensions taken with a non-digital caliper; treat as approximate (±~0.5 mm).
- Sub-ohm readings are at the meter's resolution floor; lead/contact resistance was not nulled, so "~0.1 Ω" means "indistinguishable from a short," not a precise value.
- Conductor thickness and moving mass are manufacturer figures, not independently measured.
