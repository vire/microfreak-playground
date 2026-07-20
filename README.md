# MicroFreak Field Guide

An interactive, self-contained HTML learning site built around the **Arturia MicroFreak** — from "what does this knob do" to writing your own music with it.

**File:** `public/index.html` — single file, no build step, no dependencies, no internet required. Open it in any modern browser.

The site is split into three tabs:

| Tab | What it is |
|-----|------------|
| **01 · MicroFreak** | The hardware: signal flow, the panel, patch recipes, tutorials, arp & seq masterclass |
| **02 · Playground** | A working Web Audio synth in the browser, plus experiments |
| **03 · Music theory** | A 20-lesson curriculum where every example plays through that synth |

---

## Tab 01 — MicroFreak

### Signal flow
A clickable diagram of the architecture: **digital oscillator → analog filter → amp/output**, with the modulators (envelopes, LFO, mod matrix, pressure) acting on every stage. The mental model the rest of the tab builds on.

### The panel, section by section
Eight cards covering every block of the hardware panel: digital oscillator, analog filter, envelope, cycling envelope, LFO, mod matrix, arp/seq + Spice & Dice, and the touch keyboard.

### Three patch recipes
Knob-by-knob settings (as clock positions, with visual knob dials) for **Pluck**, **Pad** and **Bass stab**. Each links into the playground so you can hear the target first.

### Tutorials (T-01 – T-07)
Seven hands-on exercises in increasing difficulty, each with steps and a "what to listen for" note:

| # | Tutorial | Focus |
|---|----------|-------|
| T-01 | Meet the engines | Oscillator types; Wave/Timbre/Shape as macro controls |
| T-02 | The filter is an instrument | Cutoff sweeps, resonance, filter types |
| T-03 | First matrix routing | LFO → Pitch (vibrato), LFO → Cutoff (breathing pad) |
| T-04 | Play with pressure | Aftertouch routings, Assign destinations |
| T-05 | Self-playing machine | Arp + Hold + Spice & Dice performance |
| T-06 | Build your own drum kit | Kick / snare / hi-hat (pitch-drop via Cycling Envelope) |
| T-07 | Drum pattern + bass | One-patch beats with mod lanes; DAW/looper overdub workflow |

### Arp & Seq — from 0 to 100
A seven-level masterclass, each level with exercises and a checkpoint: concepts and buttons → arp modes → time feel (rate, sync, swing, gate) → sequencer recording → the 4 modulation lanes → Spice & Dice as an instrument → Key/Arp as a modulation source.

---

## Tab 02 — Playground

A miniature synth built with the **Web Audio API**, mirroring the MicroFreak's signal flow: one oscillator → low-pass filter → ADSR envelope.

- Waveform selector (saw / square / triangle / sine)
- Sliders: Attack, Decay, Sustain, Release, Cutoff, Resonance
- Live envelope + filter-brightness visualization
- Touch-style keyboard playable by mouse, touch, or computer keys (`A`–`K` row); `Z`/`X` shift octave
- One-click presets: **Pluck**, **Pad**, **Bass stab**
- A "how it maps to the hardware" section that is explicit about what this toy *doesn't* model
- Five isolate-one-variable experiments (P-01 – P-05)

> Browsers require a user click before audio can start.

---

## Tab 03 — Music theory

Twenty lessons across five themes. Every lesson carries **playable examples** — buttons that sound intervals, scales, chords and progressions through the playground synth while lighting the notes on a 3-octave mini keyboard — plus a vocabulary block.

| Theme | Lessons |
|-------|---------|
| **1 · Foundations** | L-01 notes & semitones · L-02 intervals · L-03 rhythm · L-04 consonance & the harmonic series |
| **2 · Scales & keys** | L-05 major scale · L-06 minor scales · L-07 modes · L-08 pentatonic & blues · L-09 circle of fifths |
| **3 · Harmony** | L-10 triads · L-11 diatonic chords & Roman numerals · L-12 seventh chords · L-13 progressions · L-14 cadences |
| **4 · Line & voice** | L-15 voice leading · L-16 extended & altered chords · L-17 modal interchange · L-18 melody writing |
| **5 · Making music** | L-19 basslines · L-20 form & arrangement on the MicroFreak |

**239 playable examples** in total. Because they run through the playground's current patch, whatever voice you dial in on tab 02 is the voice your scales and chords speak with.

### Glossary
A searchable glossary of **110 terms** in nine categories — synth vocabulary (sound basics, oscillator, filter, envelopes, modulation, sequencing) and music theory vocabulary (pitch & scales, chords & harmony, rhythm & form) — written in plain language. Reachable from any tab.

---

## Tech notes

- **Single HTML file** — inline CSS and vanilla JS only, system fonts, no external requests (safe to open offline or host anywhere, e.g. GitHub Pages)
- **Web Audio API** for the synth (oscillator → biquad low-pass → gain envelope, plus a small filter envelope for punch and a compressor on the master bus). One `mkVoice`/`relVoice` pair serves both the live keyboard and the scheduled theory examples.
- Theory examples are encoded declaratively in a `data-play` attribute: space separates steps, `+` joins simultaneous notes, `-` is a rest. So `60+64+67 67+71+74` is two chords and `60 62 64` is a melody. Numbers are MIDI note numbers (60 = middle C).
- A `selfTest()` runs on load and logs to the console, checking that all 239 example note-lists parse to valid in-range MIDI — cheap insurance against a typo in hand-written data.
- Tabs are plain `hidden` toggles; anchor links (e.g. `#glossary`) resolve across tabs, so deep links keep working.
- Keyboard-accessible controls, visible focus states, `prefers-reduced-motion` respected
- Dark UI themed after the MicroFreak hardware panel (charcoal, orange knobs, OLED-style header)

## Accuracy caveat

Hardware sections are written against MicroFreak firmware ~4–5. A few menu details (gate-length location, per-step lane editing gestures) vary slightly between firmware versions — where the guide says "in Utility," trust the unit's own menus over the wording. Concepts are firmware-stable.

Music theory is presented as the common-practice Western tradition, which is a convention rather than a law. Where the guide states a rule (avoid parallel fifths, put chord tones on strong beats) it also says what the rule is protecting, so you can break it deliberately.

## Repo layout

```
microfreak-playground/
├── README.md          ← this file
└── public/
    └── index.html     ← the guide (single file)
```
