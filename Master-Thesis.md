# 🎓 Master's Thesis Template Documentation

This comprehensive guide covers the setup, structure, and compilation of the unofficial HCMUS Master's Thesis LaTeX template.

---

## 📌 Table of Contents
1. [⚙️ Quick Setup in `main.tex`](#-quick-setup-in-maintex)
2. [📄 Structure of `main.tex`](#-structure-of-maintex)
3. [📝 Writing Thesis Information (`thongtinluanvan.tex`)](#-writing-thesis-information-thongtinluanvantex)
4. [🗂️ Adding New Chapters & Appendices](#-adding-new-chapters--appendices)
5. [📚 References System (Biber & Split Bibliographies)](#-references-system-biber--split-bibliographies)
6. [🔤 Acronyms & Abbreviations (`acronyms.tex`)](#-acronyms--abbreviations-acronymstex)
7. [📄 Managing Publications (`publish.tex`)](#-managing-publications-publishtex)
8. [💝 Acknowledgements (`thanks.tex`)](#-acknowledgements-thankstex)
9. [🛠️ Local Compilation Guide](#-local-compilation-guide)
10. [🛠️ FAQ & Troubleshooting](#-faq--troubleshooting)

---

## ⚙️ Quick Setup in `main.tex`

Open [main.tex](https://github.com/khongsomeo/hcmus-unofficial-report-template/blob/main/thesis/master/main.tex) and configure the student metadata block:

```tex
% Tên học viên: {Tiếng Việt}{Tiếng Anh} (Không dùng \\)
\setHoVaTen{Nguyễn~Văn~A}{Nguyen Van A}

% Mã số học viên (MSSV) (Không dùng \\)
\setMSSV{22C11001}

% Khóa đào tạo (Ví dụ: K32/2022) (Không dùng \\)
\setKhoaDaoTao{K32/2022}

% Tên đề tài luận văn: {Tiếng Việt}{Tiếng Anh}
% [!] Được phép chứa dấu xuống dòng (\\) để tự động căn chỉnh trang bìa
\setTenKL{Nghiên~cứu~phát~triển~hệ~thống\\trí~tuệ~nhân~tạo}{Research and Development of Artificial Intelligence Systems}

% Mã số ngành (Không dùng \\)
\setMaNganh{8.48.01.01}

% Tên ngành đào tạo: {Tiếng Việt}{Tiếng Anh} (Không dùng \\)
\setTenNganh{Khoa học Máy tính}{Computer Science}

% Cán bộ hướng dẫn: {Tiếng Việt}{Tiếng Anh} (Không dùng \\)
% [!] Nếu có từ 2 cán bộ hướng dẫn trở lên, gọi dòng \addTenGVHD nhiều lần liên tiếp
\addTenGVHD{PGS. TS. Nguyễn Văn B}{Assoc. Prof. Dr. Nguyen Van B}
\addTenGVHD{TS. Trần Thị C}{Dr. Tran Thi C}

% Tên bộ môn (Không dùng \\)
\setTenBM{Công nghệ Tri thức}

% Địa điểm bảo vệ (Không dùng \\, mặc định là Tp. Hồ Chí Minh nếu comment)
% \setDiaChi{Tp. Hồ Chí Minh}
```

> [!WARNING]
> **Line Breaks (`\\`) Warning**
> Line breaks (`\\`) are strictly forbidden in all metadata fields except for the thesis title (`\setTenKL`). Putting line breaks in fields like student names or supervisor names will break the metadata processing and result in compilation errors.

---

## 📄 Structure of `main.tex`

The body of [main.tex](https://github.com/khongsomeo/hcmus-unofficial-report-template/blob/main/thesis/master/main.tex) is clean and focuses entirely on the logical structure of your thesis, hiding complex LaTeX resets and styles under the hood:

```latex
\begin{document}

% 1. Trang bìa (không đánh số trang)
\makethesiscover

% Bắt đầu đánh số trang La Mã (i, ii, iii, ...) cho phần giới thiệu đầu
\pagenumbering{roman}

% 2. Lời cam đoan
\inputreassurances

% 3. Lời cảm ơn
\inputthanks

% 4. Các trang mục lục và danh mục
\maketableofcontents
\makelistoffigures
\makelistoftables
\makeglossaryofacronyms

% 5. Trang thông tin luận văn (Tiếng Việt & Tiếng Anh)
% [!] Tự động định dạng các đề mục của trang thông tin và khôi phục khi hoàn tất
\inputthesisinfo

% ========================================================================================= %
% CÁC CHƯƠNG NỘI DUNG
% ========================================================================================= %

% Bắt đầu đánh số trang Ả Rập (1, 2, 3, ...) từ Chương 1
\pagenumbering{arabic}

\input{Thesis/Chapter1-Introduction/chapter1}
\input{Thesis/Chapter2-RelatedWorks/chapter2}
\input{Thesis/Chapter3/chapter3}
\input{Thesis/Chapter4/chapter4}
\input{Thesis/Chapter5-Conclusion/chapter5}

% ========================================================================================= %
% CÔNG TRÌNH & TÀI LIỆU THAM KHẢO & PHỤ LỤC
% ========================================================================================= %

% Danh mục công trình của tác giả (nếu không có thì comment dòng này)
\inputpublications

% In tài liệu tham khảo (Tự động chia nhóm Tiếng Việt & Tiếng Anh với số thứ tự liên tục)
\printthesisbibliography

% Phần phụ lục (nếu có)
\appendix
\input{Thesis/Appendix/appendix-a}

\end{document}
```

---

## 📝 Writing Thesis Information (`thongtinluanvan.tex`)

The thesis information page [thongtinluanvan.tex](https://github.com/khongsomeo/hcmus-unofficial-report-template/blob/main/thesis/master/Thesis/Appendix/thongtinluanvan.tex) uses logical environments. All the margins, signature tables, and page breaks are handled automatically.

```tex
\begin{trangthongtinluanvan}
    \begin{tomtatvi}
        % Viết tóm tắt nội dung luận văn Tiếng Việt tại đây...
    \end{tomtatvi}

    \begin{ketquamoivi}
        % Viết kết quả mới đạt được tại đây...
    \end{ketquamoivi}

    \begin{ungdungvi}
        % Viết khả năng ứng dụng thực tiễn tại đây...
    \end{ungdungvi}
\end{trangthongtinluanvan}

\begin{trangthesisinformation}
    \begin{summaryen}
        % Write English summary here...
    \end{summaryen}

    \begin{noveltyen}
        % Write English novelty here...
    \end{noveltyen}

    \begin{applicationsen}
        % Write English applications here...
    \end{applicationsen}
\end{trangthesisinformation}
```

> [!IMPORTANT]
> **Dynamic Supervisor Lists**
> You can print the formatted, comma-separated list of supervisors anywhere in your chapters by using:
> - `\listSupervisors` (Vietnamese, e.g., *PGS. TS. Nguyễn Văn B và TS. Trần Thị C*)
> - `\listSupervisorsEnglish` (English, e.g., *Assoc. Prof. Dr. Nguyen Van B and Dr. Tran Thi C*)

---

## 🗂️ Adding New Chapters & Appendices

### 1. Adding New Chapters
Each chapter is stored as a separate `.tex` file inside its own dedicated folder in the `Thesis/` directory (e.g., `Thesis/Chapter1-Introduction/chapter1.tex`).

> [!TIP]
> **Co-locating Resources**
> The purpose of creating a dedicated folder for each chapter is to keep chapter-specific resources (such as figures, images, or raw data tables) self-contained within that directory. This makes managing complex documents much easier and prevents cluttering the global folders.

#### How to Add a New Chapter
1. **Create the Folder & File**: Create a folder (e.g., `Thesis/Chapter6-MyNewChapter/`) and create a `.tex` file inside it (e.g., `chapter6.tex`).
2. **Start the Chapter**: Write the chapter header at the top of the file:
   ```tex
   \chapter{Tên Chương Mới}
   \label{Chapter6}
   
   Nội dung chương mới viết ở đây...
   ```
3. **Register in `main.tex`**: Import your chapter inside `main.tex` under the `% Các chương nội dung` block (before the publication/bibliography imports):
   ```tex
   \input{Thesis/Chapter6-MyNewChapter/chapter6}
   ```

### 2. Adding Appendices
Appendices are stored inside the `Thesis/Appendix/` directory (e.g., `Thesis/Appendix/appendix-a.tex`).

#### How to Add a New Appendix
1. **Create the File**: Create a `.tex` file (e.g., `Thesis/Appendix/appendix-b.tex`).
2. **Start the Appendix**: Use standard `\chapter` tags. In LaTeX, calling `\chapter` after the `\appendix` command automatically formats it as an Appendix (e.g., *Phụ lục B*) instead of a standard chapter:
   ```tex
   \chapter{Bảng Biểu Chi Tiết}
   \label{appendix:b}
   
   Nội dung phụ lục viết ở đây...
   ```
3. **Register in `main.tex`**: Import your appendix file inside `main.tex` under the `% Phần phụ lục` block (at the very bottom of the document):
   ```tex
   \appendix
   \input{Thesis/Appendix/appendix-a}
   \input{Thesis/Appendix/appendix-b}
   ```

---

## 📚 References System (Biber & Split Bibliographies)

The Master's Thesis template uses `biblatex` with the `biber` backend. This setup automates the separation of Vietnamese and English citations while maintaining continuous sequential numbering (e.g., Vietnamese entries start at `[1]`, and English entries continue from `[2]`, `[3]`, etc.).

### 1. How References are Split
The reference bibliography entries are stored in [Materials/References/references.bib](https://github.com/khongsomeo/hcmus-unofficial-report-template/blob/main/thesis/master/Materials/References/references.bib).
* **Vietnamese References**: Must include a `keywords = {Viet}` line in their BibTeX entries.
* **English/Foreign References**: Do **not** include the `keywords` line.

#### Example Vietnamese Entry:
```bibtex
@article{nguyen2026sample,
  author   = {Nguyen, Van A and Tran, Thi B},
  title    = {A Sample Reference for Vietnamese},
  journal  = {Journal of Computer Science},
  year     = {2026},
  keywords = {Viet}
}
```

#### Example English Entry:
```bibtex
@book{adams2026treatise,
  author    = {Adams, Albert},
  title     = {A Treatise on Computer Science},
  publisher = {Example Publishing},
  year      = {2026}
}
```

---

## 🔤 Acronyms & Abbreviations (`acronyms.tex`)

Acronyms and abbreviations are managed using the `glossaries` package inside [Thesis/Appendix/acronyms.tex](https://github.com/khongsomeo/hcmus-unofficial-report-template/blob/main/thesis/master/Thesis/Appendix/acronyms.tex).

### How to Define an Acronym
Define your acronyms in `acronyms.tex` using the `\newacronym` command:
```tex
\newacronym{label}{Abbreviation}{Full Description}
% Example:
\newacronym{ai}{AI}{Artificial Intelligence}
```

### How to Reference Acronyms in Text
Reference your defined acronyms in chapters using:
- `\gls{label}`: Standard reference (outputs full text on first use, e.g., *Artificial Intelligence (AI)*, and just abbreviation subsequently, e.g., *AI*).
- `\Gls{label}`: Capitalized first letter (for starting sentences).
- `\glspl{label}`: Plural form.

---

## 📄 Managing Publications (`publish.tex`)

The list of candidate publications is managed in [Thesis/Appendix/publish.tex](https://github.com/khongsomeo/hcmus-unofficial-report-template/blob/main/thesis/master/Thesis/Appendix/publish.tex).

### How to Add a New Publication
Add a new item inside the `enumerate` block using `\item[CT-xx]` and `\hypertarget`:
```tex
\item[CT-02] \hypertarget{pub:CT-02}{} \textbf{Họ Tên Tác Giả}, \textit{Tên bài báo mới}. Tên tạp chí/hội nghị, Năm.
```

> [!NOTE]
> **Understanding Labels**
> - The prefix `CT` stands for **"Công trình"** (work). You are free to change this prefix to whatever you prefer (e.g., `BB` for *Bài báo* or `PUB` for *Publication*).
> - Make sure to keep the labels consistent between `\item[...]` and the `\hypertarget{pub:...}{}` anchor so that any cross-references or hyperlinks point to the correct items.

### How to Remove the Publications Page
If you do not have any publications yet, simply comment out or remove this line in `main.tex`:
```tex
% \inputpublications
```

---

## 💝 Acknowledgements (`thanks.tex`)

The acknowledgements section is located in [Thesis/Appendix/thanks.tex](https://github.com/khongsomeo/hcmus-unofficial-report-template/blob/main/thesis/master/Thesis/Appendix/thanks.tex). 

### How to Edit Acknowledgements
1. Open `thanks.tex`.
2. Edit the content directly within the file.
3. You can dynamically print the correct list of your science supervisors by referencing `\listSupervisors` (Vietnamese format) or `\listSupervisorsEnglish` (English format) to ensure consistency.

---

## 🛠️ Local Compilation Guide

This guide explains how to compile the Master's Thesis template locally on your machine.

### 1. Automated Compilation (Recommended)
Navigate to the `thesis/master/` directory and execute the provided build script:
```bash
bash thesis-build.sh
```
This script automates the full compilation pipeline (PDFLaTeX -> Biber -> PDFLaTeX -> PDFLaTeX) to resolve all cross-references, glossary terms, and split bibliographies.

### 2. Manual Compilation
If you prefer to compile manually, run the following sequence of commands in the `thesis/master/` directory:
```bash
pdflatex main
biber main
pdflatex main
pdflatex main
```

> [!IMPORTANT]
> **Biber Backend Required**
> This template uses the `biber` backend for `biblatex` to handle continuous split reference numbering. Running legacy `bibtex` will result in missing bibliography lists or citations showing as `[0]`.

---

## 🛠️ FAQ & Troubleshooting

Here are the solutions to common issues when compiling the HCMUS Master's Thesis template.

### 1. Compilation Error: Metadata Field Processing
*   **Symptom**: Compilation fails with error messages inside the title page generation.
*   **Cause**: You put line breaks (`\\`) in a metadata field other than the thesis title.
*   **Solution**: Line breaks (`\\`) are strictly forbidden in all student/supervisor names, departments, programs, and date fields. Remove any `\\` from macros such as `\setHoVaTen`, `\addTenGVHD`, `\setTenBM`, and `\setMSSV`. Only the thesis title `\setTenKL` supports `\\`.

### 2. References are shown as [0] or missing
*   **Symptom**: All citations in the compiled PDF appear as `[0]` or are not printed in the bibliography page.
*   **Cause**: The bibliography was compiled using the legacy `bibtex` command instead of `biber`.
*   **Solution**: Make sure to run `biber main` instead of `bibtex main`, or use the provided build script `bash thesis-build.sh`.

### 3. Reference numbering is reset to [1] for the second section
*   **Symptom**: The Vietnamese bibliography starts at `[1]` and the English bibliography also starts at `[1]`.
*   **Cause**: `defernumbers=true` option is missing in the `biblatex` package configuration.
*   **Solution**: Ensure that your class file includes `defernumbers=true` inside `\RequirePackage[backend=biber,...]{biblatex}`. This is already enabled by default in the latest `hcmusthesis.cls`.
