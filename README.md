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
