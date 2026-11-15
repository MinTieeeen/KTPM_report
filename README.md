# Báo cáo BTL Kiến trúc Phần mềm – Hệ thống chấm công và kiểm soát ra vào bằng mã QR (TMC)

Mã nguồn LaTeX của báo cáo môn Kiến trúc Phần mềm (CO3017), lớp L01, GVHD ThS. Lê Đình Thuận.
Báo cáo gồm hai milestone: **M1** (phân tích yêu cầu, thiết kế kiến trúc) và **M2** (hoàn thiện thiết kế, hiện thực, kiểm thử).

## Cấu trúc thư mục

```
KTPM_report/
├── main.tex                  # File gốc: preamble, trang bìa, danh sách thành viên, lịch sử phiên bản, thứ tự \include
├── references.bib            # Tài liệu tham khảo (biblatex + biber)
├── appendix.tex              # Phụ lục: sơ đồ use case và đặc tả use case
├── section/                  # Nội dung từng phần, đánh số theo thứ tự trong báo cáo
│   ├── 1_Introduction.tex
│   ├── 2_Context_System_Requirement.tex   # Bối cảnh, mục tiêu (OBJ), ràng buộc (C), giả định (A), rủi ro (R), phạm vi, stakeholder
│   ├── 3_Requirements_Analysis.tex        # Yêu cầu chức năng (FR) và phi chức năng (NFR)
│   ├── 4_Domain_Model_Design.tex          # Luồng nghiệp vụ, thực thể, lược đồ lớp
│   ├── 5_Architecture_Characteristics.tex # Đặc tính kiến trúc, top-3, trade-off
│   ├── 6_Architecture_Structure.tex       # Quantum, chọn style, kiến trúc logic và vật lý
│   ├── 7_Architecture_Decisions.tex       # ADR
│   └── 8_Design_Principles.tex            # Nguyên tắc thiết kế, SOLID, tổ chức mã nguồn
├── figures/                  # Hình dùng trong báo cáo, mỗi thư mục con ứng với một phần
│   ├── common/               # Logo, hình dùng chung
│   ├── 04_domain_model/      # Lược đồ lớp
│   ├── 06_architecture_structure/  # Sơ đồ component, sơ đồ triển khai
│   ├── 08_design_principles/ # Cấu trúc module
│   └── appendix_use_case/    # Sơ đồ use case (tiền tố uc_)
└── build/                    # Kết quả build (bị .gitignore)
```

File nguồn sơ đồ (draw.io) và các bản nháp cũ **không** nằm trong thư mục này mà ở `../artifacts/` (cùng cấp với `KTPM_report/`):

```
artifacts/
├── drawio/        # File .drawio nguồn của các hình; PNG xuất ra được chép vào figures/<phần>/
└── archive/       # Bản nháp, hình cũ không còn dùng trong báo cáo
```

## Quy ước

- **Tên hình:** `figures/<số phần>_<tên phần>/<tên_hình>.png`, chữ thường, phân tách bằng `_`. Hình thuộc phần nào thì đặt trong thư mục của phần đó.
- **Mã định danh:** OBJ-xx (mục tiêu), C-xx (ràng buộc), A-xx (giả định), R-xx (rủi ro), P-xx (vấn đề), FR-xx, NFR-<nhóm>-xx, INV-xx (bất biến), G1–G5 / C1–C9 (component), ADR-xx, DP-xx. Phần sau chỉ dùng mã đã được định nghĩa ở phần trước.
- **Tham chiếu chéo:** dùng `\label{...}` và `\ref{...}`, không viết cứng số bảng, số hình hay số mục.

## Build

Yêu cầu: TeX Live hoặc MiKTeX có `pdflatex`, `biber`, `latexmk`.

```bash
latexmk -pdf -outdir=build main.tex
```

Kết quả nằm ở `build/main.pdf`. Trong VS Code (LaTeX Workshop), đặt `outDir` là `build`.
