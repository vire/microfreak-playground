# MicroFreak Field Guide

An interactive, self-contained HTML learning site for the **Arturia MicroFreak** synthesizer — from "what does this knob do" to running the synth as a self-playing groove machine.

**File:** `microfreak-field-guide.html` — single file, no build step, no dependencies, no internet required. Open it in any modern browser.

## Contents

### 1. Signal flow
A clickable diagram of the MicroFreak's architecture: **digital oscillator → analog filter → amp/output**, with the modulators (envelopes, LFO, mod matrix, pressure) acting on every stage. This is the mental model the rest of the guide builds on.

### 2. The panel, section by section
Eight cards explaining every block of the hardware panel and how it affects the sound:

- Digital oscillator (Type, Wave, Timbre, Shape, Glide)
- Analog filter (Cutoff, Resonance, LPF/BPF/HPF)
- Envelope (ADSR, Filter Amt, Amp Mod)
- Cycling envelope (Env / Run / Loop modes)
- LFO (shapes, rate, sync)
- Mod matrix (sources → destinations)
- Arp/Seq + Spice & Dice
- Touch keyboard, pressure, paraphonic mode

### 3. Playground (makes real sound)
A miniature synth built with the **Web Audio API**, mirroring the MicroFreak's signal flow: one oscillator → low-pass filter → ADSR envelope.

- Waveform selector (saw / square / triangle / sine)
- Sliders: Attack, Decay, Sustain, Release, Cutoff, Resonance
- Live envelope + filter-brightness visualization
- Touch-style keyboard playable by mouse, touch, or computer keys (`A`–`K` row)
- One-click sound presets: **Pluck**, **Pad**, **Bass stab**

> Note: browsers require a user click before audio can start.

### 4. Three patch recipes
Knob-by-knob settings (given as clock positions, with visual knob dials) to build on the real hardware:

1. **Pluck** — zero sustain, short decay, snappy filter envelope
2. **Pad** — slow attack, paraphonic chords, LFO breathing via the matrix
3. **Bass stab** — instant attack, strong Filter Amt, optional acid variation with glide

Each recipe links into the playground so you can hear the target sound first.

### 5. Tutorials & examples (T-01 – T-07)
Seven hands-on exercises in increasing difficulty, each with steps and a "what to listen for" note:

| # | Tutorial | Focus |
|---|----------|-------|
| T-01 | Meet the engines | Oscillator types; Wave/Timbre/Shape as macro controls |
| T-02 | The filter is an instrument | Cutoff sweeps, resonance, filter types |
| T-03 | First matrix routing | LFO → Pitch (vibrato), LFO → Cutoff (breathing pad) |
| T-04 | Play with pressure | Aftertouch routings, Assign destinations |
| T-05 | Self-playing machine | Arp + Hold + Spice & Dice performance |
| T-06 | Build your own drum kit | Kick / snare / hi-hat sound design (pitch-drop trick via Cycling Envelope) |
| T-07 | Drum pattern + bass | One-patch beats with mod lanes; DAW/looper overdub workflow |

### 6. Arp & Seq — from 0 to 100
A seven-level masterclass on the arpeggiator and sequencer, each level with exercises and a checkpoint:

| Level | Topic |
|-------|-------|
| 0–15 | Concepts and the buttons (arp vs seq, A/B sequences, Hold/Tie/Rest) |
| 15–35 | Arp modes (Up / Order / Random / Pattern), octave range, live chord editing |
| 35–50 | Time feel: rate, sync, swing, gate length, external clock |
| 50–65 | Sequencer recording: step vs real-time, rests and ties, A/B switching |
| 65–80 | The 4 modulation lanes: per-step knob automation recipes |
| 80–90 | Spice & Dice as an instrument; structuring a live jam |
| 90–100 | Key/Arp as a modulation source; fully self-modulating patches |

### 7. Glossary
A searchable glossary of ~35 synth terms in six categories (sound basics, oscillator, filter, envelopes, modulation, playing & sequencing), written in plain language.

### 8. Mental model
The one-sentence summary the whole guide reduces to: *an oscillator makes a tone, a filter darkens it, an envelope shapes it in time, and modulation moves any of those automatically.*

## Tech notes

- **Single HTML file** — inline CSS and vanilla JS only, system fonts, no external requests (safe to open offline or host anywhere, e.g. GitHub Pages)
- **Web Audio API** for the playground synth (oscillator → biquad low-pass → gain envelope, plus a small filter envelope for punch and a compressor on the master bus)
- Keyboard-accessible controls, visible focus states, `prefers-reduced-motion` respected
- Dark UI themed after the MicroFreak hardware panel (charcoal, orange knobs, OLED-style header)

## Accuracy caveat

Written against MicroFreak firmware ~4–5. A few menu details (gate-length location, per-step lane editing gestures) vary slightly between firmware versions — where the guide says "in Utility," trust the unit's own menus over the wording. Concepts are firmware-stable.

## Suggested repo layout

```
microfreak-guide/
├── README.md                    ← this file
└── microfreak-field-guide.html  ← the guide
```
