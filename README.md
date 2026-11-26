# RobotiXX Lab LaTeX Paper Template

A modern, screen-friendly, two-column LaTeX template for papers and technical reports from the **[RobotiXX Lab](https://robotixx.cs.gmu.edu/)** at **George Mason University (GMU)**.

## Features

- **Modern Two-Column Layout:** Clean `letterpaper` geometry with generous margins and balanced column spacing.
- **Readable Typography:** Uses **EB Garamond** (lining figures) for warm, refined prose and headings paired with crisp **Times (`newtxmath`)** for math formulas and **Inconsolata** for monospace (optional `[times]` and `[sans]` modes are also supported).
- **GMU & RobotiXX Branding:** Incorporates the official [George Mason University brand palette](https://brand.gmu.edu/) (Mason Green `#005239`, Mason Gold `#FFC733`, Accent Teal `#008285`, Accent Red `#CC4824`) and the RobotiXX Lab header banner.
- **Standard Abbreviations:** Includes `robotixxabbrv.sty` for smart-spaced abbreviations (`\eg`, `\ie`, `\etal`, `\wrt`, `\cf`, `\aka`, etc.).

---

## Repository Structure

```text
.
├── robotixx.sty          # Core RobotiXX template package
├── robotixxabbrv.sty     # Standard abbreviations package (loaded automatically)
├── RobotiXX_gmu.png      # RobotiXX logo (used by pdflatex)
├── preamble.tex          # Document class, template import, and paper-specific packages
├── main.tex              # Main entry point (metadata, abstract, sections, bibliography)
├── main.bib              # BibTeX references
├── contents/             # Modular paper sections (abstract, introduction, method, etc.)
└── figures/              # Paper figures
```

---

## Quick Start

### 1. Compile Locally

Build the PDF with `pdflatex` and `bibtex`:

```bash
pdflatex main.tex
bibtex main
pdflatex main.tex
pdflatex main.tex
```

On Overleaf, upload the repository and set the compiler to **pdfLaTeX** with `main.tex` as the main document.

### 2. Configure Paper Metadata

In `main.tex`, set your paper details before `\begin{document}` and call `\maketop` right after `\begin{document}`:

```latex
\input{preamble}

\robotixxtitle{Your Paper Title Here}
\robotixxrunningtitle{Short Running Title}

\robotixxauthors{%
    \textbf{First Author}$^{1\dagger}$ \quad
    \textbf{Second Author}$^{1}$
}

\robotixxaffiliations{%
    $^1$RobotiXX Lab, Department of Computer Science, George Mason University, Fairfax, VA, USA
}

\robotixxmeta{%
    $^\dagger$Correspondence: \href{mailto:author@gmu.edu}{\texttt{author@gmu.edu}} \;\textbar\;
    \faGlobe\ \href{https://robotixx.cs.gmu.edu/}{robotixx.cs.gmu.edu}
}

\robotixxkeywords{Robotics, Motion Planning, Machine Learning}

\robotixxabstract{\input{contents/abstract}}

\begin{document}

\maketop

\input{contents/introduction}
% ...

\bibliographystyle{abbrvnat}
\bibliography{main}

\end{document}
```

### 3. Template Options

In `preamble.tex`, you can pass options to `\usepackage{robotixx}`:

- `\usepackage{robotixx}` — Default mode (EB Garamond text/headings, Times math, preprint date in header).
- `\usepackage[times]{robotixx}` — Classic Times (`newtxtext` + `newtxmath`) for both text and math.
- `\usepackage[sans]{robotixx}` — All-sans-serif body mode using Inter.
- `\usepackage[final]{robotixx}` — Hides the date from the top-right header bar.
- Customize the date directly via `\robotixxdate{January 2026}`.

---

## Abbreviations (`robotixxabbrv.sty`)

`robotixxabbrv.sty` is loaded automatically by `robotixx.sty` and provides:

| Macro | Output | Macro | Output |
| :--- | :--- | :--- | :--- |
| `\eg` | *e.g.* | `\wrt` | w.r.t. |
| `\ie` | *i.e.* | `\etc` | *etc.* |
| `\cf` | *cf.* | `\vs` | *vs.* |
| `\etal` | *et al.* | `\aka` | a.k.a. |
| `\iid` | i.i.d. | `\dof` | d.o.f. |

Trailing periods are handled automatically—write `(\eg, something)` or `... \etal.` without double periods.

---

## Brand Colors

The following GMU brand colors are available anywhere in your document (e.g., for TikZ diagrams, tables, or callouts):

- `gmugreen` (`#005239`) — Primary Mason Green
- `gmugold` (`#FFC733`) — Mason Gold
- `gmudark` (`#333333`) — Neutral Dark
- `gmuteal` (`#008285`) — Accent Teal
- `gmured` (`#CC4824`) — Accent Red
- `robotixxbg` (`#F4F7F6`) — Soft card background tint
- `robotixxborder` (`#D2DFDA`) — Subtle hairline border
