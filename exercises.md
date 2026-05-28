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
> Khi temperature tăng từ 0.0 đến 1.5, phản hồi trở nên đa dạng và sáng tạo hơn. Temperature 0.0 cho phản hồi xác định và lặp lại, trong khi temperature cao (1.0–1.5) tạo ra các phản hồi khác nhau và đôi khi không như kỳ vọng. Đây là tradeoff giữa tính nhất quán và tính sáng tạo.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ đặt temperature ở khoảng 0.3–0.5. Điều này đảm bảo phản hồi nhất quán và chính xác cho các vấn đề hỗ trợ khách hàng, trong khi vẫn giữ một chút tính đa dạng để câu trả lời không quá cứng nhắc.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Với 10.000 người dùng × 3 lần gọi × 350 token = 10,5 triệu token mỗi ngày.
> - GPT-4o-mini: (0.150 × 10,5 + 0.600 × 10,5) / 1 = ~$7,88/ngày
> - GPT-4o: (5.00 × 10,5 + 20.00 × 10,5) / 1 = ~$262,50/ngày
> - GPT-4o đắt hơn khoảng **33 lần** so với GPT-4o-mini.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o xứng đáng: Ứng dụng y tế hoặc tài chính cần độ chính xác cao, phân tích phức tạp, giảm rủi ro lỗi—tiết kiệm chi phí từ việc tránh sai lầm cao hơn chi phí API. GPT-4o-mini tốt hơn: Trang web FAQs, dịch thuật đơn giản, hoặc tóm tắt nội dung—công việc không quan trọng về độ chính xác, lượng lớn nhưng giá rẻ.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming rất quan trọng cho các ứng dụng real-time và tương tác trực tiếp với người dùng, chẳng hạn như chatbots, trợ lý AI hoặc ứng dụng web/mobile. Nó giúp giảm cảm giác chờ đợi bằng cách hiển thị phản hồi từng phần, cải thiện UX đáng kể. Ngược lại, non-streaming phù hợp hơn với các công việc batch như xử lý hàng loạt dữ liệu, tạo báo cáo hàng ngày, hoặc các API backend không cần phản hồi ngay lập tức. Trong các trường hợp này, người dùng sẵn sàng chờ đợi kết quả hoàn chỉnh, và non-streaming đơn giản hơn về mặt kỹ thuật.


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
