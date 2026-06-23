# Raw measurements — Piega LDR II

REW log-swept-sine exports for two LDR II units ("blackdot" / "plain", per a
physical mark on the units). Measured pre-teardown, on the aged drivers.

| File | Unit | Data |
|---|---|---|
| `ldrii_blackdot_fr.txt`  | black-dot | Frequency response (SPL + phase), 1/24-oct smoothed |
| `ldrii_blackdot_thd.txt` | black-dot | Distortion (THD % + harmonics H2–H9) |
| `ldrii_plain_fr.txt`     | plain     | Frequency response (SPL + phase), unsmoothed |
| `ldrii_plain_thd.txt`    | plain     | Distortion (THD % + harmonics H2–H9) |

**Rig:** USB measurement microphone into a portable multitrack recorder,
handheld, uncalibrated. Quasi-anechoic gate 2 ms (≈ 500 Hz resolution floor).
Levels are relative, not calibrated SPL.

**Reading the data:** trust the flat-band shape and the in-band vs out-of-band
distortion contrast; treat data below ~1.5 kHz and fine ripple detail with
caution. The steep distortion rise below the ~3.5 kHz crossover is the expected
below-passband artifact (fundamental rolls off while harmonics stay in band),
not a driver fault. See the report for full interpretation.
