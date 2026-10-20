# Hyperframes Composition Brief: ghoLang

## Objective
Create a short launch-style brag video for ghoLang.

## Output
- Composition directory: `brag-output-2026-10-20-152424/composition/`
- Rendered video: `brag-output-2026-10-20-152424/brag.mp4`
- Format: landscape — 1920x1080
- Duration: 23.2s

## Source Material
- Project root: /Users/sarbagya/Desktop/clox
- Primary files read: README.md, closures.gho, other `.gho` samples, src/common.h, src/chunk.h, src/main.c; real runs of `./gho closures.gho` (opcode trace) and a `DEBUG_LOG_GC` build (allocate/free log)
- Product name: ghoLang (binary: `gho`, scripts: `.gho`)
- Tagline / strongest claim: "a small scripting language with a bytecode virtual machine written in C99"
- Key UI or visual moment to recreate: terminal running `closures.gho` (output 1, 2, 1) and the real opcode/stack trace and GC log
- Copy that must appear verbatim:
  - ghoLang
  - Bytecode VM. Written in C99.
  - single pass, no AST
  - DEBUG_TRACE_EXECUTION / DEBUG_LOG_GC

## Creative Direction
- Tone preset: default
- Creative direction: a language launch that treats a hobby VM with moonshot seriousness, terminal-native
- Interpretation: dry, short, real output carries it
- Angle: Nobody asked for another programming language; here it is anyway, and it takes out its own garbage.
- Hook: "Nobody asked for another programming language. Here it is anyway."
- Outro / punchline: "It takes out its own garbage."
- Avoid: generic SaaS language, abstract filler, any claim not in the project

## Visual Identity
- Background: #0b0e14
- Text: #e6e1cf
- Accent: #ffb454 (amber), #aad94c (green for program output)
- Display/body font: monospace stack (JetBrains Mono, SF Mono, Menlo)
- No CSS in the project; identity is the terminal.

## Storyboard
Use `brag-plan.md` as the contract.
1. Hook — 4.2s — typed hook line
2. Reveal — 4.2s — name slam, Bytecode VM / C99, pipeline stages on beats
3. Closures — 6.0s — closures.gho typed, run, 1 / 2 / 1
4. Guts — 4.7s — real opcode trace, then real GC log
5. Outro — 4.5s — name, joke, credit

## Audio
- Audio role: warm bed with sparse accents
- Music: happy-beats-business-moves-vol-9-by-ende-dot-app.mp3 (volume 0.32, fade in 0.3s, fade out 1.2s)
- Music cue guidance: bundled preset vol-9 (114.84 BPM). Locked: 4.23s, 8.44s-ish wipe, 19.48s. Beat-grid: 6.34/6.86/7.40/7.92, 12.12/12.65/13.18.
- Audio-reactive treatment: subtle; per-frame RMS of the track modulates the amber glow behind the name. No waveform visuals.
- Audio-coupled moments: keypress ticks on typed text; drops on pipeline stages and outputs; soft impact on both name slams; bell on the joke
- SFX: keyboard keypress, interface drop/click, impactSoft_medium_001, impactBell_heavy_000 (all CC0, copied into `composition/assets/sfx/`)

## Hyperframes Instructions
Built against the Hyperframes 0.8.174 CLI docs (data-attributes, compositions, gsap topics); domain skills were not installed. GSAP is vendored locally at `assets/gsap.min.js`. Gate: `npx hyperframes check` → 0 errors.
