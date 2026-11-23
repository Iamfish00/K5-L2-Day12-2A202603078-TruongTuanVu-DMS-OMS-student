# Tự đánh giá — Trương Tuấn Vũ · G09

## 1. Tự rà soát 4 cảnh

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S02_rgb.png | child_seat / occupied | wrong_class | occupied=yes không thuộc miền giá trị gốc. Ảnh có người nhỏ trong ghế, ngoài phạm vi ghế trống của đề; tạm dùng unknown theo phản hồi Huy và quy tắc ca chưa được guideline bao phủ. | Có trong export_final_v2.zip; cần coach xác nhận trường hợp dữ liệu |
| S05_ir.png | child_seat / occupied | wrong_class | Cùng ca ngoài phạm vi như S02; không ghi no vì ảnh không thể hiện ghế trống. | Có trong export_final_v2.zip; tạm unknown |
| D01.png | frame_meta / light | guess | Khung NIR không đủ căn cứ xác định ban đêm; đổi night thành unknown. | Có trong export_final_v2.zip |
| D06.png | face / face13 | flag | Đầu cúi, vùng mắt không đủ rõ; giữ unknown thay vì suy thành closed. | Đã đối chiếu và giữ nguyên |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: Dùng occupied=yes tại 4 box ở S02/S05 RGB và IR, không có trong schema gốc; đồng thời gặp ảnh có người trong ghế trái với mô tả dữ liệu chỉ có ghế trống của đề.

Vì sao mình mắc: Schema trên máy từng được thêm yes nên các lần kiểm trước không phát hiện giá trị ngoài guideline. Miền giá trị của đề cũng chưa bao phủ trường hợp đang có trong ảnh.

Lần sau tránh bằng cách: Dùng schema gốc, đối chiếu cả hình ảnh và miền giá trị; ghi ca ngoài phạm vi để hỏi coach. Không gán no cho ghế có người chỉ để hết lỗi. Bản v2 tạm dùng unknown và giữ ca này để xác nhận.

## 3. Ghi chú về disagreement_log

Một dòng bạn của mình đúng và mình sai. Mình học được gì từ dòng đó: Hiện dùng light=unknown ở D01, còn bản cũ của mình ghi night dù không có dữ kiện ngày/đêm; bản v2 đã sửa thành unknown. Huy cũng chỉ ra 4 occupied=yes không hợp schema gốc. Qua đối chiếu ảnh và guideline, 15/17 dòng review Hiện đã có kết luận của phía mình, 2 dòng còn ambiguous; chưa ghi rằng Hiện hoặc coach đã xác nhận các kết luận đó. Bài học là phải phân biệt cờ không nhìn thấy điểm với cờ bị che, và phân biệt kết quả kiểm tra tự động với độ đúng của nhãn.
