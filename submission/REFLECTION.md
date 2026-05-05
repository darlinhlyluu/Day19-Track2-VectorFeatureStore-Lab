# Reflection - Lab 19

**Tên:** Lưu Linh Ly
**Cohort:** A20-K1
**Path đã chạy:** lite

---

## Câu hỏi (<= 200 chữ)

Trên golden set 50 queries, BM25 mạnh nhất ở `exact` queries vì query chứa đúng technical terms xuất hiện nguyên văn trong corpus. Kết quả thực nghiệm cũng cho thấy điều đó: BM25 đạt 96.7% trên `exact` queries. Hybrid thắng rõ nhất ở `mixed` queries với 100.0%, vì nó kết hợp exact-match signal của BM25 và semantic signal của vector search qua RRF. Xét trung bình toàn bộ tập, hybrid cũng đứng đầu với 78.6%, cao hơn BM25 (77.8%) và semantic (73.2%). Với `paraphrase` queries, pure vector về lý thuyết phù hợp hơn, nhưng ở lite path model `BAAI/bge-small-en-v1.5` chưa tối ưu cho tiếng Việt nên lợi thế này chưa áp đảo.

Tôi không dùng hybrid khi bài toán rất rõ ràng. Nếu query thiên về keyword chính xác, vocabulary ổn định, và cần hệ thống đơn giản, dễ giải thích, pure BM25 là lựa chọn hợp lý. Ngược lại, nếu user thường tìm theo paraphrase, đa ngôn ngữ, hoặc cần match theo ý nghĩa hơn là theo từ, pure vector sẽ phù hợp hơn.

---

## Điều ngạc nhiên nhất khi làm lab này

Điều ngạc nhiên nhất là hybrid search không phải do một retriever “thông minh hơn”, mà do cách kết hợp hai tín hiệu bổ sung cho nhau. Ngoài ra, ở NB4 tôi thấy rõ rằng logic PIT join có thể đúng nhưng latency online lookup trên SQLite local vẫn cao hơn kỳ vọng trên Windows, dù feature store và join vẫn chạy đúng.

---

## Bonus challenge

- [ ] Đã làm bonus (xem `bonus/`)
- [ ] Pair work với: _<tên đồng đội nếu có>_
