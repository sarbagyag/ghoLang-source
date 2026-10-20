# Brag Plan: ghoLang

## What is this app?
ghoLang is a small scripting language with a single-pass compiler and a stack-based bytecode VM, written in C99 (binary still named `clox`), built chapter by chapter from *Crafting Interpreters* and now done through Garbage Collection.

## The angle
Nobody asked for another programming language, so the video plays that straight: a hobby language launched with the confidence of a platform. The real UI is the terminal. Real closure output (`1 2 1`), real bytecode trace, real GC log. The punchline is the GC chapter: it takes out its own garbage.

## Hook (first 2-3 seconds)
Terminal-dark frame. Typed line: "Nobody asked for / another programming language." Then, beat-snapped: "Here it is anyway."

## Key moments (the middle)
- Name slam "ghoLang" + "Bytecode VM. Written in C99." and the pipeline lighting up one stage per beat: Scanner → Compiler → Bytecode → VM (README: "single-pass compiler into bytecode, which a stack-based VM then executes").
- Closures: `makeCounter` typed from `closures.zb`, run, output `1 2 1` (two counters, two private counts).
- VM guts: the real `DEBUG_TRACE_EXECUTION` stack/opcode trace (`OP_GET_UPVALUE`, `[ <script> ][ <fn get> ][ updated ]`), then the real `DEBUG_LOG_GC` allocate/free log.

## Outro / punchline
`ghoLang` — "It takes out its own garbage." Small credit: "Lox, from Crafting Interpreters · Done through chapter 26".

## User flow worth showing
Entry: `make` then `./clox closures.zb` → key action: the script defines `makeCounter` and calls two counters → result: `1`, `2`, `1` printed. Then the same run seen from the inside: bytecode trace and GC log.

## Tone
- Preset: default (leaning deadpan-dev)
- Creative direction: a language launch that treats a hobby VM with moonshot seriousness, terminal-native, one dry joke
- Interpretation: Mixed-case, warm but dry copy; real code and real VM output carry the video; one joke in the hook, one in the outro; no hype words.

## Format: landscape — 1920x1080
## Duration: ~23s

## Visual identity (from the project)
No web UI or CSS exists, so the identity is the terminal.
- Background: #0b0e14 (terminal ink)
- Accent: #ffb454 (amber, prompt/cursor/opcodes)
- Secondary accent: #aad94c (green, program output)
- Text: #e6e1cf
- Display font: monospace (Menlo / ui-monospace stack), bold for the name
- Body font: same monospace
- Strongest visual element: the real terminal output — opcode trace with stack brackets

## Share copy (draft)
Made a programming language: ghoLang, a bytecode VM in C99, done through the garbage collection chapter. It takes out its own garbage.

## Audio direction
- Role: warm bed with sparse accents
- Music: happy-beats-business-moves-vol-9 (mid-energy, 114.84 BPM)
- Music treatment: starts at 0 under the typing hook at ~0.30 volume, fades out over the final 1.2s
- Music cue guidance: preset `assets/music/cues/happy-beats-business-moves-vol-9-by-ende-dot-app.music-cues.md`. Strong cues to lock: 4.23s (name slam), 8.44s (closures scene), 19.48s outro slam (nearest beat). Beat grid for sequential items: 6.34, 6.86, 7.40, 7.92 (pipeline chips); 12.12, 12.65, 13.18 (outputs 1, 2, 1).
- Audio-reactive treatment: subtle; RMS makes the amber glow behind the name and cursor breathe. No waveform/equalizer visuals.
- SFX posture: sparse, motion-matched
- Audio-coupled moments: hook typed with keypress ticks; pipeline chips tick on beats; code typing in the closures scene; name slam with a soft impact; outro bell.
- Restraint rule: no SFX over dense trace scene beyond one accent; never above music energy.

## Storyboard

### Scene 1 — Hook — 3.7s
Black terminal frame, blinking cursor. Large text types: "Nobody asked for" / "another programming language." (hold ≥1.5s settled), then "Here it is anyway." at the 3.18 beat.
Sequential/interaction: yes — typed text, character by character
Audio intent: dry, curious
Audio-coupled idea: keypress ticks while typing
Music: bed fades in
Transition mood: hard cut → Scene 2

### Scene 2 — Reveal — 4.74s
"ghoLang" slams in at 4.23s (strong cue). Subtitle "Bytecode VM. Written in C99." Then a pipeline: Scanner → Compiler → Bytecode → VM, one stage per beat (6.34, 6.86, 7.40, 7.92), final state held ≥0.5s.
Sequential/interaction: yes — 4 pipeline stages light up one by one
Audio intent: confident
Audio-coupled idea: soft impact on slam; drop ticks on stages
Transition mood: clean wipe → Scene 3

### Scene 3 — Closures — 5.78s
Terminal split. Left: `closures.zb` makeCounter code types in. Run line `$ ./clox closures.zb`. Right: output `1`, `2`, `1` at 12.12, 12.65, 13.18. Caption: "Two counters. Two private counts."
Sequential/interaction: yes — code typed, then three outputs on consecutive beats
Audio intent: satisfying
Audio-coupled idea: keypress ticks, click on run, drop on each output
Transition mood: hard cut → Scene 4

### Scene 4 — Guts — 4.74s
Real trace scrolls (`OP_GET_UPVALUE`, `OP_CLOSURE`, stack brackets). Label "DEBUG_TRACE_EXECUTION". Then GC log (`allocate 40 for type 3` … `free type 3`) with label "DEBUG_LOG_GC" and caption "Mark-sweep garbage collection."
Sequential/interaction: yes — log lines streaming
Audio intent: busy, technical
Transition mood: crossfade → Scene 5

### Scene 5 — Outro — 4.24s
"ghoLang" at 19.48s. "It takes out its own garbage." Small credit: "Lox, from Crafting Interpreters · Done through chapter 26".
Sequential/interaction: none
Audio intent: land the joke, warm resolve
Audio-coupled idea: outro bell, music fade-out
Transition mood: fade to black

**Music mood for this video:** upbeat, restrained
**Audio summary:** a quiet-ish bed under typing, a soft impact on the name, steady ticks through the demo, one bell on the joke, fade out.

Scene durations: 3.7 + 4.74 + 5.78 + 4.74 + 4.24 = 23.2s
