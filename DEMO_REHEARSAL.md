# Demo Rehearsal & Self-Assessment — StudyMate AI

Hướng dẫn tập demo 5 phút và tự chấm điểm theo tiêu chí PDF.

## Chuẩn bị trước khi demo

1. Mở [`prototype/07-demo-path.html`](prototype/07-demo-path.html) trên trình duyệt (Chrome/Edge).
2. Thu nhỏ cửa sổ hoặc dùng chế độ phone frame sẵn có.
3. Đọc script trong [`TASKS.md`](TASKS.md) mục "Demo script 5 phút".
4. Phân vai nhóm 3 người: người demo UI, người giải thích rationale, người nhấn mạnh Act/Ask/Don't Act.

## Script demo (5 phút)

| Thời gian | Nói gì (gợi ý) | Màn |
|-----------|----------------|-----|
| 0:00 | "Đây là StudyMate AI — lát cắt đọc email trường, tạo task, ưu tiên tuần, recovery khi sai." | Flow map |
| 0:30 | "Onboarding 3 bước — không form dài. User biết AI làm gì / không làm gì trước khi cấp quyền." | Onboarding → Connect |
| 1:15 | "AI đọc email minh bạch, đề xuất task có bằng chứng. Fact vs inference trước khi chấp nhận." | Email scan → Task → Priority |
| 2:15 | "Review sau hành động. Soạn email nháp — AI không gửi thay (Don't Act)." | Review → Draft email |
| 2:45 | "User phát hiện gán nhầm môn. Báo lỗi cụ thể → recovery → tiếp tục ưu tiên tuần." | Wrong → Error → Recovery |
| 3:45 | "Đủ 4 ô feedback 2×2 — explicit và implicit." | Feedback matrix |
| 4:30 | "Tóm tắt design rationale chính." | Rationale |

## Checklist trong lúc demo

- [ ] Nhấn mạnh: **không phải chatbot**
- [ ] Chỉ ra **sticky rationale note** trên màn
- [ ] Chỉ ra nhãn **[Act] / [Ask] / [Don't Act]**
- [ ] Chỉ ra **panel bằng chứng** (S4) và **sliders tiêu chí** (S2)
- [ ] Recovery **không dừng** ở "đã ghi nhận"
- [ ] Email: badge **Nháp — chưa gửi**

## Tự chấm điểm (1–5 mỗi tiêu chí)

| Tiêu chí | Trọng số | Điểm (1–5) | Ghi chú |
|----------|----------|------------|---------|
| **Rationale** | 30% | | Sticky notes + trang 06-rationale đủ 7 section? |
| **Failure & Recovery** | 25% | | Vòng S6: phát hiện → form lỗi → xác nhận → sửa → tiếp tục? |
| **Agency** | 20% | | Don't Act gửi email, granular consent, bỏ qua/sửa/undo? |
| **Feedback 2×2** | 15% | | Đủ 4 ô với ví dụ UI thật trên prototype? |
| **Prototype** | 10% | | Clickable, mobile-first, trạng thái AI rõ? |

**Công thức:** `(Rationale×0.30 + Failure×0.25 + Agency×0.20 + Feedback×0.15 + Prototype×0.10) × 20` → thang 100 (nếu mỗi tiêu chí 1–5).

## Kết quả rà soát prototype (đã kiểm tra)

| Yêu cầu | Trạng thái | Vị trí |
|---------|------------|--------|
| Act / Ask / Don't Act | ✓ | Badges trên mọi màn chính |
| Explicit User→System | ✓ | `04-error-feedback` |
| Implicit User→System | ✓ | Toast hoàn tác/từ chối |
| Explicit System→User | ✓ | Banner trạng thái AI |
| Implicit System→User | ✓ | Nút Xem nguồn, badge Nháp |
| Recovery hoàn chỉnh | ✓ | `04-recovery` → `02-week-priority?recovered=1` |
| Lớp bằng chứng | ✓ | Panel email S4, sliders S2 |
| Rationale | ✓ | Sticky notes + `06-rationale` |

## Sau khi tập

1. Ghi lại điểm tự chấm vào [`TASKS.md`](TASKS.md) bảng "Tự chấm điểm".
2. Đánh dấu Phase 7 trong TASKS.md khi đã tập xong.
3. Host prototype (GitHub Pages / Netlify) nếu cần link nộp bài.
