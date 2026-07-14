# 📝 Quiz Class Template Documentation

This comprehensive guide covers the setup, structure, and compilation of the unofficial HCMUS **Quiz** LaTeX template (located in the [quiz/](https://github.com/khongsomeo/hcmus-unofficial-report-template/tree/main/quiz) directory of the repository).

---

## 📌 Table of Contents
1. [⚙️ Quick Setup in `main.tex`](#quick-setup-in-maintex)
2. [📄 Quiz Template Structure](#quiz-template-structure)
3. [🛠️ Toggling Solutions/Answers](#toggling-solutionsanswers)
4. [💻 Source Code Highlighting](#source-code-highlighting)
5. [🛠️ Local Compilation Guide](#local-compilation-guide)

---

## ⚙️ Quick Setup in `main.tex`

Open [main.tex](https://github.com/khongsomeo/hcmus-unofficial-report-template/blob/main/quiz/main.tex) and configure the metadata parameters at the top of the file:

```tex
\documentclass[a4paper,14pt,oneside]{hcmusquiz}

\ExamName{Quiz 01}
\ExamTime{20 mins}
\ExamDate{October 22, 2025}
\CourseName{Data Structures and Algorithms}
\ClassName{25C05}

\ExamNote{Students can answer the questions in English or Vietnamese.}
```

### Parameter Explanations:
*   `\ExamName{...}`: The name of the exam sheet (e.g. `Quiz 01`, `Midterm Exam`, `Final Exam`).
*   `\ExamTime{...}`: Separate command to specify the exam duration (e.g. `20 mins`, `90 mins`). If omitted, it defaults to blank. If provided, it is automatically formatted in parentheses next to the exam name.
*   `\ExamDate{...}`: Date of the exam session.
*   `\CourseName{...}`: The name of the academic course.
*   `\ClassName{...}`: The class section/code.
*   `\ExamNote{...}`: Text parameter to define a custom exam note at the bottom of the student identity header box. If empty or omitted, the note section and its extra padding are hidden. It also supports `\CanAnswerInVietnamese` as a backward-compatible shortcut for the bilingual answer permission note: *Students can answer the questions in English or Vietnamese.*

---

## 📄 Quiz Template Structure

The template is organized as follows:
*   `main.tex`: Entry driver file containing quiz parameters and questions list.
*   `hcmusquiz.cls`: Custom LaTeX class file (inherits from standard `exam` class) containing margins, page boundaries, listings styling, headers, and name boxes.
*   **Identity Box (`addnamebox`)**: Invokes a clean box at the top of the first page containing fields for Full name, Student ID, and the optional bilingual note.
*   **Questions block (`questions`)**: Standard `exam` class environment wrapping all questions (`\question`), multiple choices (`choices` environment), and solution blocks (`solution` environment).
*   **End marker (`headline{END}`)**: Generates a centered, dotted line marking the end of the quiz paper.

---

## 🛠️ Toggling Solutions/Answers

The template supports generating both the blank student test paper and the completed teacher's answer key from the same source file.

To display correct choices and solution blocks, uncomment `\printanswers` in `main.tex`:

```tex
% Show answers: uncomment to display solution blocks and correct choices in red
\printanswers
```

When enabled:
- The correct choice defined via `\correctchoice` will be highlighted in **crimson red** (defined globally as `AnswerColor` matching `red!75!black`).
- Solution blocks inside `\begin{solution} ... \end{solution}` or `\begin{solutionordottedlines} ... \end{solutionordottedlines}` will render in a Beamer-like modern style (accented with a `3pt` thick left-margin line in `AnswerColor` and a subtle light red background).
- The correct answers inside the MCQ Answer Sheets are automatically rendered in `AnswerColor` (filled circles for bubble style and bold colored letters for table style).

---

## 📊 Layout & Choices Formatting

The template supports both vertical and horizontal multiple-choice layout blocks:
*   **Vertical Choices (`choices` environment)**: Standard vertical list block for long options.
*   **Equalized Horizontal Choices (`oneparchoices` environment)**: Redefined inside `hcmusquiz.cls` to distribute choices symmetrically across the page. Instead of being bunched together, options automatically stretch to fill the text width evenly using `\hfill`, keeping the margins aligned.

---

## 📝 MCQ Answer Sheets

The class introduces a specialized command `\MCQAnswerBox[instruction]{style}` to dynamically render multiple-choice answer blocks at any position in the document. The sheet automatically counts the total number of exam questions (`\numquestions`) and populates correct answers from the template's `\correctchoice` markers when `\printanswers` is active.

### 1. Circle-Filling Style (`\MCQAnswerBox[instruction]{circle}`)
*   Generates a double-column bubble grid matching the total question count.
*   Renders choices inline (e.g. `(A) (B) (C) (D)`).
*   If `\printanswers` is active, the correct choice bubble is highlighted in **bold crimson red** (`AnswerColor`).
*   **Optional instruction parameter**: By invoking `\MCQAnswerBox[instruction]{circle}`, you append a clear set of student filling guidelines (drawing a TikZ sample filled bubble) right above the sheets.
*   **Customization**: Define the number of choices (default is 4) using `\NumChoices{N}` (supports up to 8: `A` to `H`).

### 2. Table-Filling Style (`\MCQAnswerBox[instruction]{fill}`)
*   Generates a full-page width tabular grid (using `tabularx`) with two rows:
    - **Row 1**: Question numbers (`1`, `2`, `3` ...).
    - **Row 2**: Answer boxes for students to write in.
*   If `\printanswers` is active, correct answer letters populate the second row cells in **bold crimson red** (`AnswerColor`).
*   **Optional instruction parameter**: By invoking `\MCQAnswerBox[instruction]{fill}`, you append clear student write-in instructions right above the tables.
*   **Customization**: Define the maximum questions allowed per row (default is 10) using `\MaxMCQPerRow{M}`. If the total number of MCQ questions exceeds `M`, it will automatically split into stacked table rows, separating each header and student writing block.

---

## 💻 Source Code Highlighting

The custom class `hcmusquiz.cls` imports the `listings` package and pre-configures it for styling source code blocks (specifically tailored for C++ syntax).

```latex
\begin{lstlisting}
int main() {
    std::cout << "Hello, HCMUS!";
    return 0;
}
\end{lstlisting}
```

This will automatically format keywords in blue, comments in green, and strings in purple with line numbering on the left.

---

## 🛠️ Local Compilation Guide

### 1. Automated Compilation (Recommended)
Navigate to the `quiz/` directory and execute the provided helper script:
```bash
bash build.sh
```

### 2. Manual Compilation
If you prefer manual compilation, run the following command sequence inside the `quiz/` directory:
```bash
pdflatex main
pdflatex main
```
*(No BibTeX is required as this template does not include a bibliography by default).*

