# Danh sách lớp v0 — Trương Tuấn Vũ · G09

## DMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | eye_left / eye_right | open / closed / unknown, riêng từng mắt | Mô tả trạng thái mắt từng khung; hỗ trợ phân tích mắt nhắm kéo dài trên chuỗi thời gian | Có khi khe mí đủ rõ; bị che hoặc không phân biệt được thì unknown |
| 2 | gaze_zone | road / mirror_l / mirror_r / mirror_c / cluster / center / lap / other | Xác định vùng người lái đang hướng mắt và đầu tới | Có khi mắt và đầu đủ rõ; không chắc thì other |
| 3 | glasses | none / clear / sun / unknown | Nhận biết kính và ảnh hưởng của kính tới khả năng quan sát mắt | Có giới hạn; kính râm có thể trông trong trên NIR |
| 4 | face13 | 13 điểm, cờ occluded / outside | Mô tả hình học mắt, mũi, miệng để hỗ trợ phân tích khuôn mặt | Có khi mặt đủ lớn và rõ; điểm bị che cần cờ phù hợp |
| 5 | hand / on_wheel | whose: driver/passenger; side: left/right; on_wheel: yes/no/unknown | Phân biệt bàn tay và xác định tay có chạm vô lăng | Có nếu tay và vùng tiếp xúc nhìn thấy được |
| 6 | phone / state | held / mounted / lap | Xác định điện thoại và ngữ cảnh sử dụng | Có khi thấy cạnh, góc hoặc màn hình; không suy từ tay gần tai |

## OMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | person | box phần cơ thể nhìn thấy | Xác định sự hiện diện và phân bố người trong cabin | Có theo hình dạng; che khuất làm giảm thông tin |
| 2 | seat | rear_left / rear_middle / rear_right trong bộ OMS này | Gắn người hoặc vật với vị trí ghế theo xe | Có theo vị trí cabin; trái ảnh OMS là rear_right |
| 3 | child_seat / occupied | no / unknown | Nhận diện ghế trẻ em trống và trường hợp chưa thấy rõ bên trong | Có theo hình dạng; không đoán khi bên trong bị che |
| 4 | infant_seat / facing | rear / front | Nhận diện ghế em bé và hướng đặt theo xe | Có khi cấu trúc và hướng ghế đủ rõ |
| 5 | object / type | bag / box / cup / other | Phân loại đồ vật mang theo và xác định vị trí trong cabin | Có theo hình dạng, vị trí, ngữ cảnh; không dựa vào màu RGB trên IR |
| 6 | person / seatbelt | not_worn / unknown trong SVIRO | Ghi nhận tình trạng dây an toàn khi có người | Có nếu vùng dây đủ rõ; bị tối hoặc che thì unknown |

## 2 câu hỏi leo thang

1. Câu hỏi: Ngưỡng mặt rộng 60 px được tính theo chiều x của box trên ảnh gốc hay theo chiều ngang khuôn mặt khi ảnh DMS xoay 90°?
   Khung ví dụ: D06.png, G09.
   Bạn tạm gán thế nào và vì sao: Giữ nguyên hướng ảnh và đối chiếu chiều rộng box theo cách script hiện kiểm; cần coach xác nhận cách áp dụng cho ảnh xoay.
2. Câu hỏi: S02/S05 có người nhỏ ngồi trong ghế, trong khi đề mô tả bộ ảnh chỉ có ghế trẻ em trống và schema không có occupied=yes. Cần mở rộng guideline hay xử lý các khung này thế nào?
   Khung ví dụ: S02_rgb.png và S05_ir.png, G09.
   Bạn tạm gán thế nào và vì sao: Giữ các đối tượng hiện có, dùng occupied=unknown tạm theo quy tắc ca ngoài guideline; không coi ghế có người là ghế trống, chờ coach xác nhận.
