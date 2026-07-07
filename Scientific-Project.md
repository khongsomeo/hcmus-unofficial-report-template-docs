# 🔬 Scientific Project Template Documentation

This comprehensive guide covers the setup, structure, and compilation of the unofficial HCMUS **Scientific Project** LaTeX templates (located in the [scientific-research/](https://github.com/khongsomeo/hcmus-unofficial-report-template/tree/main/scientific-research) directory of the repository), which includes the final project report and the formal acceptance request form.

---

## 📌 Table of Contents
1. [⚙️ Project Report Quick Setup in `Report/Config.tex`](#project-report-quick-setup-in-reportconfigtex)
2. [📄 Project Report Structure](#project-report-structure)
3. [⚙️ Acceptance Request Form Setup](#acceptance-request-form-setup)
4. [🛠️ Local Compilation Guide](#local-compilation-guide)

---

## ⚙️ Project Report Quick Setup in `Report/Config.tex`

Open [Report/Config.tex](https://github.com/khongsomeo/hcmus-unofficial-report-template/blob/main/scientific-research/project-report/Report/Config.tex) and configure the project metadata block:

```tex
% Thiết lập trang bìa: điền 1 để chọn mẫu bìa mới (không logo, viền đôi đen sát nhau), 0 để chọn mẫu bìa cũ (có logo, viền xanh)
\BiaMoi{1}

% 1. Thông tin chung về đề tài
\Tendetai{Tên đề tài nghiên cứu khoa học bằng tiếng Việt}
\TendetaiTiengAnh{English Title of the Scientific Research Project}
\MasoDeTai{ABCD-202X-XX}
\ChunhiemDeTai{Học vị.}{Họ và tên chủ nhiệm đề tài}
\newcommand{\KinhphiDuyet}{100} % Số triệu đồng
\newcommand{\KinhphiBangchu}{Một trăm}
\newcommand{\ThoigianHopdong}{12 tháng, từ MM/YYYY đến MM/YYYY}
\newcommand{\ThoigianGiahan}{0 tháng}
\newcommand{\ThoigianThucte}{12 tháng, từ MM/YYYY đến MM/YYYY}
\DiaPhuongBaoCao{Tp. Hồ Chí Minh}
```

### 👥 Adding Project Members
Add members under the `% 2. Danh sách chủ nhiệm, thành viên tham gia thực hiện đề tài` block using the `\AddMember` macro:
```tex
\AddMember{Mã số}{Họ và tên}{Đơn vị công tác}{Vai trò trong đề tài}
% Example:
\AddMember{1001}{PGS. TS. Nguyễn Văn A}{Trường ĐH KHTN, ĐHQG-HCM}{Thành viên chính}
```

### 📚 Registering Project Publications
Declare academic articles or papers outputted by the project:
```tex
\AddCongBoConfIntl{Tác giả}{Năm}{Tên công trình}{Thông tin chi tiết}{Xếp hạng}{DOI}{ISSN/ISBN}{Tình trạng}
```

### 💰 Budget Allocation Table
Define the direct/indirect expenses to generate the automated financial statement table:
```tex
\SetKinhPhiNhanCong{80000000}{80000000}
\SetKinhPhiVatLieu{10000000}{10000000}
\SetKinhPhiThietBi{5000000}{5000000}
```

---

## 📄 Project Report Structure

The project report is organized as follows, keeping only files requiring user editing visible:
*   `main.tex`: Entry driver file invoking document layout setups and sections.
*   `baocaotonghophcmus.cls`: Document class file encapsulating page geometrics, tables, and static report components (`TitlePage`, `Part I: General Info`, `Part III: Publications`, `Part IV: Budget`).
*   `Report/Config.tex`: Configuration file for entering project metadata, member listings, publication registries, and budget statements.
*   `Report/PartII.tex`: Chapter II (Research Objectives, Scope, and Methodology) where you write the core research text.
*   `Report/PartV.tex`: Chapter V (Conclusions, Recommendations, and Future Work).
*   `Report/Report.bib`: Bibliography citations database.

---

## ⚙️ Acceptance Request Form Setup

Open [main.tex](https://github.com/khongsomeo/hcmus-unofficial-report-template/blob/main/scientific-research/acceptance-form/main.tex) in the `acceptance-form/` directory and configure the metadata parameters:

```tex
\DonviQuanly{Khoa Công nghệ Thông tin} % Tên đơn vị quản lý đề tài

\NgayKy{\dots} % Ngày ký đơn
\ThangKy{\dots} % Tháng ký đơn
\NamKy{\dots\dots} % Năm ký đơn

\HoTenChuNhiem{Học vị}{Họ tên chủ nhiệm} % Họ tên chủ nhiệm đề tài: {Học vị}{Họ tên}
\TenDeTai{Tên đề tài nghiên cứu khoa học của bạn}
\MasoDeTai{Mã số đề tài (ví dụ: ABCD-202X-XX)} % Mã số đề tài
\NamDangKy{202X} % Năm đăng ký thực hiện đề tài

\KinhGoiDonVi{Ban chủ nhiệm Khoa / Phòng quản lý đề tài}
\XacNhanDonVi{Ban chủ nhiệm Khoa / Phòng quản lý đề tài}
```

### 👥 Declaring Review Committee Members
Add review board members (President, Reviewer, Member, Secretary) using the `\DeclareMember` command:
```tex
\DeclareMember{Mã vai trò}{Họ và Tên}{Đơn vị công tác}{MSCB}
% Example:
\DeclareMember{ChuTich}{PGS. TS. Nguyễn Văn A}{Trường ĐHKHTN, ĐHQG-HCM}{MS1234}
```

---

## 🎨 Template Compilation Modes (Review vs. Print)

Both templates are designed with two compilation modes: **Review** (for drafting and checking) and **Print/Publish** (for final submission). These are configured via the class options in `\documentclass`.

### 1. Scientific Research Project Report (`baocaotonghophcmus`)
*   **Review Mode** (`\documentclass[review]{baocaotonghophcmus}`):
    *   Renders the official template box label (`Mẫu T-BCTH-22v1`) on the front cover.
    *   Adds column index labels `(1), (2), (3)...` below table headers for verification.
    *   Leaves the signature date blank with dotted placeholders (`ngày ............ tháng ............ năm ............`) for hand signing.
*   **Print/Publish Mode** (`\documentclass[print]{baocaotonghophcmus}` or `\documentclass[publish]{baocaotonghophcmus}`):
    *   Hides the template box label on the cover.
    *   Hides the table column index labels for a clean academic layout.
    *   Automatically stamps the current system date in the signature block.

### 2. Acceptance Request Form (`dondenghinghiemthuhcmus`)
*   **Review Mode** (`\documentclass[review]{dondenghinghiemthuhcmus}`):
    *   Displays the form template box (`Mẫu T-ĐĐNNT-22v1`) at the top right.
    *   Highlights all filled text and variables in **purple color** to easily identify completed sections.
*   **Print/Publish Mode** (`\documentclass[print]{dondenghinghiemthuhcmus}` or `\documentclass[publish]{dondenghinghiemthuhcmus}`):
    *   Hides the form template box at the top.
    *   Renders all text in standard academic black.

---

## 🛠️ Local Compilation Guide

### 1. Automated Compilation (Recommended)
Navigate to the `scientific-research/` directory and execute the provided helper script:
```bash
bash build.sh
```
This script will present an interactive menu allowing you to choose whether to compile the **Project Report** or the **Acceptance Request Form**.

Alternatively, you can compile specific templates directly by passing the target name:
- **Compile Report**: `bash build.sh report`
- **Compile Form**: `bash build.sh form`

### 2. Manual Compilation
If you prefer manual compilation, run the following command sequence inside either the `project-report/` or `acceptance-form/` directories:
```bash
pdflatex main
bibtex main     # (Only required for project-report to compile references)
pdflatex main
pdflatex main
```
