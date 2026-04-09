# SPEC Final — Nhom16-C401-Day05

## Track: VinUni / VinSchool

## Product: AI Tutor — Trợ lý học tập thông minh (Q&A nội bộ)

---

## 0. TL;DR

Chúng tôi xây dựng một AI Tutor giúp sinh viên/học sinh giải đáp câu hỏi học tập dựa trên tài liệu nội bộ (slides, notes, syllabus, bài giảng).

Hiện tại, người học thường mất nhiều thời gian để:

* Tìm lại tài liệu
* Hiểu lại kiến thức
* Chờ phản hồi từ giảng viên hoặc bạn bè

AI Tutor cho phép:

* Hỏi trực tiếp câu hỏi
* Nhận câu trả lời chính xác từ tài liệu
* Được giải thích rõ ràng + ví dụ minh họa
* Học liên tục 24/7

👉 Đây là **augmentation**, không phải automation:
AI không học thay người học — mà **giúp người học hiểu nhanh hơn và chủ động hơn**

---

## 1. Problem Statement

Trong môi trường học tập tại VinUni/VinSchool:

### 📌 Thực trạng

* Sinh viên:

  * Không hiểu bài ngay trên lớp
  * Không nhớ nội dung đã học nằm ở đâu
  * Ngại hỏi giảng viên (tâm lý phổ biến)

* Hệ thống hiện tại:

  * Tài liệu phân tán (slides, LMS, PDF)
  * Không có search thông minh
  * Không có trợ lý học tập real-time

---

### 📌 Hậu quả

* Mất 10–30 phút chỉ để tìm lại kiến thức
* Hiểu sai hoặc hiểu không đầy đủ
* Giảm hiệu quả học tập
* Phụ thuộc vào TA / bạn bè

---

👉 **Vấn đề cốt lõi:**

> Người học không có một trợ lý thông minh giúp họ truy xuất và hiểu kiến thức ngay lập tức

---

### 🔥 Insight quan trọng

> Đây không phải là “thiếu tài liệu”
> 👉 mà là **thiếu khả năng truy cập và hiểu tài liệu đúng cách**

---

## 2. Solution Overview

### 🎯 Giải pháp

AI Tutor tích hợp vào hệ thống học tập (LMS / web app):

1. User nhập câu hỏi tự nhiên
2. Hệ thống truy xuất tài liệu liên quan (RAG)
3. AI trả lời với:

   * Giải thích rõ ràng
   * Ví dụ minh họa
   * Trích dẫn nguồn (slide/bài giảng)

---

### 🎯 Use cases chính

* Hỏi khái niệm (VD: “Gradient descent là gì?”)
* Hỏi cách giải bài
* Ôn tập trước kỳ thi
* Hỏi nhanh khi làm bài tập

---

### 🎯 Nguyên tắc thiết kế

* Không trả lời nếu không có nguồn
* Luôn hiển thị citation
* Không tạo “false confidence”
* Không làm bài hộ hoàn toàn
* Ưu tiên clarity > complexity

---

## 3. AI Product Canvas

### Value

* Tiết kiệm thời gian tìm kiếm
* Tăng tốc độ hiểu bài
* Cá nhân hóa trải nghiệm học
* Học mọi lúc (24/7)

---

### Trust

Domain giáo dục có rủi ro:

* Nếu AI sai → học sai kiến thức

→ Cần:

* RAG (chỉ trả lời từ tài liệu thật)
* Citation rõ ràng
* Confidence level
* Option xem tài liệu gốc

---

### Feasibility

* LLM + RAG trên tài liệu nội bộ
* Data: PDF, slides, lecture notes
* Latency < 5s
* Cost thấp (~0.003–0.01$/query)

---

### 🔥 Insight

> AI Tutor không cần “biết mọi thứ”
> 👉 Chỉ cần **biết đúng những gì trường dạy**

---

## 4. User Flows (4 Paths)

### ✅ 1. Happy Path

* User: “Backpropagation là gì?”
* AI:

  * Giải thích đơn giản
  * Có ví dụ
  * Có citation từ slide

👉 User hiểu ngay trong 1 lần hỏi

---

### ⚠️ 2. Low-confidence Path

* User hỏi mơ hồ: “Cái này là gì?”

AI:

* Hỏi lại:

  * “Bạn đang hỏi phần nào?”
* Gợi ý topic liên quan

👉 Giảm sai hiểu context

---

### ❌ 3. Failure Path

* AI trả lời sai / thiếu

Recovery:

* User:

  * Xem tài liệu gốc
  * Hỏi lại
* System log lại lỗi

---

### 🔁 4. Correction Path

* User: “Giải thích chưa rõ”

System:

* Trả lời lại theo cách khác
* Thêm ví dụ
* Đơn giản hóa nội dung

---

## 5. Learning Signals

### Primary Signals

* User feedback (👍 / 👎)
* Số lần hỏi lại
* Click vào tài liệu nguồn

---

### Secondary Signals

* Thời gian hiểu bài (giảm số lần hỏi)
* Session length
* Topic frequency

---

### 🔥 Insight

> Đây là dữ liệu hành vi học tập thực
> 👉 có thể dùng để:

* Cá nhân hóa AI
* Gợi ý học tập
* Xây dựng learning path

---

## 6. Hướng đi chính

### Prototype

* Chatbot Q&A
* Input: câu hỏi tự nhiên
* Output:

  * Answer
  * Explanation
  * Citation
  * (Optional) example

---

### Evaluation

* Answer accuracy ≥ 80%
* Citation accuracy ≥ 90%
* Hallucination < 5%

---

### Main Failure Mode

* Hallucination (trả lời ngoài tài liệu)
* Hiểu sai câu hỏi (context mismatch)

---

## 7. Evaluation Metrics

### 🎯 Objective

**Maximize correctness & trust, minimize hallucination**

---

### Metrics

| Metric             | Target | Threshold      |
| ------------------ | ------ | -------------- |
| Answer Accuracy    | ≥ 80%  | < 65% = fail   |
| Citation Accuracy  | ≥ 90%  | < 70% = fail   |
| Hallucination Rate | < 5%   | > 10% = fail   |
| Re-ask Rate        | < 30%  | > 50% = UX kém |

---

### Trade-off

* Trả lời ít nhưng đúng > trả lời nhiều nhưng sai
* Trust > coverage

---

## 8. Failure Modes & Mitigation

### ❗ Hallucination (nguy hiểm nhất)

Mitigation:

* Bắt buộc RAG
* Không có nguồn → từ chối trả lời
* Hiển thị citation

---

### ❗ Over-helping (làm hộ bài)

Mitigation:

* Giải thích từng bước
* Không đưa đáp án trực tiếp

---

### ❗ Context mismatch

Mitigation:

* Clarifying questions
* Topic suggestion

---

### ❗ Outdated tài liệu

Mitigation:

* Sync mỗi kỳ học
* Version control tài liệu

---

## 9. System Design

### Architecture

* LLM (reasoning + explanation)
* RAG (retrieval)
* Embedding database
* Citation module
* Feedback logging system

---

### Flow

User question
→ Embed query
→ Retrieve documents
→ LLM generate answer
→ Attach citation
→ Return output

---

### 🔥 Improvement (future)

* Personalized tutor (adaptive learning)
* Quiz generation
* Knowledge gap detection

---

## 10. UX Principles

1. Luôn hiển thị nguồn
2. Giải thích đơn giản, dễ hiểu
3. Không overwhelm thông tin
4. Hỗ trợ học, không thay thế học
5. Response < 5s
6. Có khả năng hỏi lại dễ dàng

---

## 11. ROI Estimation

| Scenario     | Users/day | Accuracy | Benefit             |
| ------------ | --------- | -------- | ------------------- |
| Conservative | 50        | 70%      | Hỗ trợ cơ bản       |
| Realistic    | 200       | 80%      | Giảm phụ thuộc TA   |
| Optimistic   | 500       | 90%      | Scale toàn hệ thống |

---

### 📌 Value dài hạn

* Giảm workload giảng viên / TA
* Tăng chất lượng học tập
* Tạo nền tảng AI education

---

## 12. Kill Criteria

* Hallucination > 10% → STOP
* Accuracy < 65% → Rebuild
* User dissatisfaction > 50% → Redesign

---

## 13. Why This Matters

Chúng tôi không thay thế giảng viên.

👉 Chúng tôi giúp sinh viên:

* Hiểu bài nhanh hơn
* Học chủ động hơn
* Không bị “kẹt” khi học

---

### 🔥 Insight cuối

> Đây không chỉ là Q&A system
> 👉 mà là **learning companion**

---

## 14. Demo Statement

“We are not replacing teachers — we are augmenting how students learn.”

---

## 15. Phân công

* Nguyễn Tiến Đạt - 2A202600218: Problem + Canvas + UX
* Ngô Văn Long - 2A202600129: User flows (4 paths)
* Nguyễn Duy Hiếu - 2A202600153: Metrics + ROI
* Phạm Đan Kha - 2A202600253: Prototype + Prompt design

