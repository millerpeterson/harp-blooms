# harp-blooms

Live harp event extraction and processing in Max/MSP.

## Goal

Build a Max/MSP patch that listens to a live harp performance, detects individual notes in real time, and emits a stream of musical events that can drive other systems — visuals, generative music, lighting, or anything else.

The focus is **event extraction, not audio processing**: the harp's acoustic sound passes through unchanged. What the patch produces is a structured stream of note events with properties like pitch and loudness.

## Instrument & Setup

- **Harp:** Ogden lever harp
- **Mic:** Small diaphragm condenser mic

## Event Properties (planned)

- **Pitch** — which string/note was played
- **Loudness** — how hard the string was plucked (onset amplitude)
- More to come (duration, decay rate, etc.)

## Approach

Audio from the mic feeds into Max/MSP. The patch performs pitch detection and onset detection on the incoming signal to identify discrete note events, then routes those events (rather than the audio) to whatever downstream processing is connected.

### Pitch & Onset Detection Options (Max 9)

**Built-in (no install required):**
- `fzero~` — monophonic fundamental frequency estimator (wavelet-based). Three outlets: Hz, amplitude, onset bang. Best native option for sparse monophonic sources like harp. [Docs](https://docs.cycling74.com/reference/fzero~/)

**Third-party externals (free):**
- `sigmund~` — spectral pitch tracker, considered the stronger successor to `fiddle~`. Handles partial tracking and polyphony.
- `fiddle~` — older but robust pitch + amplitude tracker.
- `bonk~` — percussion/onset detection via bounded-Q spectral analysis. Good complement to pitch tracking.
- All three maintained by Volker Boehm (Mac Intel + Apple Silicon + Windows): https://vboehm.net/downloads/

**Package Manager (more advanced):**
- FluCoMa — research-grade toolkit with `fluid.pitch~` (YinFFT, returns pitch + confidence), `fluid.ampslice~` (amplitude onset), and `fluid.noveltyslice~`. Install via Max Package Manager. [Docs](https://learn.flucoma.org/reference/)

## Documentation & Community

- **Max 9 Reference Docs:** https://docs.cycling74.com/
- **Cycling '74 Forums:** https://cycling74.com/forums
