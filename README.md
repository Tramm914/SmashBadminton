1. Tên dự án
SmashBadminton — Hệ thống Quản lý và Đặt lịch Sân Cầu Lông.
2. Mô tả đề bài
Hiện tại, cụm sân cầu lông SmashBadminton (gồm 6 sân) đang vận hành hoàn toàn thủ công bằng sổ tay và Zalo:
- Khó khăn của khách hàng: Khách muốn đặt sân phải nhắn tin hoặc gọi điện hỏi trống giờ nào, đợi nhân viên lật sổ kiểm tra rất mất thời gian.
- Khó khăn của chủ sân/nhân viên: Nhân viên ghi chép lịch bằng tay dễ bị trùng lịch (double-booking) vào giờ cao điểm. Đến cuối tháng, chủ sân không thống kê được chính xác doanh thu, không biết sân nào được đặt nhiều nhất hay khách hàng nào là khách quen để áp dụng ưu đãi.
- Giải pháp: Xây dựng một hệ thống phần mềm nhỏ giúp tự động hóa quy trình quản lý Khách hàng, Sân cầu lông và Lịch đặt sân.
3. Các thực thể chính (>= 3 thực thể)
- Khách hàng (Customer): Lưu trữ thông tin người đặt sân để liên hệ và quản lý lịch sử đặt.
- Sân cầu lông (Court): Quản lý danh sách các sân hiện có trong cụm, loại sân và giá tiền.
- Lịch đặt sân (Booking): Lưu trữ thông tin các ca đặt sân, kết nối giữa Khách hàng và Sân cầu lông theo thời gian cụ thể.
4. Người dùng / Phạm vi hệ thống
- Khách hàng (Customer): Tra cứu danh sách sân, xem lịch trống và tự tạo lịch đặt sân online.
- Quản trị viên / Nhân viên (Admin/Staff): Quản lý danh sách sân, duyệt/hủy lịch đặt của khách, xem thống kê doanh thu và quản lý thông tin khách hàng.