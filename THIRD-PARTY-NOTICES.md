# Third-party notices

## Yamaha OPL2 — synthesis model only

BLAST imitates the two-operator FM sound of Yamaha's OPL2. The tables are computed from the chip's published
mathematics, not copied from a ROM dump, and no Yamaha code, table, sample or firmware is included in this
repository.

Yamaha, OPL2 and SoundBlaster are named only to say what this machine was modelled after. BLAST is not affiliated
with, endorsed by or supported by Yamaha.

## Elektron

No Elektron firmware is included in this repository, original or modified, nor anything extracted from one — no
section, no dump, no copied routine. The machine is source code and a relocatable object; it is applied to a user's
own official `model-cycles_OS1.13.syx` by the host project's build.

Model:Cycles and Model:Samples are trademarks of Elektron Music Machines MAV AB. This project is independent and
not affiliated with, endorsed by or supported by Elektron.

## Tools this package is built with

| Component | Licence | How it is used |
|---|---|---|
| GNU m68k GCC and binutils | GPL | compiles and links `blast.o`; not distributed here |
| cycles-engines | MIT | the package format, composer and build; not distributed here |
