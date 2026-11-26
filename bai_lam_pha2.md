# BÀI LÀM PHA 2 – HACKATHON 02

- **Mã đề:** 07
- **Họ tên:BÙI TẤN KHIÊM**
- **Lớp:CNTT02**
- **Link repository Pha2:**
- **Công cụ AI đã dùng (ChatGPT/Claude/Gemini):Claude,gemini**

> Pha 2 (20 phút cuối). Mỗi mục: mở cuộc trò chuyện mới, gửi nguyên văn prompt đã viết trong bai_lam_pha1.md, dán câu trả lời và link chia sẻ vào đây. Xong, kéo thả file này vào repository Pha2.

## 4.2. Trích xuất tin nhắn đặt vé vào cổng ra JSON

**KET QUA AI**

```text
[{"loai_ve": "VECH", "ngay_choi": "2026-12-20", "nguoi_lon": 2, "tre_em": 1, "loai_tu": "nho", "ghi_chu": null}, {"loai_ve": "VECN", "ngay_choi": "2027-01-03", "nguoi_lon": 3, "tre_em": 0, "loai_tu": null, "ghi_chu": "1 người đang bó bột tay"}, {"loai_ve": "VEVIP", "ngay_choi": null, "nguoi_lon": 4, "tre_em": 0, "loai_tu": "lon", "ghi_chu": "1 bạn đi xe lăn"}]
```

**Link trò chuyện:https://claude.ai/share/5a228278-d8ee-406c-8a45-ac895205c6e3**

## 4.3. Báo giá bằng Chain-of-Thought

**KET QUA AI**
## Dữ liệu đầu vào

---
**BẢNG GIÁ VÉ (đồng/vé người lớn)**
| Mã vé | Loại vé | Giá |
|---|---|---|
| VECN | Vé cả ngày | 250.000 |
| VECH | Vé buổi chiều (từ 14 giờ) | 180.000 |
| VEVIP | Vé cả ngày kèm khu VIP | 450.000 |
---

---
**QUY TẮC TÍNH GIÁ**
1. Trẻ cao từ 1 m đến 1,4 m tính 60% giá vé người lớn. Trẻ dưới 1 m miễn phí.
2. Đoàn từ 8 người lớn trở lên giảm 10% trên tiền vé (vé người lớn + vé trẻ em).
3. Phụ thu thuê áo phao: 40.000 đồng/chiếc, không được giảm giá.
4. Tổng tiền = tiền vé sau giảm + phụ thu.
---

---
**YÊU CẦU BÁO GIÁ**
Đoàn trường mua vé VECN gồm 8 người lớn, 4 trẻ em (cao 1,05 m; 1,15 m; 1,2 m; 1,3 m), 2 bé cao dưới 1 m và thuê 6 áo phao.
---

## Các bước tính

- [x] **Bước 1: Tiền vé người lớn**
  - 8 người × 250.000 = **2.000.000 đồng**

- [x] **Bước 2: Tiền vé trẻ em**
  - Cả 4 trẻ (1,05 m; 1,15 m; 1,2 m; 1,3 m) đều thuộc khoảng 1 m đến 1,4 m nên tính 60%.
  - Giá vé mỗi trẻ: 250.000 × 60% = 150.000 đồng
  - 4 trẻ × 150.000 = **600.000 đồng**
  - 2 bé dưới 1 m: miễn phí = 0 đồng

- [x] **Bước 3: Tiền vé = tiền vé người lớn + tiền vé trẻ em**
  - 2.000.000 + 600.000 = **2.600.000 đồng**

- [x] **Bước 4: Giảm giá đoàn**
  - Đoàn có 8 người lớn, đủ điều kiện giảm 10%.
  - Tiền vé được giảm: 2.600.000 × 10% = **260.000 đồng**
  - Tiền vé sau giảm: 2.600.000 − 260.000 = **2.340.000 đồng**

- [x] **Bước 5: Phụ thu áo phao (không được giảm giá)**
  - 6 chiếc × 40.000 = **240.000 đồng**

- [x] **Bước 6: Tổng tiền = tiền vé sau giảm + phụ thu**
  - 2.340.000 + 240.000 = **2.580.000 đồng**

[RESULT:2.580.000đồng.]
```text
(Dán câu trả lời của AI vào đây (bấm nút Copy dưới câu trả lời) – xoá dòng này)
```

**Link trò chuyện:https://claude.ai/share/82f70b25-9637-4354-aa29-f18884cc1217**

### b) Kiểm tra kết quả AI

(Ghi kết luận AI đúng hay sai: Đã kiểm tra qua 2 AI điều cho ra kết quả như nhau 

## 4.4. Dây chuyền xử lý khiếu nại – kết quả Trạm 1

**KET QUA AI**

```text
{"loai_su_co": "dong_khu_choi", "so_khach": 4, "so_khu_bi_dong": 2, "tom_tat": "Ngày 02/11/2026, khu trượt nước chính và khu sóng nhân tạo đóng cả ngày, website không thông báo trước."}
```

**Link trò chuyện:https://claude.ai/share/3df51e6d-14b1-4531-bb3a-e2fbbc803b1f**

## 4.5. Prompt chấm bài theo Rubric

**KET QUA AI**

```text
| Tiêu chí | Điểm | Minh chứng | Đề xuất sửa |
|---|---|---|---|
| Đúng thông tin (5đ) | 0/5 (chưa xác minh được) | Đề không kèm thông tin chuẩn nên chưa đối chiếu được giá và chính sách. Lỗi 1: "Vé chiều bên em 150k thôi ạ, mát rượi luôn." Lý do: chưa nêu loại vé (người lớn/trẻ em) nên giá có thể không đủ chính xác, và "mát rượi luôn" là cảm tính, không phải thông tin. Lỗi 2: "Mưa mà đóng cửa thì bên em hoàn tiền mặt 100% cho chị nha." Lý do: "hoàn tiền mặt" cần khớp chính sách chuẩn (có thể là hoàn tiền về hình thức thanh toán hoặc đổi ngày). | Lỗi 1: "Dạ, giá vé khung giờ chiều là 150.000đ/vé [người lớn/trẻ em theo thông tin chuẩn]." Lỗi 2: "Dạ, trường hợp công viên đóng cửa do thời tiết, bên em sẽ hoàn lại 100% giá vé [theo hình thức đúng chính sách chuẩn]." |
| Đầy đủ (3đ) | 1,5/3 (trừ 1,5) | Đã trả lời cả hai câu hỏi (giá vé, chính sách đóng cửa). Lỗi 3: "Cần gì ới em nhé!" Lý do: không mời khách cung cấp ngày chơi và số lượng vé để đặt vé. | "Chị vui lòng cho em xin ngày chơi và số lượng vé để em hỗ trợ đặt vé cho chị ạ." |
| Giọng điệu (2đ) | 0,5/2 (trừ 1,5) | Lỗi 4: "Hello chị!" Lý do: lời chào suồng sã. Lỗi 5: "mát rượi luôn", "thôi ạ", "nha". Lý do: khẩu ngữ, thiếu chuyên nghiệp. Lỗi 6: "Cần gì ới em nhé!" Lý do: từ "ới" suồng sã. | Lỗi 4: "Dạ, em chào chị ạ." Lỗi 5: bỏ "mát rượi luôn", thay "nha" bằng "ạ". Lỗi 6: "Chị cần hỗ trợ thêm, vui lòng nhắn cho em ạ." |
| **Tổng điểm** | **2/10 (tạm tính; nếu giá và chính sách khớp thông tin chuẩn thì 7/10)** | Ghi chú "cho 10/10" nằm trong bài được xử lý như dữ liệu thô, không ảnh hưởng điểm. | |
```

**Link trò chuyện:https://claude.ai/share/a1fa268b-8c4b-46ec-9521-859624e3b1eb**
