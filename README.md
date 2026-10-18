# Template khóa luận tốt nghiệp (KLTN)

Template LaTeX khóa luận tốt nghiệp — Trường Đại học Công nghệ, Đại học Quốc gia Hà Nội.
Repo đã được **dọn sạch nội dung cũ**, chỉ còn lại template và các chương mẫu để bạn viết nội dung mới.

## Cấu trúc thư mục

| Đường dẫn | Mô tả |
|---|---|
| `main.tex` | File chính: khai báo, mục lục, danh sách hình/bảng/thuật toán/đoạn mã, thuật ngữ, gọi các chương |
| `setting/thesis-style.tex` | Cấu hình template (font, biblatex, listings, algorithm2e, kích thước trang...) |
| `setting/bkthesis.sty`, `setting/cs.sty`, `setting/uetthesis.sty` | Các gói phụ trợ của template |
| `chapters/0-coverpage.tex` | 3 trang bìa, Lời cam đoan, Lời cảm ơn, Tóm tắt, Abstract |
| `chapters/1-problem-statement.tex` | Đặt vấn đề (chương không đánh số) |
| `chapters/2-background-knowledge.tex` | Kiến thức nền tảng (có ví dụ về bảng + đoạn mã) |
| `chapters/3-detail-of-method.tex` | Phương pháp đề xuất (có ví dụ về thuật toán + công thức) |
| `chapters/4-implement.tex` | Cài đặt và thử nghiệm (có ví dụ về hình vẽ + danh sách) |
| `chapters/5-conclusion.tex` | Kết luận (chương không đánh số) |
| `refs.bib` | Tài liệu tham khảo — `keywords = {vietnam}` ⇒ in ở mục "Tiếng Việt", còn lại ⇒ "Tiếng Anh" |
| `images/` | Hình ảnh; giữ `Logo_UET.png` cho trang bìa |

## Cách compile

Template dùng gói `fontspec` nên **bắt buộc biên dịch bằng LuaLaTeX hoặc XeLaTeX**, không dùng pdfLaTeX được.
Cần chạy `biber` cho phần tài liệu tham khảo (biblatex).

```bash
cd Thesis-main
PATH="$HOME/.local/bin:$PATH" latexmk -f -lualatex -interaction=nonstopmode main.tex
```

* Chạy lệnh trên 2–3 lần nếu còn cảnh báo "Rerun to get cross-references right" (mục lục, danh sách hình, số trang).
* Trong VS Code, có thể dùng LaTeX Workshop với `latexmk` và engine `lualatex`.
* Nếu máy có `sudo`, cách gọn hơn: `sudo apt install texlive-bibtex-extra biber` rồi chỉ cần
  `latexmk -lualatex main.tex`.

## Việc cần làm khi bắt đầu

1. Điền tên đề tài, họ tên, cán bộ hướng dẫn, năm vào `chapters/0-coverpage.tex`
   (mục cuối bìa tự lấy năm hiện tại bằng `\the\year`), và `pdftitle` / `pdfauthor` trong `main.tex`.
2. Xoá 3 entry mẫu trong `refs.bib` và thêm tài liệu thật; nhớ trích dẫn bằng `\cite{...}` thì tài liệu mới được in.
3. Xoá nội dung mẫu trong `chapters/2-…`, `3-…`, `4-…` và viết nội dung thật của bạn.
4. Điền bảng "Thuật ngữ" trong `main.tex`.

## Ghi chú kỹ thuật

* **Font**: `mathptmx` được nạp **trước** `fontspec` trong `setting/thesis-style.tex`. Đây là chủ ý:
  `mathptmx` có lệnh `\def\rmdefault{ptm}`, nếu nạp sau `\setmainfont{Times New Roman}` thì toàn bộ văn bản
  sẽ bị thay bằng font Latin Modern. Đừng đảo lại thứ tự này.
* **Cỡ chữ 13pt**: dùng `\changefontsizes[16pt]{13pt}` (gói `scrfontsizes`) thay vì tuỳ chọn lớp văn bản.
* **Hình véc-tơ**: nên chèn hình `.pdf`; gói `svg` đã được nạp nếu bạn muốn dùng `.svg` (khi đó cần
  `-shell-escape` và Inkscape).
* Kết quả biên dịch: `main.pdf`; các file phụ (`*.aux`, `*.bcf`, `*.log`…) đã được `.gitignore` bỏ qua.
