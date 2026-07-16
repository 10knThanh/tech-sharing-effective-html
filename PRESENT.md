# Kịch bản trình bày — Diagram as Code với Effective HTML (15')

> Slide: https://10knthanh.github.io/tech-sharing-effective-html/
> Demo project: `SharingPresent/simple-auth-demo`
> Ngày: **16/07/2026**

---

## 🖥️ Trình chiếu toàn màn hình

- **Fullscreen:** mở link slide trên trình duyệt → nhấn `F11` (Windows/Linux) hoặc `⌃⌘F` (Chrome/Safari trên Mac). Nhấn lại / `Esc` để thoát.
- **Chuyển slide:** `→` `↓` `Space` (tiến) · `←` `↑` (lùi) · hoặc cuộn chuột. Góc phải dưới có số trang.
- **Cỡ chữ trên TV/máy chiếu:** slide **tự phóng to** theo màn hình — màn ≥1600px (Full HD) phóng 1.28×, màn ≥2400px (4K) phóng 1.65×. Chiếu 65" là chữ đã to sẵn.
- Muốn to/nhỏ thêm: nhấn `⌃/⌘ +` và `⌃/⌘ -` ngay trên trình duyệt (zoom cả trang). Hoặc chỉnh 2 số trong `index.html` (tìm `zoom: 1.28`).

---

## ✅ Checklist 30 phút trước giờ G

- [ ] Mở link slide, nhấn `F11` fullscreen — thử phím `↓` chuyển slide, nút `Theme` chọn sáng/tối hợp phòng
- [ ] Chiếu thử lên đúng màn hình 65" — kiểm tra chữ đủ to từ cuối phòng (chưa đủ thì `⌘/⌃ +`)
- [ ] Refresh slide một lần (các chip tương tác về trạng thái mặc định)
- [ ] Terminal: `cd ~/Projects/SharingPresent/simple-auth-demo`
- [ ] `git status` sạch, đang ở `main`, **không có thư mục docs/** (nếu có: `git checkout main -- . && rm -rf docs`)
- [ ] `node --version` ≥ 20.12 (CLI `skills` cần `util.styleText`)
- [ ] Chạy thử 1 lần: `npx skills add plannotator/effective-html --skill html-diagram -y` — rồi gỡ/reset lại repo cho sạch
- [ ] Mở sẵn `README.md` của simple-auth-demo (chứa toàn bộ prompt — **copy, đừng gõ tay**)
- [ ] Mở app SimpleAuth thử register/login; muốn demo sạch: DevTools → `localStorage.clear()`
- [ ] Tăng font terminal + editor (⌘+ vài lần)
- [ ] Optional: `npm run docs` sau khi có docs — hub có Architecture + Register + Login + Forgot + **Payment**

**Nhớ:** repo là `plannotator` (có "or") — lần trước gõ `plannotat` là fail ngay trên sân khấu đấy 😄

---

## 🎬 Kịch bản theo slide

### Slide 1 — Title (0:00 → 0:30)

Nói: *"Hôm nay mình chia sẻ một cách làm diagram mà không cần kéo thả — viết diagram bằng code, sống trong repo, review qua PR như code. Demo trên project SimpleAuth."*

### Slide 2 — Khởi động (0:30 → 2:30)

- Hỏi câu 1: **"Ai ở đây có vẽ diagram khi làm việc? Giơ tay."** — đợi 3 giây, đếm miệng
- Hỏi câu 2: **"Mọi người đang vẽ bằng gì?"** — chỉ vào từng pill, hỏi "ai dùng Draw.io?", "ai dùng PowerPoint?"
- Chốt: *"Nhớ giúp mình tool các bạn vừa kể — 2 slide nữa ta sẽ gặp lại chúng."*

### Slide 3 — Agenda (2:30 → 2:45)

Lướt nhanh, chỉ nói: *"15 phút, phần dài nhất là live demo SimpleAuth — gồm cả highlight multi-flow."*
Không nhắc lại khởi động (vừa xong rồi).

### Slide 4 — Why (2:45 → 4:15)

- Chỉ vào pills: *"Đây chính là những tool mọi người vừa kể."*
- Đọc 4 pain point, mỗi cái 1 câu. Nhấn mạnh **"không review được trên PR"** — hỏi QA/reviewer trong phòng: *"đã bao giờ approve một PR đổi kiến trúc mà không biết kiến trúc đổi thế nào chưa?"*
- Kết bằng quote trên slide: *"Documentation thường bị bỏ quên sau vài sprint."*

### Slide 5 — What (4:15 → 5:45)

- *"Effective HTML = node là div, layout là CSS, diagram là DOM."*
- Chỉ code bên trái → kết quả bên phải: *"Đây là toàn bộ 'công sức vẽ'."*
- Buông một câu để dành: *"Và chính bộ slide này cũng là một file Effective HTML — cuối buổi mình cho xem source."*

### Slide 6 — AI + Effective HTML (5:45 → 7:00)

- *"Phần thú vị nhất: bạn không cần tự viết HTML. Cài skill một lần, sau đó chỉ prompt."*
- Chỉ workflow: Prompt → AI → Effective HTML → Diagram
- Chuyển tiếp: *"Vậy trong project thật, diagram sinh ra sẽ nằm ở đâu?"*

### Slide 7 — Tích hợp vào project (7:00 → 7:45)

- Chỉ cây thư mục **đúng SimpleAuth**:
  `docs/architecture/overview.html` · `sequence/register · login · forgot-password · payment` · `assets/diagram.css`
- Chỉ quy trình: *"bước 'sửa diagram' nằm ngay trong luồng làm việc, không phải việc làm thêm cuối sprint"*
- Chuyển cảnh: *"Nói suông không tin được — demo SimpleAuth từ con số 0."* → **chuyển sang terminal**

### Slide 8 → Live demo thật (7:45 → 11:15) — xem phần script bên dưới

Slide 8 (Prompt → diagram → git diff) = **bản đồ 3 bước SimpleAuth**:
1. Sinh architecture → 2. Thêm Payment → 3. git diff  
Dùng làm **phao cứu sinh** nếu AI trục trặc — quay lại slide, bấm 3 chip kể chuyện.

### Slide 9 — Highlight multi-flow ⭐ (11:15 → 12:30) — **điểm ăn tiền, ngay sau demo**

Khán giả vừa thấy diagram SimpleAuth trong browser. Ngay lúc đó show USP:

1. **Toàn cảnh**: *"Một sơ đồ SimpleAuth — login, forgot password, payment chồng chéo."*
2. **Login flow** → Browser → Gateway → Auth → User / PostgreSQL
3. **Forgot password** → Auth + Email Service + DB (reset token)
4. **Payment flow** → Payment Service + Payment Gateway (Stripe-like) + PostgreSQL
5. Chốt: *"Đúng những service vừa sinh trong demo — tất cả chỉ là vài dòng CSS."*

### Slide 10 — So sánh (12:30 → 13:05)

- Chỉ 3 hàng: **Review trên PR**, **Highlight flow** (vừa demo), **Xuất PNG/PDF** (hàng thua → dẫn slide sau)
- Summary: *"Draw.io cho business, Mermaid cho flowchart nhỏ (song song), Effective HTML khi cần custom / interactive / nhiều flow."*

### Slide 11 — Giới hạn (13:05 → 13:35)

- Hai giới hạn: sơ đồ rất lớn (AI ước lượng toạ độ, không auto-routing) · xuất ảnh tĩnh không chuyên
- Chốt: *"Không có tool nào thắng tất cả — đúng việc là đủ."*

### Slide 12 — Tổng kết (13:35 → 14:05)

Đọc chậm 4 dòng. Dòng cuối: *"— chính là chúng ta."*

### Slide 13 — Q&A

Source slide: `github.com/10knThanh/tech-sharing-effective-html`  
Demo: `SharingPresent/simple-auth-demo` · branch `demo-final` có đủ diagram kể cả payment.

---

## 🖥️ Script live demo — SimpleAuth (7:45 → 11:15)

### Bước 0 — Cho xem app (30s)

```bash
cd ~/Projects/SharingPresent/simple-auth-demo && npm run dev
```

Register → Login → Dashboard. Nói: *"Project web auth bình thường — chưa có một diagram nào. `ls docs` — not found."*

### Bước 1 — Cài skill (30s)

```bash
npx skills add plannotator/effective-html --skill html-diagram -y
```

### Bước 2 — Sinh architecture (≈60–90s)

Prompt 1 (copy từ README):

```
Create an architecture diagram for this authentication project.
Put it in docs/architecture/overview.html with a shared stylesheet
at docs/assets/diagram.css.
```

Trong lúc AI chạy → kể tiếp chuyện. Xong → mở file / `npm run docs` → **overview hiện ra**.

*(Nếu dư thời gian: prompt 2–3 sinh register + login sequence.)*

### Bước 3 — PO đổi yêu cầu: Payment (≈90s) ⭐

Nói: *"PO: 'Sau login cần thanh toán'. Tôi không mở Draw.io."*

Prompt 7 (copy từ README):

```
Create a sequence diagram for payment / checkout flow in docs/sequence/payment.html,
reusing docs/assets/diagram.css. Include: User, Frontend, Auth Service,
Payment Service, Payment Gateway, Database. Mark new elements with class "new".
Then update docs/architecture/overview.html to add a Payment Service node
(class "new") and link it from docs/index.html.
```

Refresh hub docs → card **Payment flow** + node Payment Service trên architecture.

*(Fallback ngắn nếu thiếu giờ: chỉ chạy forgot-password — prompt 4 — rồi chuyển nhanh sang payment bằng checkout `demo-final`.)*

### Bước 4 — Chốt bằng git (30s)

```bash
git add docs && git diff --staged --stat
```

Nói: *"Diagram cũng chỉ là source code — đúng cây thư mục slide Tích hợp vừa chiếu."*
→ quay lại slide bản đồ 3 bước (nếu cần) → **ngay sang highlight Login / Forgot / Payment**.

### 🛟 Fallback nếu AI chậm/lỗi

```bash
git checkout demo-diagrams -- docs   # = kết quả prompt 1–3 (architecture + register + login)
git checkout demo-final -- docs      # = đủ diagram: forgot + MFA + email verify + payment
```

Refresh browser — diagram hiện ra, `git diff` cuối buổi vẫn diễn như thật.
Nói tỉnh bơ: *"Mình dùng bản đã sinh sẵn ở nhà cho nhanh — prompt y hệt trên màn hình."*

---

## ❓ Q&A dự kiến

### So sánh công cụ

- **"Sao không dùng Mermaid luôn?"** — Dùng song song! Mermaid cho flowchart nhỏ trong README (nhanh, cú pháp gọn). Effective HTML khi cần custom layout, interactive, nhiều flow chồng chéo (login + forgot + payment trên cùng một sơ đồ), hoặc diagram là tài liệu chính của hệ thống.
- **"Mermaid cũng là code, cũng diff/review được mà?"** — Đúng, và đó là lý do Mermaid ở chiếu trên Draw.io. Khác biệt: Mermaid bị giới hạn theme + engine tự bố cục; Effective HTML là HTML/CSS thuần nên tuỳ biến vô hạn, thêm được hover/animation/highlight flow — thứ Mermaid không làm được.
- **"PlantUML / D2 / Structurizr thì sao?"** — Cùng triết lý diagram-as-code, đều tốt. Điểm khác của Effective HTML: không cần cài renderer riêng (chỉ browser), và AI sinh cực nhanh vì HTML/CSS là thứ mọi LLM thạo nhất.
- **"Draw.io cũng lưu được dạng XML trong Git mà?"** — Lưu được, nhưng XML kéo thả không đọc được bằng mắt khi review; đổi 1 node là cả chục dòng toạ độ thay đổi. Diff vô nghĩa với reviewer.

### Quy trình & tích hợp

- **"Diagram có tự sync với code không?"** — Không tự động. Nhưng nằm cùng repo nên đưa được vào Definition of Done: đổi kiến trúc thì PR phải kèm cập nhật diagram, reviewer chặn ngay nếu thiếu. Kỷ luật quy trình, không phải magic.
- **"Ai chịu trách nhiệm cập nhật diagram?"** — Chính người sửa code trong PR đó — vì giờ chỉ là sửa vài dòng + prompt, chi phí thấp nên không đùn đẩy. Trước đây tách rời tool nên "để sau" rồi quên.
- **"Làm sao đưa vào CI/CD?"** — Diagram là file tĩnh: GitHub Action build → deploy GitHub Pages/GitLab Pages → team mở URL. Không cần bước render phức tạp.
- **"Non-engineer (PO/BA) xem thế nào?"** — Deploy Pages ra URL để xem trên browser; hoặc xuất PNG/PDF dán Confluence (đây là điểm Draw.io mạnh hơn — đã nói ở slide Giới hạn).

### Về AI

- **"AI vẽ sai kiến trúc thì sao?"** — AI sinh bản nháp, người **review và sửa** như review code do junior viết. Không phải "AI thay người", mà "AI làm phần vất vả, người kiểm chứng".
- **"Không có AI thì có dùng được không?"** — Được, vẫn viết tay HTML/CSS như mọi component. AI chỉ giúp nhanh hơn, không phải điều kiện bắt buộc.
- **"Prompt mỗi lần ra layout khác nhau, khó kiểm soát?"** — Có shared `diagram.css` + convention class (`node`, `svc`, `data`, `new`) nên kết quả nhất quán. Prompt càng cụ thể (chỉ định file, class) càng ổn định — xem các prompt mẫu trong README.
- **"Tốn token/chi phí AI không?"** — Diagram nhỏ nên rẻ; và team đang dùng AI assistant sẵn rồi.

### Kỹ thuật & giới hạn

- **"Diagram lớn (vài chục node) thì HTML có rối không?"** — Đây là giới hạn thật (slide 10): AI ước lượng toạ độ chứ không auto-routing như Draw.io. Cách xử lý: chia nhỏ theo domain, mỗi diagram một câu chuyện.
- **"File diagram có bị phình to không?"** — Không — shared CSS tách riêng, mỗi file chỉ còn cấu trúc node/arrow, rất mỏng. Đó cũng là lý do diff sạch.
- **"Có làm được sequence/ERD/state diagram không?"** — Được hết, đều là HTML/CSS. Demo có architecture + sequence (register/login/forgot/payment). ERD, deployment, network… chỉ là prompt khác.
- **"Responsive / in ấn thì sao?"** — Responsive tốt (CSS flex/grid). In ra PDF được nhưng không "pixel-perfect" như tool chuyên xuất ảnh.

### Áp dụng cho team

- **"Người không biết HTML/CSS dùng được không?"** — Người **tạo** chỉ cần prompt. Người **review** chỉ đọc diff như đọc code. Không ai phải học layout thủ công.
- **"Bắt đầu từ đâu cho nhẹ?"** — Tuần này chọn 1 module đang làm, vẽ 1 diagram bằng Effective HTML đặt trong `docs/`. Thấy hợp thì mở rộng dần, đưa vào DoD.
- **"Có cần bỏ hết Draw.io/Figma không?"** — Không. Draw.io cho brainstorm/business, Figma cho design, Mermaid cho flowchart nhỏ. Effective HTML cho tài liệu kỹ thuật sống trong repo.

### Bảo mật & chi phí

- **"App demo có thanh toán thật không?"** — Không — SimpleAuth fake auth bằng localStorage. Payment/MFA/email verification chỉ sống trong `docs/` để minh hoạ diagram-as-code, không có backend thật.
- **"Có tốn thêm chi phí license không?"** — Skill open source (MIT). Không có license phải mua.
- **"Diagram deploy Pages có lộ kiến trúc nội bộ không?"** — Dùng private repo / GitLab Pages nội bộ / chỉ xem local. Giống như source code — phân quyền theo repo.

## 🎯 Một câu mang về

> **"Diagram cũng chỉ là source code — commit cùng nhau, review cùng nhau, và để AI viết phần vất vả."**
