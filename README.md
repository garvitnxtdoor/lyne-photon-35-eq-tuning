# lyne-photon-35-eq-tuning
# Budget Earphone EQ Tuning — Lyne Photon 35

Ear-derived parametric EQ tuning, driver stress-testing, and signal chain analysis on a ₹390 wired Type-C earphone, benchmarked conceptually against the Harman target curve.

No measurement rig. No squig.link data for this unit (it doesn't exist — Lyne Photon 35 has zero public frequency response measurements). Just critical listening, a 10-band ±15dB graphic EQ, a stress-test playlist, and a few hours of iteration.

## Why this exists

Most budget earphone "reviews" are subjective one-liners ("bass is good", "treble is sharp"). There's no public data on how budget Indian earphones actually behave under EQ stress, where their drivers clip, or whether aggressive correction curves are even usable on them. This repo documents that process for one specific unit, with the methodology made explicit so it's repeatable on other budget gear.

## Hardware

- **Earphone:** Lyne Photon 35, wired, USB-C, dynamic driver, silicone tips (stock, medium)
- **Source:** Samsung Galaxy A22, Dimensity 700, USB-C output (no onboard DAC in the earphone — relies entirely on phone's audio output stage)
- **EQ:** Stock Android system equalizer, 10-band graphic EQ, ±15dB range per band, plus Bass Boost / Loudness / Virtualizer toggles

## Stock signature

Identified by ear, consistent with typical budget V-shape tuning:
- Elevated sub/mid-bass
- Recessed mids (vocals sit back in the mix)
- Elevated treble, prone to harshness around 8kHz

## The tuning: "Super W"

A W-shaped correction curve — not a flat/reference tune, but a deliberately more aggressive correction than Harman target, on the reasoning that **a driver with larger inherent frequency response errors needs proportionally larger correction** than a reference-grade driver (which Harman's listening tests were largely conducted on).

| Band | Setting | Purpose |
|------|---------|---------|
| 31 Hz | +7.0 | Sub-bass rumble |
| 62 Hz | +6.0 | Kick/bass punch |
| 125 Hz | -5.0 | Removes mud/boom |
| 250 Hz | -4.0 | Removes boxiness |
| 500 Hz | +3.0 | Warmth/body |
| 1 kHz | +5.0 | Vocal presence (corrects recession) |
| 2 kHz | +5.0 | Instrument clarity/separation |
| 4 kHz | +4.0 | Attack/definition |
| 8 kHz | -6.0 | Kills sibilance/harshness |
| 16 kHz | +7.0 | Air/openness |

Full values and a Harman-target comparison curve are in [`eq-profiles/`](./eq-profiles).

### Why more aggressive than Harman

Harman target was derived from preference testing largely using accurate reference headphones. A driver with significant inherent frequency response error (recessed mids, V-shape skew) doesn't reach a balanced *perceived* result from a gentle, reference-grade correction curve — the underlying error is too large. Super W intentionally over-corrects in the direction the stock tuning is weak (mids, controlled treble) to compensate for the driver's actual measured-by-ear deficiencies, rather than applying a correction calibrated for a driver that doesn't have those deficiencies in the first place.

A milder, closer-to-Harman variant is included in the profiles folder for comparison — it's more "correct" in the reference sense but noticeably less balanced-sounding on *this specific driver*.

## Driver stress testing

Tested the driver against deliberately bass/treble-extreme settings and known difficult tracks to find actual hardware limits (not just EQ-app limits).

| Test | Setting | Result |
|------|---------|--------|
| +15dB @ 8kHz, 70% volume | Sibilance torture test | No crackle/distortion |
| +15dB @ 8kHz, 100% volume | Max volume torture test | No crackle (sounded bad, but didn't physically distort) |
| +10/+9dB @ 31/62Hz | Sub-bass stress | Held on most tracks |
| "Massive" — Drake | Reference bass-heavy track | Crunch/distortion artifact present **at every EQ setting, including flat/stock, and on a second unrelated earphone (Samsung Buds Pro 2)** — confirmed to be baked into the track's production, not driver clipping |
| "Flights Booked" — Gunna | Sub-heavy stress track | Held cleanly |

Methodology note: the "Massive" result is the more interesting finding here — initial assumption was driver clipping, but the artifact's volume-independence (constant at both min and max volume) and reproduction on a completely different driver ruled that out. Logged here so nobody else burns time on the same false lead.

## Signal chain notes

- Earphone has no internal DAC — audio path is phone analog/USB-C output → driver, directly.
- USB-C analog audio output on the A22 is lower-powered than its 3.5mm output (dedicated headphone amp circuits on 3.5mm vs. shared/simpler analog path on USB-C audio). Irrelevant for this specific low-impedance passive driver, but relevant if/when moving to higher-impedance gear.
- Audible hiss (DAC noise floor) present only in silence, masked completely once audio plays. Normal behavior for phone-driven passive earphones, not a defect.

## Listening volume / safety note

All tuning and testing done at low absolute volume (~15-20% of device max). Aggressive EQ values here are *relative* boosts/cuts, not an endorsement of high listening volumes — this matters more for hearing safety than the EQ curve itself.

## Future work

- [ ] Apply same methodology to a measured IEM (e.g. KZ EDX Pro) using squig.link data as ground truth, compare ear-derived curve against AutoEQ-generated curve for the same target
- [ ] Document cable/connector failure point if/when the Type-C cable fails (mechanical vs. driver longevity)
- [ ] Possible tie-in with [sleep-monitoring ESP32 project] for a bed-side audio environment build

## Disclaimer

This is ear-tuning, not measurement. No frequency response graph exists for this exact unit. Every value here is the output of subjective critical listening, cross-checked against multiple genres and a few deliberately difficult test tracks, not a calibrated microphone. Treat the curve as a documented starting point, not lab data.
