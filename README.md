# HKA LaTeX Template for Group Projects

This repository contains a LaTeX template designed for group projects and theses at the **Hochschule Karlsruhe (University of Applied Sciences)**, specifically adapted for the Faculty of Mechanical Engineering and Mechatronics.

It provides a structured, professional framework complying with university formatting standards, allowing students to focus on content rather than layout.

## Table of Contents
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Project Structure](#project-structure)
- [Configuration](#configuration)
- [Usage](#usage)
- [Credits](#credits)

## Features

* **HKA Corporate Identity:** Includes the HKA logo and defines official colors (e.g., `HKA_MMTblue`).
* **Group Project Support:** Pre-configured for up to three authors (Name, Student ID).
* **Multi-Language:** Supports both **German** (default) and **American English**. Language can be toggled via settings.
* **Modular Structure:** Content is split into separate files (Introduction, Chapters, Appendix) for better version control and collaboration.
* **Professional Components:**
    * Automatic Title Page generation.
    * Non-Disclosure Notice (Sperrvermerk) logic based on company involvement.
    * Acronyms and Glossary support via `acronym` and `glossaries` packages.
    * Bibliography management using `biblatex` (IEEE style by default).
    * Declaration of Authorship (Eidesstattliche Erklärung).

## Prerequisites

To compile this project, you need a LaTeX distribution and an editor installed on your machine.

* **LaTeX Distribution:** [TeX Live](https://www.tug.org/texlive/) (Linux/Windows), [MacTeX](https://www.tug.org/mactex/) (macOS), or [MiKTeX](https://miktex.org/).
* **Editor:** [TeXstudio](https://www.texstudio.org/), [Texmaker](https://www.xm1math.net/texmaker/), or VS Code with the LaTeX Workshop extension.
* **Online Alternative:** This project is compatible with [Overleaf](https://www.overleaf.com/).

## Project Structure

The repository is organized as follows:

```text
.
├── main.tex                  # The root file that integrates all other files
├── bibliography.bib          # Bibliography entries
├── Glossar.bib               # Glossary definitions
├── Figures/                  # Directory for images and diagrams
│   ├── png/                  # Raster images (e.g., HKA Logo)
│   ├── signature/            # Scanned signatures
│   └── tikz2pdf/             # TikZ diagram sources
└── TeXFiles/                 # Content and configuration files
    ├── 000_Settings.tex      # Global variables (Names, Title, Language)
    ├── 001_Titlepage.tex     # Title page layout
    ├── 002_NDNotice.tex      # Non-disclosure notice
    ├── 004_Acronyms.tex      # Acronym definitions
    ├── 005_Glossar.tex       # Glossary setup
    ├── 010_Einleitung.tex    # Chapter 1
    ├── 110_Anhang.tex        # Appendix
    └── 120_Declaration.tex   # Declaration of authorship
```

## Configuration

All project-specific metadata should be edited in ```TeXFiles/000_Settings.tex```. You do not need to modify the layout files manually.

1. **Open** ```TeXFiles/000_Settings.tex```.

1. **Update Author Details:**

    ```Code-Snippet
    \newcommand{\NameA}{Your Name}
    \newcommand{\StudentIdA}{Matrikelnr. 123456}
    % Repeat for NameB/C if working in a group
    ```

1. **Set Thesis Metadata:** Update ```\ThesisTitle```, ```\ThesisSubtitle```, ```\Supervisor```, etc.

1. **Company Involvement:** If no company is involved, ensure the following line remains:

    ```Code-Snippet
    \newcommand{\CompanyName}{NoCompanyInvolved}
    ```

    If a company is involved, replace NoCompanyInvolved with the company name to automatically enable the Non-Disclosure Notice.

1. **Language Selection:** To switch the thesis language to English, uncomment the following line at the end of ```000_Settings.tex```:

    ```Code-Snippet
    %\newcommand*{\ThesisLanguageIsEnglish}{} 
    ```

    Remove the ```%``` to activate English.

## Usage

1. **Writing Content:**

    * Write your chapters in the files located in ```TeXFiles/``` (e.g., ```010_Einleitung.tex```, ```020_chapter2.tex```).

    * To add new chapters, create a new ```.tex``` file in ```TeXFiles/``` and include it in ```main.tex``` using ```\input{TeXFiles/Filename}```.

1. **Adding Citations:**

    * Add your BibTeX entries to ```bibliography.bib```.

    * Cite them in the text using ```\cite{key}```.

1. **Compiling:**

    * Set your compiler to **LuaLaTeX** or **pdfLaTeX**.

    * Run the build chain:

        1. ```pdflatex main```

        1. ```biber main``` (for bibliography)

        1. ```makeglossaries main``` (if using glossary)

        1. ```pdflatex main```

        1. ```pdflatex main```

1. **Signatures:**

    * Place a scan of your signature in ```Figures/signature/```.

    * Update the filename reference in ```TeXFiles/120_Declaration.tex``` if necessary (default is ```YourSignature_w.png```).

## Credits

**Original Creator:** Prof. Dr.-Ing. Thomas Hollstein (Frankfurt University of Applied Sciences)

**Adapted for HKA:** Paul Glaser, B. Eng

**Last Revision:** January 12, 2026