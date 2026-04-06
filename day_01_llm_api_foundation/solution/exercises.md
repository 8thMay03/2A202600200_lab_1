# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> *Khi tăng `temperature` từ 0.0 → 1.5, câu trả lời trở nên **đa dạng và sáng tạo hơn**. Ở `temperature=0.0`, phản hồi rất ổn định, gần như giống nhau mỗi lần (mang tính “chắc chắn”); còn ở các mức cao hơn như 1.0–1.5, nội dung có xu hướng phong phú hơn, đôi khi bất ngờ hoặc ít phổ biến hơn. Tuy nhiên, temperature cao cũng có thể làm câu trả lời **kém nhất quán hoặc ít chính xác hơn**.
*

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> *Chọn temperature ~0.3 vì nó đảm bảo câu trả lời ổn định, chính xác, ít hallucination nhưng vẫn tự nhiên đủ để giao tiếp với khách hàng.*

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> *GPT-4o thường đắt hơn GPT-4o-mini khoảng ~10–20 lần (≈15x trung bình) cho workload này, vì tổng ~10.000 × 3 × 350 ≈ 10.5M token/ngày và đơn giá/token của 4o cao hơn mini ~1 bậc độ lớn.*

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> *GPT-4o đáng giá khi: bài toán cần độ chính xác cao + suy luận phức tạp + hiểu ngữ cảnh sâu (ví dụ: chatbot tư vấn tài chính/y tế, phân tích hợp đồng, hệ thống RAG quan trọng) nơi sai sót gây hậu quả lớn. 
GPT-4o-mini tốt hơn khi: workload lớn, lặp lại, không quá phức tạp (FAQ chatbot, phân loại, autocomplete, xử lý batch) nơi chi phí và tốc độ quan trọng hơn độ “thông minh” tối đa.*

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> *Streaming quan trọng nhất khi cần phản hồi tức thì và cải thiện UX (chatbot, AI assistant, gõ từng chữ như thật) để giảm cảm giác chờ đợi, còn non-streaming phù hợp hơn khi cần kết quả hoàn chỉnh, xử lý backend, hoặc logic phụ thuộc toàn bộ output (batch processing, lưu DB, kiểm tra/validate response trước khi trả về).*


## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
