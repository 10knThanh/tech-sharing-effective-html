# Kịch bản trình bày — Diagram as Code với Effective HTML (15')

> Slide: https://10knthanh.github.io/tech-sharing-effective-html/
> Demo project: `SharingPresent/simple-auth-demo`

---

## ✅ Checklist 30 phút trước giờ G

- [ ] Mở link slide, nhấn `F11` fullscreen — thử phím `↓` chuyển slide, nút `Theme` chọn sáng/tối hợp phòng
- [ ] Refresh slide một lần (các chip tương tác về trạng thái mặc định)
- [ ] Terminal: `cd ~/Projects/SharingPresent/simple-auth-demo`
- [ ] `git status` sạch, đang ở `main`, **không có thư mục docs/** (nếu có: `git checkout main -- . && rm -rf docs`)
- [ ] `node --version` ≥ 20.12 (CLI `skills` cần `util.styleText`)
- [ ] Chạy thử 1 lần: `npx skills add plannotator/effective-html --skill html-diagram -y` — rồi gỡ/reset lại repo cho sạch
- [ ] Mở sẵn `README.md` của simple-auth-demo (chứa toàn bộ prompt — **copy, đừng gõ tay**)
- [ ] Mở app SimpleAuth thử register/login; muốn demo sạch: DevTools → `localStorage.clear()`
- [ ] Tăng font terminal + editor (⌘+ vài lần)

**Nhớ:** repo là `plannotator` (có "or") — lần trước gõ `plannotat` là fail ngay trên sân khấu đấy 😄

---

## 🎬 Kịch bản theo slide

### Slide 1 — Title (0:00 → 0:30)

Nói: *"Hôm nay mình chia sẻ một cách làm diagram mà không cần kéo thả — viết diagram bằng code, sống trong repo, review qua PR như code."*

### Slide 2 — Khởi động (0:30 → 2:30)

- Hỏi câu 1: **"Ai ở đây có vẽ diagram khi làm việc? Giơ tay."** — đợi 3 giây, đếm miệng
- Hỏi câu 2: **"Mọi người đang vẽ bằng gì?"** — chỉ vào từng pill, hỏi "ai dùng Draw.io?", "ai dùng PowerPoint?"
- Chốt: *"Nhớ giúp mình tool các bạn vừa kể — 2 slide nữa ta sẽ gặp lại chúng."*

### Slide 3 — Agenda (2:30 → 2:45)

Lướt nhanh, chỉ nói: *"15 phút, phần dài nhất là live demo."*

### Slide 4 — Why (2:45 → 4:15)

- Chỉ vào pills: *"Đây chính là những tool mọi người vừa kể."*
- Đọc 4 pain point, mỗi cái 1 câu. Nhấn mạnh **"không review được trên PR"** — hỏi QA/reviewer trong phòng: *"đã bao giờ approve một PR đổi kiến trúc mà không biết kiến trúc đổi thế nào chưa?"*
- Kết bằng quote trên slide: *"Documentation thường bị bỏ quên sau vài sprint."*

### Slide 5 — What (4:15 → 5:45)

- *"Effective HTML = node là div, layout là CSS, diagram là DOM."*
- Chỉ code bên trái → kết quả bên phải: *"Đây là toàn bộ 'công sức vẽ'."*
- Buông một câu để dành: *"Và chính bộ slide này cũng là một file Effective HTML — cuối buổi mình cho xem source."*

### Slide 6 — AI + Effective HTML (5:45 → 7:15)

- *"Phần thú vị nhất: bạn không cần tự viết HTML. Cài skill một lần, sau đó chỉ prompt."*
- Chỉ workflow: Prompt → AI → Effective HTML → Diagram
- Chuyển cảnh: *"Nói suông không tin được — demo luôn."* → **chuyển sang terminal**

### Slide 7 → Live demo thật (7:15 → 11:15) — xem phần script bên dưới

Slide 7 (Prompt → diagram → git diff) dùng làm **bản đồ 3 bước** trước khi rời slide,
và là **phao cứu sinh** nếu demo thật trục trặc — quay lại slide, bấm 3 chip kể chuyện.

### Slide 8 — So sánh (11:15 → 12:00)

- Đừng đọc cả bảng — chỉ vào 3 hàng: **Review trên PR**, **Highlight flow** (chỉ Effective HTML có ✓) và **Xuất PNG/PDF** (hàng duy nhất Effective HTML thua — dẫn sang slide sau)
- Summary bên phải: *"Không phải thay thế tất cả — Draw.io cho business, Mermaid cho flowchart nhỏ, Effective HTML cho tài liệu kỹ thuật."*

### Slide 9 — Giới hạn (12:00 → 12:30)

- Nói thẳng 2 giới hạn: **sơ đồ rất lớn** (AI lo bố cục cho diagram cỡ tài liệu, nhưng vài chục node chằng chịt thì AI ước lượng toạ độ chứ không phải engine auto-routing — mỗi lần chỉnh là một vòng prompt) và **xuất ảnh tĩnh không chuyên** (dán Confluence/slide cho non-engineer vẫn là đất của Draw.io/Excalidraw)
- Nếu bị hỏi "AI lo layout rồi thì sao còn là giới hạn?": trả lời bằng chính ý trên — AI ước lượng, không tối ưu; sơ đồ nhỏ thì không sao, sơ đồ khổng lồ thì chia nhỏ theo domain
- Câu dẫn: *"Không có tool nào thắng tất cả — quan trọng là đúng việc. Nói thẳng giới hạn để mọi người chọn đúng."*
- Slide này giúp bạn ghi điểm khách quan trước Q&A

### Slide 10 — Tích hợp (12:30 → 13:00)

- Chỉ cây thư mục: *"diagram nằm cạnh code, đi cùng commit"*
- Chỉ workflow: *"bước 'update diagram' nằm ngay trong luồng làm việc, không phải việc làm thêm cuối sprint"*

### Slide 11 — Ví dụ thực tế · highlight flow (13:00 → 14:15) ⭐

**Điểm ăn tiền — thao tác chậm thôi:**
1. Để "Toàn cảnh": *"Một diagram, ba flow chồng chéo — chỗ này tool kéo thả bó tay."*
2. Bấm **Login flow** → đường sáng chạy: *"chỉ flow login sáng lên, phần còn lại mờ đi nhưng không mất."*
3. Bấm **Coupon flow** → *"thấy ngay nó đi qua Redis và Database dùng chung."*
4. Bấm **Mall refund flow** → *"nhánh Notification của riêng nó."*
5. Chốt: *"Tất cả chỉ là vài dòng CSS."*

### Slide 12 — Tổng kết (14:15 → 14:45)

Đọc chậm 4 dòng. Dòng cuối nhìn cả phòng: *"— chính là chúng ta."*

### Slide 13 — Q&A

Mở source repo slide cho ai muốn xem: `github.com/10knThanh/tech-sharing-effective-html`

---

## 🖥️ Script live demo (7:15 → 11:15)

### Bước 0 — Cho xem app (30s)

```bash
cd ~/Projects/SharingPresent/simple-auth-demo && npm run dev
```

Register → Login → Dashboard. Nói: *"Project web bình thường — và chưa có một diagram nào. `ls docs` — not found."*

### Bước 1 — Cài skill (30s)

```bash
npx skills add plannotator/effective-html --skill html-diagram -y
```

### Bước 2 — Prompt sinh diagram (90s)

Prompt 1 (copy từ README):

```
Create an architecture diagram for this authentication project.
Put it in docs/architecture/overview.html with a shared stylesheet
at docs/assets/diagram.css.
```

Trong lúc AI chạy → kể tiếp chuyện, đừng nhìn màn hình chờ. Xong → mở file → **diagram hiện ra**.

### Bước 3 — PO đổi yêu cầu (90s)

Nói: *"Giờ PO xuất hiện: 'cần thêm Forgot Password'. Tôi không mở Draw.io."*

```
Create a sequence diagram for forgot password flow
in docs/sequence/forgot-password.html.
Include: User, Frontend, Auth Service, Email Service, Database.
```

Refresh → done. (Nếu dư thời gian, chạy thêm prompt MFA.)

### Bước 4 — Chốt bằng git (30s)

```bash
git add docs && git diff --staged --stat
```

Nói: *"Diagram cũng chỉ là source code. Review qua PR như mọi thay đổi khác."* → quay lại slide 8.

### 🛟 Fallback nếu AI chậm/lỗi

```bash
git checkout demo-diagrams -- docs   # = kết quả prompt 1–3
git checkout demo-final -- docs      # = kết quả prompt 4–6 (forgot + MFA + email verification)
```

Refresh browser — diagram hiện ra, `git diff` cuối buổi vẫn diễn như thật.
Nói tỉnh bơ: *"Mình dùng bản đã sinh sẵn ở nhà cho nhanh — prompt y hệt trên màn hình."*

---

## ❓ Q&A dự kiến

| Câu hỏi | Trả lời gọn |
|---|---|
| "Diagram lớn thì HTML có rối không?" | Có shared CSS + component nên file diagram rất mỏng; đọc thì đã có flow highlight; và người viết chính là AI. |
| "Sao không dùng Mermaid luôn?" | Dùng song song! Mermaid cho flowchart nhỏ trong README. Effective HTML khi cần custom, interactive, nhiều flow chồng chéo. |
| "Người không biết HTML/CSS thì sao?" | Không cần biết — prompt là đủ. Người review chỉ đọc diff như đọc code. |
| "Diagram có tự sync với code không?" | Không tự động — nhưng nằm cùng repo nên đưa vào Definition of Done: đổi kiến trúc thì PR phải kèm cập nhật diagram, reviewer chặn được ngay. |
| "Có tốn thêm chi phí gì không?" | Skill là open source (MIT). AI assistant thì team đang dùng sẵn rồi. |

## 🎯 Một câu mang về

> **"Diagram cũng chỉ là source code — commit cùng nhau, review cùng nhau, và để AI viết phần vất vả."**
