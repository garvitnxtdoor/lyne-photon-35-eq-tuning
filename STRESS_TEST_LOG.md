# Driver Stress Test Log — Lyne Photon 35

Informal stress testing to find the actual physical limits of a ₹390 dynamic driver, since no manufacturer spec sheet or third-party measurement exists for this unit.

## Method

Pushed EQ bands to extreme values (within the ±15dB range available) one region at a time, at varying volumes, while listening for audible distortion/crackle/"breakup" — the audible signature of a driver's diaphragm exceeding its linear excursion range.

## Results

### Treble extreme (8kHz)
- **+15dB @ 8kHz, 70% volume** → clean, no distortion
- **+15dB @ 8kHz, 100% volume** → clean, no distortion (sounded unpleasant due to the EQ choice itself, not hardware failure)
- Conclusion: driver's voice coil/diaphragm has no issue reproducing the sibilance region even under extreme boost. Treble harshness in stock tuning is a tuning choice, not a hardware ceiling.

### Sub-bass extreme (31/62Hz)
- **+10/+9dB**, most tracks → held cleanly
- **+7/+6dB (Super W level)** → no issues across full test playlist except one track (below)

### The "Massive" anomaly
- Track: *Massive* — Drake
- Symptom: audible "crunchy/plastic" artifact during drum hits, present even at **0dB EQ (flat)** and at **both minimum and maximum playback volume** (volume-independence is the key diagnostic detail — true driver clipping gets worse with volume, this didn't)
- Cross-check: same artifact reproduced on a **second, unrelated earphone** (Samsung Galaxy Buds Pro 2) on the same track
- Conclusion: artifact is baked into the track's mix/master, not a driver fault. False positive — initially misattributed to EQ-induced clipping before the volume-independence and cross-device tests ruled that out.

### Control track (sub-bass heavy, for comparison)
- Track: *Flights Booked* — Gunna
- Result: held cleanly under the same Super W settings that "Massive" appeared to (falsely) struggle with — confirms the issue was track-specific, not a general sub-bass driver limitation

## Takeaway

This driver's actual hardware ceiling, within the ±15dB range tested, was not found. Every distortion-like symptom encountered traced back to either (a) source material characteristics, not EQ, or (b) subjectively unpleasant but not physically distorted audio at extreme settings. For a ₹390 unit this is a notably high tolerance — consistent with the theory that budget driver manufacturing (much of it sourced from a small number of shared Chinese OEM supply chains) has improved enough that "cheap = fragile" is no longer a safe assumption.

## Caveat

This is not a controlled test. No SPL meter, no THD measurement, no oscilloscope on the driver terminals — purely subjective listening for audible breakup. Treat as anecdotal, not as a rated spec.
