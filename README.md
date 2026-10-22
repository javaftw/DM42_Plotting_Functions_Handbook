# Plotting Functions on the DM42

A self-contained handbook for programming Cartesian, parametric, polar, implicit, fractal and 3-D plots on the SwissMicros DM42.

Current release: **v0.51**

[Download the compiled handbook](dist/DM42_Plotting_Functions_Handbook.pdf)

## About the handbook

*Plotting Functions on the DM42* develops a reusable graphics toolkit for the calculator's 400×240 monochrome display. It begins with a single pixel and builds toward complete plotting systems for:

- Cartesian functions
- parametric curves
- polar curves
- implicit curves, fields and contours
- vector fields
- fractals and dynamical systems
- projected 3-D curves and surfaces
- complex-plane plots

The book includes exact program-mode keystrokes, complete calculator listings, adjustable axis ticks and values, practical advice on windows and sampling, and 72 full-resolution example plots. The examples are generated as deterministic one-bit framebuffers, matching the DM42 display without smoothing, anti-aliasing or colour.

## Repository contents

- `main.tex` — handbook entry point
- `chapters/` — chapters and appendices
- `programs/` — readable DM42/Free42 listings and importable calculator binaries
- `figures/framebuffers/` — generated 400×240 plot images
- `generated/` — generated keystroke tables, program styling and plot catalogue
- `tools/` — figure, catalogue, keystroke and listing generators
- `dist/` — compiled handbook PDF
- `bibliography.bib` — technical sources used during validation

## Build from source

Run the generators and compile the book with XeLaTeX:

```sh
python3 tools/generate_framebuffers.py
python3 tools/generate_keystrokes.py
python3 tools/generate_catalogue.py
python3 tools/generate_program_highlights.py
latexmk -xelatex main.tex
```

The generators require Python 3, NumPy and Pillow. The handbook requires a reasonably complete TeX Live installation with XeLaTeX, Latin Modern, DejaVu Sans, TikZ/PGFPlots, `tcolorbox`, `listings`, `hyperref` and `cleveref`.

## DM42 program files

Each `.txt` file is a human-readable calculator program listing. Its matching `.raw` file can be imported with compatible DM42/Free42 transfer tools. The handbook also shows the physical-key or menu route for every program line.

### Why `CPLOT` is not a separate file

`CPLOT` is a public entry point identified by a global label. It shares a calculator program file with supporting routines such as coordinate mapping, axes and connected-line drawing. This arrangement keeps related code, register conventions and dependencies together, avoids duplicating common routines, and lets the complete toolkit be imported or exported as one unit. You still run it directly with `XEQ "CPLOT"`; sharing a file does not make it less independent as a callable routine.

## Reproducibility

All displayed calculator images are generated from the included source. The readable listings, calculator binaries, generation scripts and final PDF are kept together so that the programs and illustrations can be checked against the published handbook.

## Release notes

Version 0.51 removes the unnecessary “read it as…” asides while retaining the v0.5 listing improvements: matching pastel highlights for each `LBL` and its associated `GTO` lines, plus corrected spacing after program line numbers.
