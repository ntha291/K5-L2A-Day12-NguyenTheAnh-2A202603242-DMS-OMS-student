# Tự đánh giá — Nguyễn Thế Anh · G10

## 1. Tự rà soát 4 cảnh

Hai ảnh S## và hai ảnh D## dưới đây được chọn từ các lỗi tự kiểm và bất đồng E3. Xác nhận các sửa đổi đã có trong export mới nhất trước khi nộp.

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| D04.png | frame_meta | missing | Thiếu tag frame_meta; export hiện tại đã có tag | Có, kiểm tra lại đạt |
| D03.png | person / seatbelt | wrong_class | E3 chọn worn_incorrect vì dây lệch khỏi vai; export hiện tại vẫn ghi worn_correct | Chưa; sửa trong CVAT rồi export lại nếu verdict peer đã được chốt |
| S02_ir.png | child_seat | wrong_class | occupied=yes không hợp lệ; chỉ nhận no hoặc unknown | Có, kiểm tra lại đạt |
| S05_rgb.png | infant_seat | seat_flip | Cảnh báo seat=driver trên ảnh chỉ nhìn hàng ghế sau | Cảnh báo đã hết ở lần kiểm cuối |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: Gán `frame_meta.light` khác `unknown` trên nhiều ảnh SVIRO RGB.

Vì sao mình mắc: Mình đã chọn day/night theo độ sáng nhìn thấy trên RGB mà quên SVIRO là ảnh dựng.

Lần sau tránh bằng cách: Trước khi export, kiểm tra `light=unknown` trên từng ảnh SVIRO theo guideline.

## 3. Ghi chú về disagreement_log

Dòng tham khảo: D03.png, `person.seatbelt` — E3 ghi verdict `peer`; dây được phân loại `worn_incorrect` vì lệch khỏi vai (GUIDE 4.7). Export hiện tại vẫn là `worn_correct`, nên chưa phản ánh verdict này. Bài học: phân biệt theo đường đi của dây trên cơ thể, không chỉ dựa vào việc nhìn thấy dây.
