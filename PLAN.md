# Kế hoạch: Bài present hàng tuần bằng HTML diagram

## Mục tiêu

- Xây dựng bộ slide HTML chạy trực tiếp trên browser — không cần PowerPoint, không cần build tool, mở file là trình chiếu được.
- Diagram được viết bằng code (diagram-as-code) nên dễ sửa, dễ version control, và tái sử dụng cho các tuần sau.
- Chủ đề tuần đầu tiên: **"Dùng HTML diagram để tối ưu diagram trong phát triển phần mềm/web"** — vừa là bài present, vừa là demo sống cho chính chủ đề đó.

## Công nghệ đề xuất

Deck dựng theo phong cách **effective-html** (github.com/plannotator/effective-html):
một file HTML tự chứa, không dependency, không CDN — CSS + SVG viết tay,
scroll-snap để chuyển slide, dark mode tự nhận theo hệ thống (nút Theme để đổi tay).

| Thành phần | Vai trò |
|---|---|
| **Scroll-snap slides** | Chuyển slide bằng phím mũi tên / space, có bộ đếm trang |
| **SVG + CSS variables** | Diagram tương tác: flow chip làm sáng từng luồng, tự đổi theo dark mode |
| **Mermaid** (đề cập trong nội dung) | Công cụ đề xuất cho diagram hằng ngày trong docs/PR |

Ghi chú: `template.html` và `assets/theme.css` là phiên bản Reveal.js cũ, giữ lại để tham khảo.

## Cấu trúc thư mục

```
html-diagram/
├── index.html          # Deck của tuần này (chủ đề HTML diagram)
├── template.html       # Template trắng — copy cho các tuần sau
├── assets/
│   ├── theme.css       # Theme công ty: màu, font, logo
│   └── diagrams/       # SVG diagram tách riêng (nếu phức tạp)
└── PLAN.md             # File này
```

## Outline: "Effective HTML — A New Way to Build Technical Diagrams" (12 slide, 15 phút)

1. **Title** — Effective HTML · Diagram as Code for modern development teams
2. **Agenda** — 7 phần kèm thời lượng
3. **Why** (2') — vấn đề của diagram truyền thống + quote "Documentation thường bị bỏ quên sau vài sprint"
4. **What** (2') — HTML + CSS + component thay vì kéo thả; benefits
5. **AI + Effective HTML** (2') — `npx skills add plannotator/effective-html --skill html-diagram`; Prompt → AI → Effective HTML → Diagram
6. **Live demo** (5') — slide tương tác 3 bước đúng kịch bản: Generate login flow → Add Redis Cache (node highlight) → git diff (+2 dòng)
7. **Comparison** (2') — bảng 4 công cụ (EH / Draw.io / Mermaid / Excalidraw) + summary chọn tool
8. **Who should use it** — highly recommended vs. less suitable
9. **Integration** (1') — cấu trúc docs/, workflow Developer→…→Merge, tích hợp GitHub/GitLab/Wiki/Pages/ADR
10. **Real examples** — chip chuyển giữa Login / Coupon / Mall refund flow (sát team Mobile + Backend + QA)
11. **Key takeaways** (1')
12. **Q&A**

Kịch bản live demo thật (5'): prompt AI sinh `docs/architecture/login.html` → prompt "Add Redis Cache"
→ render lại → `git diff` cho thấy chỉ +2 dòng. File mẫu để diff: `demo/login-flow.html`.

## Các bước thực hiện

- **Phase 1 — Skeleton**: dựng `index.html` với Reveal.js qua CDN, tạo `theme.css` theo màu nhận diện công ty
- **Phase 2 — Nội dung**: viết 12 slide theo outline, code các diagram demo (Mermaid + SVG)
- **Phase 3 — Polish**: animation fragment (hiện từng ý), speaker notes, kiểm tra export PDF
- **Phase 4 — Template hoá**: tách `template.html` sạch để các tuần sau chỉ cần copy và điền nội dung

## Workflow hàng tuần (sau khi có template)

1. Copy `template.html` → `2026-07-14-ten-chu-de.html`
2. Điền nội dung, vẽ diagram bằng Mermaid (nhanh) hoặc SVG (khi cần tuỳ biến)
3. Mở file bằng browser, nhấn `F` để fullscreen, `S` để mở speaker notes
4. Cần chia sẻ sau buổi present: thêm `?print-pdf` vào URL rồi in ra PDF

## Mẹo trình chiếu Reveal.js

- `←/→` chuyển slide, `ESC` xem tổng quan toàn bộ slide, `B` màn hình đen tạm dừng
- Speaker notes hiện trên cửa sổ riêng kèm đồng hồ đếm giờ — hợp với slot 15 phút hàng tuần
