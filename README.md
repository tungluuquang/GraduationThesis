# Khóa luận tốt nghiệp (KLTN)

Template LaTeX khóa luận tốt nghiệp — Trường Đại học Công nghệ, Đại học Quốc gia Hà Nội.

## Biên dịch

Template dùng `fontspec` nên **bắt buộc biên dịch bằng LuaLaTeX hoặc XeLaTeX** (kèm `biber` cho tài liệu tham khảo):

```bash
PATH="$HOME/.local/bin:$PATH" latexmk -f -lualatex -interaction=nonstopmode main.tex
```

Kết quả: `main.pdf`. Chạy lại 2–3 lần nếu còn cảnh báo "Rerun to get cross-references right".

