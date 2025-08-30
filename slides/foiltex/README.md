# Making slides using FoilTeX

## FoilTeX installation

- Download FoilTeX source code: `curl -OL https://mirrors.ctan.org/macros/latex/contrib/foiltex.zip`.
- Unzip: `unzip foiltex.zip`.
- Compile the source to generate the style files: `cd foiltex && latex foiltex.ins`.
- Copy or move the `foils.cls`, `foil*.clo`, `fltfonts.def` and `foils.sty` files to some directory in the `TEXINPUTS` path. To do this, you can
  - put the style files into the same folder as the document source, or,
  - (for MacOS) create a folder named `texmf-local` under the `texlive` folder (which is located in `/usr/local` by default), then under the `texmf-local` folder, do:
    - `mkdir -p tex/latex/foiltex` and put the `foils.cls`, `foil*.clo`, `fltfonts.def` and `foils.sty` into this folder;
    - (optional for package documents) `mkdir -p doc/latex/foiltex` and put the generated document file `foiltex.pdf` and example file `sampfoil.tex` into this folder;
    - finally, run `mktexlsr` to update the LaTeX filename database.

## Usage

### Commands

In general, defining the general information for the slides document is more or less standard via `\title{}`, `\author{}`, and `\data{}` commands.
Then, the command `\maketitle` will insert a title page.

To add new sections and slide pages, use the following commands:

- `\makesection{}`: adding a new section page with title given in the argument; specifically for this page, a header defined by `\info{}` will appear as the right header.
- `\makefoil{}`: adding a new slide page with title given in the command argument.

### Generating PDF

It is recommended to compile the source with `pdflatex`; if bibTeX is also used, the recipe would be `pdflatex -> bibtex -> pdflatex -> pdflatex`.