# BLAST — fourteen OPL2-style FM models for the Model:Cycles

BLAST is one added machine for the **Elektron Model:Cycles**, OS 1.13: fourteen melodic FM models built on a
two-operator FM engine in the manner of the Yamaha OPL2. A '90s PC SoundBlaster engine, with a stepped modulator
ratio on SWEEP.

This repository is the machine's **source package**, published so that other projects can port it. It is not a
firmware and contains none.

**Hear it:** [BLAST on YouTube](https://www.youtube.com/watch?v=cPBxAeiMe9A)  
**Flasher:** [100demons.github.io/cycles-engines/flasher](https://100demons.github.io/cycles-engines/flasher/) —
tick BLAST and bring your own official `model-cycles_OS1.13.syx`.

## The models

SHAPE picks the model. The names are shown on the machine's screen.

| SHAPE | Model | What it is |
|---:|---|---|
| 0 | SIN | Sine: clean two-operator FM, modulator depth on COLOR |
| 1 | HLF | Half-sine: hollow, reedy carrier |
| 2 | ABS | Absolute sine: folded wave, octave-rich and bright |
| 3 | PLS | Pulse: nasal, square-edged carrier |
| 4 | BAS | Bass: short FM slap over a round body |
| 5 | PIA | Piano: bright bark settling into a round tone |
| 6 | MAR | Marimba: fundamental plus tuned overtone, mallet click |
| 7 | GLK | Glockenspiel: bright strike with a quiet high partial |
| 8 | BRS | Brass: slow swell into a sustained brass |
| 9 | ACC | Accordion: two detuned half-sine reeds |
| 10 | STR | Strings: feedback saw modulator with a bowed attack |
| 11 | STL | Steel drum: hollow ring with a semitone blip |
| 12 | TMP | Timpani: felt thud and a long low membrane |
| 13 | ZAP | Laser: four-octave pitch fall |

## The knobs

| Knob | What it does |
|---|---|
| PITCH / FINE | the note, as on every machine |
| COLOR | Index: the FM modulation index / modulator level, the mallet hardness or the feedback |
| SHAPE | the model (the table above) |
| SWEEP | the fixed modulator:carrier ratio, 1:2 to 15X, stepped; FUNC leaves the steps |
| CONTOUR | Env: how the sound moves (brightness decay, swell, feedback, detune, mallet click) |
| DECAY | the decay, or release when GATE holds the note |
| GATE | BRS, ACC and STR sustain; PIA, MAR, GLK and STL delay the damper so long notes ring |
| PUNCH | vibrato on SIN, HLF, ABS, PLS, MAR, BRS and STR; tremolo on BAS, PIA, GLK and STL; ACC gets both; TMP and ZAP ignore it |

## Status

| | |
|---|---|
| Package | `cycles-mod/0.1`, the model27/cycles-engines package format |
| Slot in the flasher | 9 (the OS numbers it machine 8) |
| Committed object | `blast.o`; `core/build_engine.py blast --check` passes |
| Emulated | the source tree's bridge proof (all 14 models, GATE, silence, cost, memory, stack) and OS proof (boot, descriptors, names, ratios, voice loop) passed |
| Tested on a real Model:Cycles | **not yet** |
| Weight | about 60 to 84 % of a stock TONE voice per block; a silent voice costs almost nothing |
| License | MIT |

BLAST makes its own envelopes; the stock amp chain is not called. A silent voice is not computed. The OS still
sets the volume and applies velocity after the voice.

## Package layout

```
tools/machines/blast/
  manifest.json    the package: build recipe, symbols, claims, tests, compatibility
  card.json        the flasher card: label, description, status, video
  blast.c          the voice-loop bridge
  blast_dsp.h      the FM engine (two operators, OPL2-style log-sine and power tables)
  blast_tables.h   the generated tables
  blast_icons.h    the splash artwork (the package still shows TONE's stock MACHINES picture)
  blast.o          the committed relocatable object
  LICENSE          MIT
```

There is no firmware here: the package is applied to the user's own official OS file by a host such as
[cycles-engines](https://github.com/100demons/cycles-engines).

## Build and check the object

The package builds with the **cycles-engines** toolchain. Copy `tools/machines/blast/` into a cycles-engines
checkout as `engines/blast/`, then:

```sh
export M68K_CROSS=/path/to/bin/m68k-elf-        # or have m68k-elf-gcc on PATH
python3 core/build_engine.py blast --check
```

`--check` rebuilds `blast.o` from `blast.c` and the manifest's recipe and compares it with the committed object.
The composer and the flasher never need the toolchain: they place the committed object.

## Install

Easiest: tick **BLAST** in the [flasher](https://100demons.github.io/cycles-engines/flasher/) and bring your own
official OS 1.13 file. Or download `blast-3.0.zip` from this repository's Releases and add the folder to your own
build.

## Credits

- Engine, tables and design: **100demons**, MIT.
- The OPL2 is named as the synthesis model; no Yamaha code, ROM dump or sample is included. See
  [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md).

## Changelog

See [CHANGELOG.md](CHANGELOG.md).
