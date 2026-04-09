# UX Exercise — AI Tutor (VinUni Learning Assistant)

**Student:** 2A202600218 - Nguyễn Tiến Đạt  
**Day:** Day05

---

## 1. Sản phẩm

AI Tutor — trợ lý học tập nội bộ cho sinh viên VinUni, hỗ trợ:
- Hỏi đáp kiến thức (Q&A)
- Giải thích khái niệm
- Tóm tắt tài liệu
- Hỗ trợ ôn tập

AI Tutor đóng vai trò **augmentation tool** (hỗ trợ học), không thay thế hoàn toàn giảng viên hoặc tài liệu gốc.

---

## 2. Phân tích 4 Paths (Core AI UX Framework)

---

### 2.1. Path 1 — AI đúng (Happy Path)

**Scenario**
- User hỏi: "Gradient descent là gì?"
- AI trả lời:
  - Định nghĩa chính xác
  - Có ví dụ minh họa
  - Có thể trích dẫn từ slide/bài giảng

**User experience**
- User hiểu ngay
- Không cần thao tác thêm
- Tăng niềm tin vào hệ thống

**UX hiện tại**
- Chat đơn giản → nhập câu hỏi → nhận câu trả lời
- Không có friction

**Insight**
- Đây là path tạo ra **giá trị chính (core value)**
- UX nên:
  - Nhanh
  - Rõ ràng
  - Không gây gián đoạn

**Risk (ẩn)**
- Nếu AI luôn “tỏ ra đúng” → user dễ overtrust

---

### 2.2. Path 2 — AI không chắc (Uncertain Path)

**Scenario**
- User hỏi mơ hồ:
  - "Cái này là gì?"
  - "Giải thích đoạn này"
- AI không có đủ context

**UX hiện tại**
- AI vẫn cố trả lời
- Có thể:
  - Hallucinate nhẹ
  - Đưa ra câu trả lời chung chung

**Vấn đề UX**
- Không có cơ chế:
  - Ask clarification
  - Yêu cầu thêm thông tin
- AI giả vờ “biết” → nguy hiểm hơn việc nói “không biết”

**Hệ quả**
- User hiểu sai nhưng không nhận ra
- Trust bị erosion âm thầm

**Thiếu sót chính**
- Không có **uncertainty communication**

---

### 2.3. Path 3 — AI sai (Failure Path)

**Scenario**
- AI trả lời sai:
  - Nhầm lẫn khái niệm (overfitting vs underfitting)
  - Thiếu thông tin quan trọng
  - Suy luận sai

**UX hiện tại**
- Không có:
  - Confidence score
  - Warning
  - Source rõ ràng

**User flow**
- User phải:
  1. Tự nhận ra sai
  2. Đi kiểm chứng (Google, tài liệu)
  3. Quay lại sửa hiểu biết

**Recovery hiện tại**
- Gần như **không tồn tại trong UX**

**Pain point**
- Tốn thời gian
- Cognitive load cao
- Không biết:
  - AI sai ở đâu
  - AI có học từ lỗi không

**Thiếu sót lớn**
- Không có:
  - Feedback loop
  - Correction mechanism
  - Learning signal visible

---

### 2.4. Path 4 — User mất niềm tin (Trust Breakdown)

**Scenario**
- Sau nhiều lần AI:
  - Trả lời sai
  - Trả lời mơ hồ
- User bắt đầu:
  - Không tin AI nữa
  - Quay về cách học truyền thống

**Hành vi user**
- Google
- Hỏi bạn bè
- Đọc tài liệu gốc

**UX hiện tại**
- Không có:
  - Fallback mode
  - “Safe mode” (chỉ show source)
  - Tùy chọn giảm automation

**Hệ quả**
- User churn (bỏ sản phẩm)
- Mất toàn bộ value

---

## 3. Path yếu nhất

👉 **Path 3 (AI sai) + Path 4 (Trust breakdown)**

### Lý do:
1. Không có recovery UX
2. Không có transparency
3. Không có feedback loop rõ ràng
4. Không có cơ chế rebuild trust

---

## 4. Gap giữa Marketing và Thực tế

### Marketing promise
- "AI giúp bạn học nhanh hơn"
- "Trả lời mọi câu hỏi"
- Ngầm imply:
  → AI chính xác cao
  → Có thể thay thế việc đọc tài liệu

---

### Thực tế sử dụng

AI hoạt động tốt khi:
- Câu hỏi rõ ràng
- Kiến thức phổ biến
- Context đầy đủ

AI hoạt động kém khi:
- Câu hỏi mơ hồ
- Context thiếu
- Kiến thức chuyên sâu
- Edge cases

---

### Gap lớn nhất

👉 **Marketing không communicate uncertainty**

**Kết quả:**
- User kỳ vọng: ~100% accuracy
- Reality: ~70–80%

→ Gây:
- Disappointment
- Trust breakdown nhanh

---

## 5. Đề xuất cải thiện UX (To-be Design)

---

### 5.1. Add Confidence Layer

- Hiển thị:
  - High / Medium / Low confidence
- UX:
  - Low → cảnh báo nhẹ
  - High → hiển thị bình thường

---

### 5.2. Clarification Loop

Khi AI không chắc:
- "Bạn có thể nói rõ hơn không?"
- Gợi ý:
  - "Bạn đang hỏi về định nghĩa hay ví dụ?"

---

### 5.3. Source Transparency (RAG-style)

- Hiển thị:
  - Source từ slide / tài liệu
- User có thể:
  - Click để verify

---

### 5.4. Error Recovery Flow

Khi user thấy sai:
- Button:
  - "Câu trả lời này sai"
- Flow:
  - User sửa → AI ghi nhận

---

### 5.5. Trust Rebuild Mechanism

- Mode:
  - "Chỉ hiển thị source"
  - "Giải thích dựa trên tài liệu"
- Giúp user:
  - Control lại trải nghiệm

---

## 6. Sketch (as-is vs to-be)

(Đính kèm sketch.jpg)

---

### As-is Flow

User → hỏi → AI trả lời → Done  
                     ↓  
                 (Sai → user tự xử lý)

---

### To-be Flow

User → hỏi  
↓  
AI trả lời + confidence  
↓  
- Nếu low confidence → ask clarification  
- Nếu có risk sai → show source  
↓  
User feedback → AI learn  
↓  
Trust được duy trì

---

## 7. Key Insight

👉 AI UX không phải tối ưu cho **accuracy tuyệt đối**

👉 Mà tối ưu cho:
- Transparency
- Recoverability
- Trust

---

## 8. Kết luận

Một AI product tốt không phải là AI luôn đúng,  
mà là AI:
- Biết khi nào mình sai
- Cho user công cụ để sửa
- Và giữ được niềm tin lâu dài

👉 **Trust > Accuracy**