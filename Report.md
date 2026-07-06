# 📄 Report Template Documentation

This comprehensive guide covers the setup, structure, and compilation of the unofficial HCMUS Course Report LaTeX template.

---

## 📌 Table of Contents
1. [⚙️ Report Template Quick Setup](#-report-template-quick-setup)
2. [📄 Report Template Structure](#-report-template-structure)
3. [🛠️ Report Local Compilation Guide](#-report-local-compilation-guide)

---

## ⚙️ Report Template Quick Setup

Open the report's [main.tex](https://github.com/khongsomeo/hcmus-unofficial-report-template/blob/main/report/main.tex) file and customize the metadata fields:

```tex
% Define course name, report name, and report title.
\newcommand{\coursename}{Môn Học Gì Đấy}
\newcommand{\reportname}{Tên Báo Cáo Gì Đấy}
\newcommand{\reporttitle}{Báo cáo Bài Tập Gì Đấy}

% Define students participating (use \\ for line breaks between names)
\newcommand{\studentname}{Quan, Tran Hoang (19120338)\\meadoge(19120000)\\Hwang S. Wan (19120000)}

% Define supervisor/teacher name
\newcommand{\teachername}{GS.\ TS.\ Nguyễn Văn Hướng Dẫn}
```

### 🛠️ Options & Configuration
The template preamble supports these optional configurations:

*   **Line Spacing**: Set to `1.5` by default. Can be adjusted by modifying `\renewcommand{\baselinestretch}{1.5}`.
*   **Indentation**: Paragraph indentation is disabled by default via `\setlength{\parindent}{0pt}`.
*   **Times Font**: Uncomment `\usepackage{mathptmx}` to use the Times New Roman font family.
*   **Roman Section Headings**: Uncomment these rows to use Roman numerals for sections and subsections:
    ```tex
    % \renewcommand{\thesection}{\Roman{section}}
    % \renewcommand{\thesubsection}{\thesection.\Roman{subsection}}
    ```

---

## 📄 Report Template Structure

The report template is highly modular, separating different components (code, images, math, tables) into standalone files under the `content/` folder for ease of maintenance.

### 🗂️ File Organization

*   `main.tex`: Entry point containing page layout resets and modular inputs.
*   `hcmus-report-template.sty`: Custom package handling package imports, headers, and footer layouts.
*   `img/`: Holds graphic assets (such as university logos and figures).
*   `ref/ref.bib`: BibTeX file containing citation references.
*   `appendix/appendix.tex`: Appendices.

### 📝 Document Body Modules (`content/`)

*   `content/title.tex`: The cover page format (reads metadata from `main.tex`).
*   `content/section.tex`: General text structure, sections, and subsections.
*   `content/hinhanh.tex`: Guidelines on inserting figures, adjusting scaling, and adding captions.
*   `content/bangbieu.tex`: Guidelines on generating tables.
*   `content/congthuctoan.tex`: LaTeX math equations, matrices, and symbols.
*   `content/thuattoan.tex`: Writing algorithms and pseudocode using the `algorithm` package.
*   `content/code.tex`: Inserting code listings (such as C++ or Python) with custom colors and line numbering.
*   `content/ngonngu.tex`: Vietnamese language setup.
*   `content/cite.tex`: Demonstrates how to cite references using `\cite`.

---

## 🛠️ Report Local Compilation Guide

The report template utilizes standard BibTeX for references. Unlike the thesis template (which uses Biber), this template compiles using the traditional BibTeX workflow.

### 1. Compilation Command Sequence
To compile the report template locally, execute the following sequence of commands in the `report/` directory:

```bash
pdflatex main
bibtex main
pdflatex main
pdflatex main
```

### 2. Preamble Clean Up
Ensure that your graphics path and fonts are resolved. If you are using custom images, make sure they are placed in `img/` or set a custom path using:
```tex
\graphicspath{{img/}}
```
