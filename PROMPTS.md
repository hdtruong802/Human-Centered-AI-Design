# PROMPTS — StudyMate AI Prototype

Bộ prompt copy-paste để dùng AI (Cursor, ChatGPT, Claude, v0, v.v.) tạo mockup/HTML clickable cho bài lab **Human-Centered AI Design — AI Personal Assistant for Students**.

**Lát cắt:** AI đọc email trường → tạo nhiệm vụ học tập → sắp xếp ưu tiên tuần → nhắc việc & khôi phục khi sai.

---

## Cách dùng

1. Chạy **Master prompt** (mục 1) một lần ở đầu phiên chat để AI nắm context.
2. Chạy lần lượt prompt từng màn (mục 2) — mỗi lần 1 màn, lưu file HTML theo tên gợi ý.
3. Chạy **Prompt nối prototype** (mục 3) khi đã có đủ các file HTML.
4. Dùng **Prompt chỉnh sửa nhanh** (mục 4) nếu thiếu Act/Ask/Don't Act hoặc ô feedback 2×2.

### Quy ước output

| Thuộc tính | Giá trị |
|------------|---------|
| Ngôn ngữ UI | Tiếng Việt |
| Persona | Sinh viên đại học năm 2 |
| Email mẫu | `@student.university.edu` |
| Tên app | **StudyMate AI** |
| Style | Mobile-first 375px, clean, accessible |
| Dữ liệu mẫu | CS101, MATH201, deadline 25/06, giảng viên Nguyễn Văn A |
| Format | 1 file HTML self-contained, inline CSS |
| Điều hướng | Nút/link dùng `data-next="tên-file"` hoặc `href` tương ứng |

Mỗi màn **bắt buộc** có:

- Trạng thái AI rõ (đang xử lý / đề xuất / chờ xác nhận / đã khôi phục)
- Nút/quyền kiểm soát của user
- **Sticky rationale note** góc phải (font nhỏ, nền vàng nhạt): AI biết gì / chưa biết / rủi ro / Act·Ask·Don't Act
- Nhãn `[Act]` / `[Ask]` / `[Don't Act]` trên hành động AI tương ứng

**Không** làm chatbot hỏi–đáp đơn thuần.

### Danh sách file output gợi ý

```
prototype/
  00-flow-map.html
  01-onboarding.html
  01b-connect-data.html
  02-email-scanning.html
  02-task-proposal.html
  02-week-priority.html
  03-review-facts.html
  03-draft-email.html
  04-wrong-deadline.html
  04-error-feedback.html
  04-recovery.html
  05-feedback-matrix.html
  06-rationale.html
  07-demo-path.html   ← tạo bằng prompt stitch
```

---

## 1. Master prompt

Copy toàn bộ khối dưới đây vào đầu mỗi phiên làm việc mới:

```
Bạn là UI/UX designer + front-end developer. Tạo prototype HTML/CSS clickable cho bài lab
"Human-Centered AI Design" — đề tài AI Personal Assistant for Students.

Lát cắt tính năng: AI đọc email trường → tạo nhiệm vụ học tập → sắp xếp ưu tiên tuần
→ nhắc việc & khôi phục khi sai.

Yêu cầu bắt buộc mọi màn hình:
- Tiếng Việt, mobile-first 375px, tên app StudyMate AI
- KHÔNG chỉ là chatbot; phải có trạng thái AI, quyền kiểm soát user, recovery path
- Mỗi màn có sticky rationale note (góc phải, font 11px, nền #FFF9E6, viền vàng)
  trả lời: AI biết gì / chưa biết / rủi ro / mức Act·Ask·Don't Act
- Gắn nhãn [Act] / [Ask] / [Don't Act] trên hành động AI tương ứng
- Dùng dữ liệu mẫu cố định:
  • Môn CS101 (Giảng viên Nguyễn Văn A, email: nguyenvana@university.edu)
  • Môn MATH201 (Giảng viên Trần Thị B, email: tranthib@university.edu)
  • Deadline mẫu: 25/06/2026
  • Email sinh viên: minh.nguyen@student.university.edu
- Output: 1 file HTML self-contained, inline CSS, không cần build step
- Nút điều hướng sang màn tiếp theo dùng data-next="tên-file" (không .html)
- Không cần backend/API thật; dùng nội dung giả lập có sẵn
- Accessibility: contrast đủ, nút ≥ 44px chiều cao, focus ring rõ
- Font: system-ui, -apple-system, sans-serif; màu chủ đạo xanh #2563EB

Kịch bản đã chọn: S0 Onboarding, S1 Kết nối dữ liệu, S4 Tạo task từ email,
S2 Ưu tiên deadline tuần, S6 Gán nhầm deadline, S9 Soạn email giảng viên.

Xác nhận đã hiểu context, sau đó chờ tôi gửi prompt từng màn cụ thể.
```

---

## 2. Prompt từng màn hình

Mỗi prompt bên dưới — copy **Master prompt** trước, rồi copy prompt màn tương ứng.

---

### `00-flow-map` — Sơ đồ tổng quan 4 giai đoạn

```
[Tiếp tục từ master prompt]

Tạo màn 00-flow-map — Sơ đồ luồng prototype StudyMate AI.

Bối cảnh: Trang mở đầu cho người chấm bài / demo, thể hiện vòng đời 4 giai đoạn:
Onboarding → During → After → Feedback.

UI:
- Header: "StudyMate AI — Flow Map"
- 4 cột hoặc 4 card dọc (mobile scroll), mỗi giai đoạn có:
  • Tên giai đoạn (tiếng Việt + tiếng Anh nhỏ)
  • Kịch bản gắn: S0, S1, S4, S2, S9, S6
  • 2–3 bullet mô tả ngắn
  • Nút "Xem màn" link tới màn đầu của giai đoạn đó
- Sơ đồ mũi tên nối: S0 → S1 → S4 → S2 → (S9 / S6) → Feedback
- Legend nhỏ: [Act] xanh / [Ask] cam / [Don't Act] đỏ
- Footer: "Bắt đầu demo" → data-next="01-onboarding"

Links gợi ý:
- Onboarding → 01-onboarding
- During → 02-email-scanning
- After → 03-review-facts
- Failure → 04-wrong-deadline
- Feedback → 05-feedback-matrix

Rationale note: giải thích vì sao chọn lát cắt email→task→priority→recovery.
```

---

### `01-onboarding` — S0 First-time Onboarding

```
[Tiếp tục từ master prompt]

Tạo màn 01-onboarding — S0 First-time Onboarding cho StudyMate AI.

Bối cảnh: Sinh viên Minh lần đầu mở app, chưa biết AI quản lý deadline/email được tới đâu.

UI — 3 bước (swipe dots hoặc 3 card xếp dọc, có thể dùng JS đơn giản chuyển bước):

Bước 1 — "AI có thể giúp":
- Icon + bullet: đọc email trường, tạo task tự động, gợi ý ưu tiên tuần, soạn email nháp
- Badge [Ask] bên cạnh "đọc email" và "tạo task"

Bước 2 — "AI không tự làm":
- Bullet: gửi email thay bạn, nộp bài, đăng ký môn, trả lời thay bạn
- Badge [Don't Act] nổi bật

Bước 3 — "Bạn kiểm soát":
- Bullet: bỏ qua bất cứ lúc nào, thu hồi quyền, chỉnh sau trong Cài đặt
- Nút chính: "Kết nối dữ liệu" → data-next="01b-connect-data"
- Nút phụ (text link): "Khám phá trước" → data-next="02-week-priority" (skip onboarding)

Trạng thái AI (banner trên): "Chưa có dữ liệu học tập — AI chưa thể đề xuất"
Progress dots: 1/3, 2/3, 3/3

Rationale note: vì sao không dùng form dài ngay đầu; progressive disclosure giảm cognitive load.

Không dùng chat input. Phải có nút "Bỏ qua" ở header.
```

---

### `01b-connect-data` — S1 Kết nối dữ liệu học tập

```
[Tiếp tục từ master prompt]

Tạo màn 01b-connect-data — S1 Xin kết nối email + lịch học.

Bối cảnh: Sau onboarding, app cần consent trước khi đọc email trường.

UI — Modal hoặc full-screen sheet:
- Tiêu đề: "Kết nối dữ liệu học tập"
- Phần "Lợi ích": 3 bullet (tự tạo task, nhắc deadline, gợi ý ưu tiên)
- Phần "Phạm vi dữ liệu" (expandable):
  • Email trường (@student.university.edu) — chỉ đọc, không gửi
  • Lịch học — chỉ xem deadline
  • KHÔNG đọc: tin nhắn cá nhân, ảnh, liên hệ
- Toggle từng nguồn (email ON, lịch ON) — user có thể tắt từng cái
- Link "Chính sách quyền riêng tư" (placeholder #)
- Nút chính [Ask]: "Cho phép kết nối" → data-next="02-email-scanning"
- Nút phụ: "Để sau" → data-next="02-week-priority" (chế độ hạn chế)

Banner [Explicit System → User]: "Bạn có thể thu hồi quyền bất cứ lúc nào trong Cài đặt"

Rationale note: consent granular — không all-or-nothing; rủi ro đọc email nhầm phạm vi.
```

---

### `02-email-scanning` — S4 During (đang đọc email)

```
[Tiếp tục từ master prompt]

Tạo màn 02-email-scanning — S4 trạng thái During: AI đang đọc email.

Bối cảnh: User vừa cho phép kết nối; AI bắt đầu quét hộp thư trường.

UI:
- Header: "Đang đồng bộ email trường"
- Progress bar animated (CSS): ~60% hoặc indeterminate
- Text trạng thái đổi dần (có thể fake bằng JS timeout 2s mỗi dòng):
  "Đang kết nối..." → "Đang phân tích 2/5 email..." → "Tìm thấy 1 deadline tiềm năng"
- Danh sách email đang xử lý (3 dòng mẫu, 1 dòng highlight):
  • "[CS101] Nộp bài tập 3 trước 25/06" ← đang phân tích
  • "Thông báo nghỉ học MATH201"
  • "Newsletter thư viện"
- Nút "Hủy quét" (user control)
- Sau 3–4 giây (JS), tự chuyển hoặc nút "Xem đề xuất" → data-next="02-task-proposal"

Banner [Explicit System → User]: "AI đang đọc — chưa tạo task nào"

Implicit system cue: thanh tiến độ + số email đã xử lý (không chỉ spinner mù).

Rationale note: transparency trong quá trình xử lý; user biết AI đang làm gì trước khi Act.
```

---

### `02-task-proposal` — S4 After (đề xuất task từ email)

```
[Tiếp tục từ master prompt]

Tạo màn 02-task-proposal — S4 AI đề xuất tạo nhiệm vụ từ email trường.

Bối cảnh: AI vừa đọc email tiêu đề "[CS101] Nộp bài tập 3 trước 25/06" nhưng email
có thể thuộc môn khác hoặc chỉ là thông báo chung.

UI:
- Card đề xuất task chính:
  • "Nộp Bài tập 3 — CS101 — Deadline 25/06"
  • Badge "Từ email" (fact) vs "Suy luận AI" (inference) trên từng field
- Panel "Bằng chứng" (expandable, mặc định mở):
  • Trích 2 dòng email nguồn + ngày nhận 20/06/2026
  • Link "Xem email đầy đủ" (mở modal nội dung giả)
- Nút hành động:
  • "Chấp nhận" [Ask] — secondary style (không phải CTA chính)
  • "Sửa" — mở inline edit môn/deadline
  • "Từ chối" — text button
- Banner [Explicit System → User]: "AI đề xuất — chưa lưu vào lịch"

Implicit system cue: nút "Xem nguồn email" nổi bật hơn nút Chấp nhận (outline vs filled).

Khi bấm Sửa: hiện dropdown môn CS101/MATH201 + date picker giả.

Nút Chấp nhận → data-next="02-week-priority"
Nút Từ chối → tooltip "Hệ thống ghi nhận: đề xuất không phù hợp" (implicit user feedback)

Rationale note: email có thể nhầm môn → cần review + bằng chứng trước khi lưu task.
```

---

### `02-week-priority` — S2 Ưu tiên deadline tuần

```
[Tiếp tục từ master prompt]

Tạo màn 02-week-priority — S2 Nhiều deadline trong tuần, AI gợi ý thứ tự ưu tiên.

Bối cảnh: Tuần này có 4 deadline; AI đề xuất thứ tự học dựa trên deadline + độ khó + trọng số môn.

UI:
- Header: "Ưu tiên tuần 22–28/06"
- Banner AI: "Đề xuất thứ tự — bạn có thể kéo thả hoặc chỉnh tiêu chí" [Act]

Danh sách 4 task (có thể drag reorder giả bằng nút ↑↓):
1. Nộp Bài tập 3 — CS101 — 25/06 — Ưu tiên cao
2. Bài kiểm tra giữa kỳ — MATH201 — 26/06 — Ưu tiên cao
3. Đọc chương 5 — CS101 — 27/06 — Trung bình
4. Bài tập nhóm — ENG102 — 28/06 — Thấp

Panel "Tiêu chí ưu tiên" (explainability):
- Slider hoặc weight bars: Deadline gần (40%) | Trọng số môn (30%) | Độ khó ước tính (30%)
- Mỗi task có tooltip "Vì sao ở vị trí này" — trích nguồn (email / lịch / suy luận)

Nút "Áp dụng" [Act] → data-next="03-review-facts"
Nút "Đặt lại mặc định"

Lớp bằng chứng: icon email bên task có nguồn email, icon brain bên suy luận AI.

Rationale note: Act vì rủi ro thấp (chỉ sắp xếp gợi ý); user luôn override được.
```

---

### `03-review-facts` — After action (fact vs inference)

```
[Tiếp tục từ master prompt]

Tạo màn 03-review-facts — Màn review sau khi AI tạo task và sắp ưu tiên.

Bối cảnh: User vừa chấp nhận đề xuất; cần xem lại fact vs inference trước khi tiếp tục.

UI:
- Tiêu đề: "Xem lại những gì AI đã làm"
- 2 cột hoặc 2 section:
  **Đã xác nhận (Fact)**
  - Email nhận 20/06 từ nguyenvana@university.edu
  - Deadline 25/06 ghi trong email
  **Suy luận AI (Inference)**
  - Môn CS101 (từ tiêu đề email)
  - Ưu tiên cao (dựa tiêu chí deadline)
- Mỗi inference có icon cảnh báo nhỏ + "Có thể cần kiểm tra"
- Nút "Hoàn tác tạo task" (undo) — khi bấm hiện toast implicit feedback:
  "Hệ thống ghi nhận: user hoàn tác — có thể đề xuất chưa phù hợp"
- Nút "Tiếp tục" → data-next="03-draft-email"
- Link phụ: "Báo sai thông tin" → data-next="04-wrong-deadline"

Banner [Explicit System → User]: "2 fact · 2 suy luận — kiểm tra trước khi tin hoàn toàn"

Rationale note: phân tách fact/inference giúp user phát hiện lỗi sớm (chuẩn bị S6).
```

---

### `03-draft-email` — S9 Soạn email giảng viên (Agency)

```
[Tiếp tục từ master prompt]

Tạo màn 03-draft-email — S9 Soạn email nháp xin dời deadline.

Bối cảnh: Sinh viên muốn nhờ AI soạn email xin dời deadline CS101; AI KHÔNG được gửi thay.

UI:
- Tiêu đề: "Soạn email nháp"
- Badge lớn [Don't Act]: "AI không gửi email thay bạn"
- Form email giả:
  • Đến: nguyenvana@university.edu (readonly)
  • Tiêu đề: "Xin gia hạn Bài tập 3 — CS101" (editable)
  • Nội dung: đoạn nháp AI viết sẵn (textarea editable), tone lịch sự, ngắn
- Panel "AI dùng thông tin": deadline 25/06, tên môn CS101 (có link xem nguồn)
- Checkbox bắt buộc: "Tôi đã đọc và chỉnh sửa nội dung"
- Nút chính [Ask]: "Sao chép & mở email" (không có nút "Gửi")
- Nút phụ: "Lưu nháp" | "Hủy"
- Sau bấm sao chép: toast "Đã sao chép — mở ứng dụng email của bạn để gửi"

Trạng thái: "Nháp — chưa gửi" (badge xám, khác "Đã gửi")

Nút tiếp demo → data-next="04-wrong-deadline"

Rationale note: rủi ro quan hệ giảng viên; Don't Act gửi; Ask trước khi user tự gửi.
```

---

### `04-wrong-deadline` — S6 Phát hiện gán nhầm môn

```
[Tiếp tục từ master prompt]

Tạo màn 04-wrong-deadline — S6 User phát hiện AI gán nhầm deadline môn.

Bối cảnh: Task "Nộp Bài tập 3" đang gán CS101 + deadline 25/06, nhưng email thực ra
từ tranthib@university.edu về MATH201.

UI:
- Card task bị lỗi (viền đỏ nhạt):
  • Hiện tại: CS101 — 25/06
  • Email nguồn: tranthib@university.edu (MATH201) ← highlight mâu thuẫn
- Callout đỏ: "Môn học không khớp email nguồn"
- Panel bằng chứng: so sánh 2 cột "AI gán" vs "Email thực tế"
- Nút "Báo sai" [explicit user feedback] → data-next="04-error-feedback"
- Nút "Tự sửa" → inline edit
- Nút "Bỏ qua" (cho phép user ignore — nhưng có cảnh báo nhỏ)

Trạng thái AI: "Đề xuất có thể sai — cần xác nhận"

Rationale note: hậu quả nếu sai = học nhầm môn, bỏ lỡ deadline MATH201 thật.
```

---

### `04-error-feedback` — S6 + Explicit User → System feedback

```
[Tiếp tục từ master prompt]

Tạo màn 04-error-feedback — Form báo sai loại lỗi (Explicit User → System).

Bối cảnh: User bấm "Báo sai" từ màn wrong-deadline; cần feedback cụ thể, không chỉ dislike.

UI:
- Tiêu đề: "Giúp StudyMate hiểu lỗi"
- Radio buttons loại lỗi (chọn 1):
  • Sai môn học ← pre-selected
  • Sai deadline
  • Không phải task (chỉ là thông báo)
  • Email không liên quan học tập
  • Khác
- Textarea tùy chọn: "Mô tả thêm" (placeholder: "Email này của thầy B, môn MATH201")
- Checkbox: "Gửi kèm trích email" (checked mặc định)
- Nút "Gửi phản hồi" → data-next="04-recovery"
- Nút "Hủy" → quay 04-wrong-deadline

Không có nút thumbs down đơn thuần — phải chọn loại lỗi.

Banner: "Phản hồi của bạn giúp AI sửa ngay, không chỉ ghi nhận"

Rationale note: structured feedback → recovery có hướng; tránh black-box dislike.
```

---

### `04-recovery` — S6 Recovery hoàn chỉnh

```
[Tiếp tục từ master prompt]

Tạo màn 04-recovery — S6 Recovery sau khi báo sai môn học.

Bối cảnh: User đã báo "Sai môn học" — email thực ra về MATH201, không phải CS101.

UI — flow 3 bước trên 1 màn (step indicator 1→2→3):

**Bước 1 — Xác nhận hiểu (Explicit System → User)**
- "Mình hiểu: deadline này thuộc MATH201, không phải CS101"
- Hiển thị thay đổi: CS101 → MATH201, giảng viên Nguyễn Văn A → Trần Thị B

**Bước 2 — Đề xuất khôi phục [Act]**
- Di chuyển task sang MATH201 (checked)
- Cập nhật ưu tiên tuần (MATH201 lên #1) (checked)
- Hoàn tác task CS101 trùng lặp (unchecked, optional)
- Nút "Áp dụng sửa"

**Bước 3 — Ghi nhớ**
- Checkbox: "Ghi nhớ: email từ tranthib@university.edu thường là MATH201"
- Text nhỏ: "Bạn có thể xóa ghi nhớ trong Cài đặt"

Nút "Hoàn tất" → data-next="02-week-priority" (phiên bản đã sửa — hiện MATH201 #1)

Phải thể hiện user TIẾP TỤC mục tiêu (quay lại ưu tiên tuần), không dừng ở "đã ghi nhận".

Toast khi hoàn tất: "Đã sửa · Ưu tiên tuần cập nhật"

Rationale note: vòng recovery đầy đủ: phát hiện → feedback → xác nhận → sửa → tiếp tục.
```

---

### `05-feedback-matrix` — Ma trận feedback 2x2

```
[Tiếp tục từ master prompt]

Tạo màn 05-feedback-matrix — Tổng hợp 4 ô ma trận feedback 2x2 với ví dụ UI thật.

Bối cảnh: Trang tổng hợp cho người chấm, mỗi ô có screenshot/mock mini + mô tả.

UI — Grid 2x2:

| | System → User | User → System |
|---|---|---|
| Explicit | Banner trạng thái "AI đề xuất — chưa lưu" (từ 02-task-proposal) | Form báo loại lỗi (từ 04-error-feedback) |
| Implicit | Nút "Xem nguồn" nổi bật hơn "Chấp nhận" | Toast khi hoàn tác / sửa tay (từ 03-review-facts) |

Mỗi ô:
- Tiêu đề ô (tiếng Việt)
- Mini UI mock (div thu nhỏ, không cần ảnh)
- 1–2 câu rationale
- Link "Xem màn đầy đủ" → data-next tương ứng

Footer: "Tiếp theo: Design rationale" → data-next="06-rationale"

Rationale note (sticky): giải thích vì sao cần cả 4 ô, không chỉ explicit user feedback.
```

---

### `06-rationale` — Design decisions chính

```
[Tiếp tục từ master prompt]

Tạo màn 06-rationale — Trang tổng hợp design rationale chính.

Bối cảnh: Tài liệu đính kèm prototype cho người chấm (trả lời 10 câu hỏi PDF mục 7.2 + feedback mục 9).

UI — Danh sách accordion hoặc sections:

1. **S0 Onboarding** — Vì sao 3 bước thay vì form? Progressive disclosure.
2. **S1 Kết nối dữ liệu** — Granular consent; Ask trước khi đọc email.
3. **S4 Task từ email** — Bằng chứng + fact/inference; Ask trước khi lưu.
4. **S2 Ưu tiên tuần** — Act vì dễ sửa; explainability sliders.
5. **S9 Soạn email** — Don't Act gửi; chỉ nháp + Ask copy.
6. **S6 Recovery** — Structured error feedback → sửa → tiếp tục mục tiêu.
7. **Feedback 2x2** — Bảng tóm tắt 4 ô + ví dụ cụ thể.

Mỗi section 3–5 câu, có tag [Act]/[Ask]/[Don't Act].

Nút "Xem demo" → data-next="07-demo-path"

Style: readable, không quá dày; có mục lục anchor links phía trên.
```

---

### `07-demo-path` — (Tạo bằng prompt stitch, mục 3)

Màn này được tạo bằng **Prompt nối prototype** bên dưới, không chạy riêng lẻ trừ khi muốn SPA đơn giản.

---

## 3. Prompt nối prototype (stitch)

Chạy sau khi đã có các file HTML riêng lẻ:

```
[Tiếp tục từ master prompt]

Tôi đã có các file HTML riêng lẻ trong thư mục prototype/:
00-flow-map, 01-onboarding, 01b-connect-data, 02-email-scanning, 02-task-proposal,
02-week-priority, 03-review-facts, 03-draft-email, 04-wrong-deadline,
04-error-feedback, 04-recovery, 05-feedback-matrix, 06-rationale.

Hãy tạo file 07-demo-path.html (hoặc index.html) nối tất cả màn theo demo script 5 phút:

| Thời gian | Nội dung |
|-----------|----------|
| 0:00 | Flow map (00) |
| 0:30 | Onboarding (01 → 01b) |
| 1:15 | Email scan → Task proposal → Week priority (02-*) |
| 2:15 | Review facts → Draft email (03-*) |
| 2:45 | Wrong deadline → Error feedback → Recovery (04-*) |
| 3:45 | Feedback matrix (05) |
| 4:30 | Rationale highlights (06) |

Yêu cầu kỹ thuật:
- Single-page app: mỗi màn là section show/hide HOẶC iframe embed — chọn cách đơn giản hơn
- Bottom bar cố định (chỉ demo mode):
  • "Demo tiếp theo" theo script
  • "Màn trước" / "Màn sau"
  • Đồng hồ elapsed giả (0:00 → 5:00)
- Sidebar hoặc drawer: danh sách tất cả màn để jump
- Mỗi màn giữ sticky rationale note
- Map data-next="..." sang chuyển section tương ứng
- Responsive 375px, có thể xem trên desktop (centered phone frame)

Output: 1 file HTML self-contained có thể mở trực tiếp trong browser, không cần server.
```

---

## 4. Prompt chỉnh sửa nhanh

Copy khi cần tinh chỉnh sau khi đã có prototype:

### Loading & trạng thái AI

```
Trên màn 02-email-scanning, thêm trạng thái loading chi tiết hơn:
thanh tiến độ %, text đổi "Đang phân tích 2/5 email", highlight email đang xử lý.
Giữ mobile-first 375px và sticky rationale note.
```

### Fact vs inference

```
Trên màn 02-task-proposal, làm nổi bật hơn sự khác biệt fact vs inference:
màu xanh cho "Từ email", màu tím cho "Suy luận AI", thêm icon và tooltip giải thích.
Nút "Xem nguồn email" phải nổi bật hơn "Chấp nhận".
```

### Implicit user feedback

```
Thêm implicit user feedback: khi user bấm Hoàn tác hoặc Từ chối đề xuất,
hiện toast 3 giây: "Hệ thống ghi nhận: có thể đề xuất chưa phù hợp".
Ghi chú trong rationale note màn đó.
```

### Recovery path

```
Kiểm tra màn 04-recovery: đảm bảo sau "Hoàn tất" user quay lại 02-week-priority
với MATH201 ở vị trí #1, không có dead-end "đã ghi nhận lỗi".
Thêm animation nhỏ khi task đổi môn.
```

### Act / Ask / Don't Act

```
Rà soát toàn bộ prototype: mỗi hành động AI phải có nhãn [Act], [Ask], hoặc [Don't Act].
Liệt kê màn nào còn thiếu và bổ sung badge + giải thích 1 dòng trong rationale note.
```

### Feedback 2x2

```
Bổ sung đủ 4 ô ma trận feedback 2x2:
- Explicit User→System: form loại lỗi (04-error-feedback)
- Implicit User→System: toast hoàn tác/sửa tay
- Explicit System→User: banner trạng thái AI
- Implicit System→User: affordance UI (nút review, draft vs sent)
Cập nhật màn 05-feedback-matrix nếu thiếu ô nào.
```

### Accessibility

```
Cải thiện accessibility toàn prototype: focus ring rõ, aria-label cho nút,
contrast tối thiểu WCAG AA, kích thước nút >= 44px. Giữ tiếng Việt UI.
```

### Chuyển sang React / Figma

```
Chuyển màn [TÊN MÀN] sang [React component / Figma frame description]:
giữ nguyên nội dung tiếng Việt, logic Act/Ask/Don't Act, và sticky rationale note.
Liệt kê props/state cần thiết nếu dùng React.
```

---

## 5. Mapping Act / Ask / Don't Act (tham chiếu)

| Hành động | Mức | Màn |
|-----------|-----|-----|
| Gợi ý thứ tự học / cập nhật ưu tiên | **Act** | 02-week-priority, 04-recovery |
| Kết nối email/lịch | **Ask** | 01b-connect-data |
| Tạo task từ email (chấp nhận) | **Ask** | 02-task-proposal |
| Soạn email nháp | **Ask** | 03-draft-email |
| Gửi email cho giảng viên | **Don't Act** | 03-draft-email |

---

## 6. Checklist trước khi nộp

- [ ] Onboarding S0 (`01-onboarding`)
- [ ] >= 4 kịch bản ngoài onboarding (S1, S4, S2, S6, S9)
- [ ] Vòng đời: Onboarding → During → After → Feedback
- [ ] Đủ Act / Ask / Don't Act trên UI
- [ ] >= 1 vòng recovery hoàn chỉnh (04-wrong → 04-error → 04-recovery)
- [ ] Đủ 4 ô feedback 2x2 (`05-feedback-matrix`)
- [ ] >= 1 lớp bằng chứng (email nguồn S4, tiêu chí ưu tiên S2)
- [ ] Rationale note trên mỗi màn quan trọng + trang `06-rationale`
- [ ] Demo path 5 phút (`07-demo-path`)
