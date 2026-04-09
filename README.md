
---

---

## 📎 Individual UX Exercise (Day 5)

Chi tiết bài làm cá nhân của mình tại: https://github.com/NguyenDat142857/2A202600218-NguyenTienDat-Lab05

### Nội dung chính
- UX analysis theo framework 4 paths
- Sketch cải thiện trải nghiệm (as-is → to-be)
- Insight về AI uncertainty và trust

👉 Bài tập tập trung vào thiết kế UX cho AI khi **không chắc chắn và có thể sai**

---

# AI Tutor — Trợ lý học tập thông minh (Q&A nội bộ)

AI Tutor là trợ lý học tập giúp sinh viên/học sinh tra cứu và hiểu kiến thức từ tài liệu nội bộ (slides, notes, syllabus) thông qua hỏi đáp tự nhiên.

---

## Problem

Người học mất nhiều thời gian tìm tài liệu, dễ hiểu sai kiến thức và phụ thuộc vào giảng viên/TA do thiếu công cụ hỗ trợ real-time.

---

## Solution

AI Tutor cho phép:

* Hỏi câu hỏi tự nhiên
* Nhận câu trả lời kèm giải thích + ví dụ
* Trích dẫn nguồn từ tài liệu (citation)

👉 Đây là **augmentation** — hỗ trợ học, không thay thế giảng viên.

---

## Key Features

* Q&A từ tài liệu nội bộ (RAG)
* Citation rõ ràng
* Gợi ý câu hỏi liên quan
* Fallback khi AI không chắc

---

## Evaluation

* Answer accuracy ≥ 80%
* Citation accuracy ≥ 90%
* Hallucination < 5%

---

## Tech

* LLM (OpenAI API)
* Vector DB (FAISS / Chroma)
* RAG pipeline

---

## Team

* Nguyễn Tiến Đạt - 2A202600218: Problem + Canvas + UX 
* Ngô Văn Long - 2A202600129: User flows (4 paths) 
* Nguyễn Duy Hiếu - 2A202600153: Metrics + ROI 
* Phạm Đan Kha - 2A202600253: Prototype + Prompt design

---

## Day 5 — AI Product Design

* AI = probabilistic (có thể sai)
* 3 trụ: Requirement · Eval · UX
* Thiết kế 4 paths: đúng / sai / không chắc / mất niềm tin
* Xây dựng Canvas + SPEC draft

---

👉 *“We are not replacing teachers — we are augmenting how students learn.”*
