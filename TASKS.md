# TASKS — StudyMate AI (Day 18 Lab)

Checklist tuần tự để hoàn thành bài lab **Human-Centered AI Design — AI Personal Assistant for Students**.

**Lát cắt:** AI đọc email trường → tạo nhiệm vụ học tập → sắp xếp ưu tiên tuần → nhắc việc & khôi phục khi sai.

**Công cụ:** HTML clickable trong [`prototype/`](prototype/) — prompt copy-paste tại [`PROMPTS.md`](PROMPTS.md).

**Timeline tổng:** ~120 phút thiết kế + prototype.

---

## Phase 0 — Chuẩn bị (trước khi prototype)

- [x] Xác nhận nhóm 3 người và phân vai (research, UI, rationale/demo)
- [x] Chốt persona sinh viên: **Minh**, đại học năm 2, email `minh.nguyen@student.university.edu`, dùng email trường + lịch học
- [x] Viết scope (xem mục Scope bên dưới)
- [x] Chọn công cụ prototype: **HTML clickable** (mobile-first 375px)
- [x] Tạo flow map tổng: Onboarding → During → After → Feedback — màn [`00-flow-map.html`](prototype/00-flow-map.html)

### Scope

**User:** Sinh viên đại học năm 2, nhiều deadline từ email trường, khó theo dõi thủ công.

**Pain point:** Email trường lẫn lộn môn học; deadline bị bỏ sót; ưu tiên tuần không rõ; sợ AI gán nhầm môn.

**Lát cắt:** AI đọc email → đề xuất task → sắp xếp ưu tiên tuần → khôi phục khi gán nhầm môn.

**Out-of-scope:** Chat hỏi–đáp chung, nộp bài tự động, đăng ký môn, gửi email thay user.

---

## Phase 1 — Onboarding (S0) ~15 phút

- [x] Thiết kế màn đầu: AI hỗ trợ gì / không làm gì / cần quyền gì — [`01-onboarding.html`](prototype/01-onboarding.html)
- [x] Thiết kế cách bắt đầu không form dài (3 bước progressive disclosure)
- [x] Thiết kế kiểm soát: bỏ qua, thu hồi quyền, điều chỉnh sau
- [x] Viết design rationale cho S0 — sticky note + [`06-rationale.html`](prototype/06-rationale.html)

---

## Phase 2 — Luồng chính During (S1, S4, S2) ~35 phút

- [x] **S1:** Flow xin kết nối email/lịch — [`01b-connect-data.html`](prototype/01b-connect-data.html) `[Ask]`
- [x] **S4:** Flow đọc email → đề xuất task — [`02-email-scanning.html`](prototype/02-email-scanning.html), [`02-task-proposal.html`](prototype/02-task-proposal.html) `[Ask]`
- [x] **S2:** Flow ưu tiên deadline tuần — [`02-week-priority.html`](prototype/02-week-priority.html) `[Act]`
- [x] Thể hiện trạng thái AI: đang xử lý, hỏi thêm, đề xuất, tiến độ
- [x] Gán Act/Ask/Don't Act cho từng hành động trong 3 flow
- [x] Viết rationale cho S1, S4, S2

---

## Phase 3 — After action & Agency (S9) ~15 phút

- [x] Màn review fact vs inference — [`03-review-facts.html`](prototype/03-review-facts.html)
- [x] **S9:** Soạn email nháp xin dời deadline — [`03-draft-email.html`](prototype/03-draft-email.html) `[Don't Act]` gửi, `[Ask]` copy
- [x] Thiết kế undo / từ chối / lưu nháp
- [x] Viết rationale cho S9 (rủi ro quan hệ giảng viên)

---

## Phase 4 — Failure & Recovery (S6) ~30 phút

- [x] **S6:** AI gán nhầm CS101 thay vì MATH201 — [`04-wrong-deadline.html`](prototype/04-wrong-deadline.html)
- [x] Vòng recovery: phát hiện → feedback cụ thể → xác nhận → sửa → tiếp tục — [`04-error-feedback.html`](prototype/04-error-feedback.html), [`04-recovery.html`](prototype/04-recovery.html)
- [x] Đường khôi phục: sửa môn, hoàn tác task, cập nhật ưu tiên
- [x] Viết rationale cho S6

---

## Phase 5 — Feedback hai chiều (ma trận 2×2) ~20 phút

- [x] **Explicit User → System:** form báo loại lỗi — `04-error-feedback`
- [x] **Implicit User → System:** toast hoàn tác / từ chối — `03-review-facts`, `02-task-proposal`
- [x] **Explicit System → User:** banner trạng thái AI — nhiều màn
- [x] **Implicit System → User:** nút "Xem nguồn" nổi bật, badge Nháp vs Đã gửi
- [x] Trang tổng hợp — [`05-feedback-matrix.html`](prototype/05-feedback-matrix.html)
- [x] Viết rationale cho cả 4 ô ma trận

---

## Phase 6 — Tổ chức prototype & nộp bài ~15 phút

- [x] Sắp xếp prototype theo cấu trúc PDF mục 16 (`00`–`07`)
- [x] Nối các frame thành prototype clickable — [`07-demo-path.html`](prototype/07-demo-path.html)
- [x] Tạo demo path 5 phút (script bên dưới)
- [x] Kiểm tra checklist tối thiểu (mục Checklist đạt)
- [x] README với link tới TASKS, PROMPTS, prototype — [`README.md`](README.md)
- [ ] Cấp quyền xem link prototype (nếu host online)

---

## Phase 7 — Demo & tự đánh giá

- [x] Tài liệu tập demo: [`DEMO_REHEARSAL.md`](DEMO_REHEARSAL.md)
- [x] Rà soát prototype theo checklist PDF (xem DEMO_REHEARSAL.md mục "Kết quả rà soát")
- [ ] Tập demo 5 phút trực tiếp trước lớp (mở [`prototype/07-demo-path.html`](prototype/07-demo-path.html))
- [x] Tự chấm theo 5 tiêu chí (bảng bên dưới — điều chỉnh sau khi tập live)

---

## Demo script 5 phút

Mở [`prototype/07-demo-path.html`](prototype/07-demo-path.html) và dùng nút **Demo tiếp theo**.

| Thời gian | Nội dung | Màn |
|-----------|----------|-----|
| 0:00 | Giới thiệu flow map 4 giai đoạn | `00-flow-map` |
| 0:30 | Onboarding 3 bước + kết nối dữ liệu | `01-onboarding` → `01b-connect-data` |
| 1:15 | Quét email → đề xuất task → ưu tiên tuần | `02-email-scanning` → `02-task-proposal` → `02-week-priority` |
| 2:15 | Review fact/inference → soạn email nháp | `03-review-facts` → `03-draft-email` |
| 2:45 | Phát hiện gán nhầm → báo lỗi → recovery | `04-wrong-deadline` → `04-error-feedback` → `04-recovery` |
| 3:45 | Ma trận feedback 2×2 | `05-feedback-matrix` |
| 4:30 | Design rationale highlights | `06-rationale` |

**Điểm nhấn khi demo:**
1. Không phải chatbot — có trạng thái AI và quyền kiểm soát
2. Bằng chứng email + fact vs inference trước khi chấp nhận task
3. Don't Act gửi email — chỉ nháp
4. Recovery hoàn chỉnh: không dừng ở "đã ghi nhận lỗi"
5. Đủ 4 ô feedback 2×2

---

## Checklist đạt tối thiểu (PDF mục 19)

- [x] Onboarding lần đầu (S0)
- [x] ≥ 4 kịch bản ngoài onboarding (S1, S4, S2, S6, S9 = 5)
- [x] Vòng đời: Onboarding → During → After → Feedback
- [x] Đủ Act / Ask / Don't Act
- [x] ≥ 1 vòng feedback + recovery hoàn chỉnh (S6)
- [x] Đủ 4 loại feedback 2×2
- [x] ≥ 1 lớp bằng chứng (S4 email nguồn, S2 tiêu chí ưu tiên)
- [x] Rationale đặt cạnh mỗi flow quan trọng

---

## Mapping Act / Ask / Don't Act

| Hành động | Mức | Màn | Lý do |
|-----------|-----|-----|-------|
| Gợi ý thứ tự học / cập nhật ưu tiên | **Act** | `02-week-priority`, `04-recovery` | Rủi ro thấp, dễ sửa |
| Kết nối email/lịch | **Ask** | `01b-connect-data` | Cần consent |
| Tạo task từ email (chấp nhận) | **Ask** | `02-task-proposal` | Tác động dữ liệu cá nhân |
| Soạn email nháp | **Ask** | `03-draft-email` | User xác nhận trước khi gửi |
| Gửi email cho giảng viên | **Don't Act** | `03-draft-email` | Rủi ro cao, khó hoàn tác |

---

## Tự chấm điểm (5 tiêu chí)

| Tiêu chí | Trọng số | Tự chấm (1–5) | Ghi chú |
|----------|----------|---------------|---------|
| Rationale | 30% | 5 | Sticky note mọi màn + trang 06-rationale 7 section |
| Failure & Recovery | 25% | 5 | Vòng S6 đầy đủ 3 màn, quay lại ưu tiên tuần |
| Agency | 20% | 5 | Don't Act gửi email, granular consent, bỏ qua/undo |
| Feedback 2×2 | 15% | 5 | Trang 05 + ví dụ implicit/explicit trên UI |
| Prototype | 10% | 4 | Clickable HTML, mobile-first; có thể polish animation |

**Điểm ước tính:** (5×0.30 + 5×0.25 + 5×0.20 + 5×0.15 + 4×0.10) × 20 = **98/100**

---

## Lỗi cần tránh

- Chỉ làm chatbot hỏi–đáp
- Nút "báo lỗi" mà không có recovery
- Cảnh báo "AI có thể sai" thay cho bằng chứng + quyền kiểm soát
- UI đẹp nhưng thiếu trạng thái và nhánh lỗi
- Recovery dừng ở "đã ghi nhận lỗi"

---

## Kịch bản đã chọn

| # | Kịch bản | File prototype |
|---|----------|----------------|
| S0 | First-time Onboarding | `01-onboarding` |
| S1 | Kết nối dữ liệu học tập | `01b-connect-data` |
| S4 | Tạo nhiệm vụ từ email | `02-email-scanning`, `02-task-proposal` |
| S2 | Nhiều deadline trong tuần | `02-week-priority` |
| S6 | Gán nhầm deadline môn học | `04-wrong-deadline`, `04-error-feedback`, `04-recovery` |
| S9 | Soạn email cho giảng viên | `03-draft-email` |

*Dự phòng:* S3 (kế hoạch học tối nay), S8 (nhắc việc đã xử lý) — thay S2/S6 nếu nhóm muốn.
