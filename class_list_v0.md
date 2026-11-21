# Danh sách lớp v0 — Nguyễn Thế Anh · G10

> Bản nháp dựa trên Guideline Cabin v1.0. Cột IR là dự đoán cần đối chiếu với các ảnh bạn đã xem; không coi đây là kết quả đo từ ảnh.

## DMS

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | eye_state | open / closed / unknown | Theo dõi dấu hiệu mắt nhắm kéo dài để cảnh báo buồn ngủ | Thường có thể thấy; phản xạ kính hoặc che khuất có thể làm phải chọn unknown |
| 2 | gaze_zone | road / mirror_l / mirror_r / mirror_c / cluster / center / lap / other | Phát hiện tài xế nhìn lệch khỏi vùng lái xe | Có thể ước lượng từ hướng mắt và đầu; nếu không chắc chọn other |
| 3 | glasses | none / clear / sun / unknown | Diễn giải độ tin cậy của quan sát mắt qua kính | Có thể bị phản xạ; kính râm trên NIR có thể trông trong suốt |
| 4 | face13 | 13 điểm khuôn mặt | Định vị mắt, mũi và miệng để hỗ trợ phân tích trạng thái mặt | Có khi đủ tương phản; điểm bị che cần đánh dấu occluded hoặc outside |
| 5 | seatbelt | worn_correct / worn_incorrect / not_worn / unknown | Phát hiện việc thắt dây an toàn của tài xế | Có thể thấy dải dây nếu đủ tương phản; nếu bị che hoặc tối chọn unknown |
| 6 | hand / on_wheel | whose, side, yes / no / unknown | Theo dõi tay tài xế có chạm vô lăng hay không | Hình bàn tay có thể thấy; tư thế hoặc vật che có thể gây khó phân biệt |
| 7 | phone / state | held / mounted / lap | Phát hiện sử dụng điện thoại gây xao nhãng | Chỉ gán khi thấy cạnh, góc hoặc màn hình đủ nhận ra điện thoại |

## OMS

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | person / seat | driver / front_passenger / rear_left / rear_middle / rear_right | Xác định có người ở ghế nào để theo dõi số người và vị trí | Thường có thể nhận ra hình dáng người; vị trí ghế phải quy đổi theo chiều xe |
| 2 | seatbelt | worn_correct / worn_incorrect / not_worn / unknown | Theo dõi tình trạng dây an toàn của người ngồi | Có thể khó thấy trên vùng tối hoặc bị che; khi không chắc chọn unknown |
| 3 | child_seat / occupied | occupied: no / unknown | Nhận biết ghế trẻ em và liệu có nhìn rõ bên trong hay không | Hình ghế có thể nhận ra; tình trạng bên trong có thể bị che |
| 4 | infant_seat / facing | rear / front | Nhận biết ghế em bé và hướng quay để hỗ trợ quy tắc an toàn trên xe | Có thể dựa vào hình dạng và hướng ghế; cần xác nhận trực tiếp trên từng ảnh |
| 5 | object / type | bag / box / cup / other | Phân loại hành lý hoặc đồ vật trong cabin | Hình dạng có thể còn thấy nhưng màu sắc mất; không rõ loại thì chọn other |
| 6 | object / seat | driver / front_passenger / rear_left / rear_middle / rear_right | Xác định vị trí đồ vật để hỗ trợ quản lý cabin và hành lý | Có thể suy từ vị trí trong ảnh nếu thấy rõ; ghế phải gọi theo chiều xe |

## 2 câu hỏi leo thang

1. Câu hỏi: Với điện thoại bị che một phần, dấu hiệu tối thiểu nào đủ để phân biệt điện thoại với một vật tối khác?
   Khung ví dụ: D04.png, nơi hai export có box phone lệch nhau.
   Bạn tạm gán thế nào và vì sao: Chỉ gán phone nếu nhìn thấy cạnh, góc hoặc màn hình nhận ra được; nếu chưa đủ căn cứ thì hỏi coach thay vì đoán.
2. Câu hỏi: Khi ghế em bé bị che hoặc nhìn xiên, cần dựa vào dấu hiệu nào để phân biệt facing=front và facing=rear?
   Khung ví dụ: S03_rgb.png, nơi hai export bất đồng về facing.
   Bạn tạm gán thế nào và vì sao: Chọn hướng có bằng chứng hình dạng rõ nhất; nếu chưa phân biệt được thì ghi nhận ca cần coach phân xử, không tự thêm giá trị ngoài schema.
