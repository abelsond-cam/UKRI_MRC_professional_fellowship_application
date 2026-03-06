## UKRI / MRC Fellowship LaTeX project

This repository contains the LaTeX source for your UKRI / MRC fellowship application, organised by the sections that will be pasted into the Je-S/UKRI forms and then combined into a single compiled PDF.

### Project context

This repository contains the academic application of David Abelson, a respiratory physician and computational biologist trained in Australia and currently based in the Floto Lab at the University of Cambridge. The project is for an MRC Professional Clinical Fellowship. Collaborators and partners are described in the `Approach` and `Partners` sections, and the applicant’s career history and track record will be expanded in `application/5_applicant/` in due course.

### Overall structure

- **Top-level driver**: `fellowship.tex`
  - Sets up document class, packages, and global bibliography (`bib/references.bib` via `biblatex`/`biber`).
  - Pulls in section files from the `application/` folder and gives each section its **own reference list** using `refsection` / `\printbibliography`.

- **Application sections** (edited as standalone LaTeX files)
  - `application/1_summary/` – summary / lay sections (currently commented out in `fellowship.tex` but can be enabled when ready).
  - `application/3_approach/` – main research approach text (currently multiple versions; will be merged and versioned via git).
  - `application/4_stats/` – statistical design and analysis plan.
  - `application/5_applicant/` – applicant track record and related sections.

- **Bibliography**
  - `bib/references.bib` – central `.bib` file for all sections.
  - Each major section in `fellowship.tex` is wrapped in:
    - `\begin{refsection}` … `\end{refsection}`
    - `\printbibliography[heading=subbibliography,title={<Section> references}]`
  - This gives **separate reference lists per section** while sharing a common `.bib` database.

- **References (PDFs and key papers)**
  - `references/` – PDFs and other reference materials (protocols, key articles, etc.) used for:
    - Scientific context while drafting.
    - Checking numbers, effect sizes, and justifications for the Approach and Stats sections.
  - These files are **not** automatically cited; you still add cites manually to `bib/references.bib` and in the section `.tex` files.

- **Figures and diagrams**
  - Figures and diagrams for the application should live in dedicated subfolders (e.g. `figures/`, `application/3_approach/figures/`, etc.).
  - Include them from section `.tex` files using standard LaTeX figure environments and `\includegraphics`, relying on `\usepackage{graphicx}` already set up in `fellowship.tex`.

### Typical workflow

1. **Draft sections** in their respective `application/<section>/` folders (e.g. `3_approach`, `5_applicant`).
2. **Add / update references** in `bib/references.bib`, then cite them in the section files.
3. **Use PDFs in `references/`** as background material (read and mine them for text/ideas; they are not directly linked into LaTeX).
4. **Compile** the whole application from `fellowship.tex` (e.g. with `latexmk` + `biber` or your editor’s LaTeX build recipe) to see each section with its own bibliography.

### Notes on versions for `3_approach`

- The `application/3_approach/` folder currently contains multiple versions (e.g. `3_Approach_v0.2.tex`).
- The plan is to **merge these into a single canonical file** and then rely on **git history** (not filenames) for versioning.
- Until that merge is done, `fellowship.tex` currently points at `3_Approach_v0.2.tex`.

