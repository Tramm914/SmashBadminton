(a) Chi tiết Thực thể & Các trường quan trọng
- Khách hàng (Customer)
+ customer_id (PK, string/uuid): Mã định danh duy nhất của khách hàng.
+ full_name (string): Họ và tên khách hàng.
+ phone_number (string): Số điện thoại liên hệ (dùng để xác nhận booking).
+ email (string): Địa chỉ email.
+ created_at (timestamp): Thời gian đăng ký tài khoản.

- Sân cầu lông (Court)
+ court_id (PK, string/uuid): Mã định danh duy nhất của sân (VD: COURT-01).
+ name (string): Tên sân (VD: Sân số 1 - Thảm VIP).
+ court_type (string): Loại sân (VD: Thảm PVC, Sân gỗ).
+ price_per_hour (decimal/integer): Giá thuê trên 1 giờ (VNĐ).
+ status (string): Trạng thái sân (ACTIVE - Hoạt động, MAINTENANCE - Bảo trì).

- Lịch đặt sân (Booking)
+ booking_id (PK, string/uuid): Mã định danh duy nhất của lịch đặt.
+ customer_id (FK): Tham chiếu đến Khách hàng đặt sân.
+ court_id (FK): Tham chiếu đến Sân được đặt.
+ booking_date (date): Ngày chơi (YYYY-MM-DD).
+ start_time (time): Giờ bắt đầu (VD: 17:00).
+ end_time (time): Giờ kết thúc (VD: 19:00).
+ total_price (decimal/integer): Tổng tiền = Số giờ chơi * price_per_hour.
+ status (string): Trạng thái lịch (PENDING - Chờ duyệt, CONFIRMED - Đã xác nhận, CANCELLED - Đã hủy).

(b) Luật nghiệp vụ 
- Quy tắc quan hệ thực thể: Một Lịch đặt sân (Booking) phải thuộc về đúng 1 Khách hàng (Customer) và áp dụng cho đúng 1 Sân cầu lông (Court).
- Quy tắc giá trị: Giá thuê sân trên một giờ (price_per_hour) và Tổng tiền đặt sân (total_price) không được là số âm hoặc bằng 0 (phải $> 0$).
- Quy tắc thời gian đặt: Giờ kết thúc (end_time) phải lớn hơn giờ bắt đầu (start_time), và thời lượng thuê tối thiểu cho mỗi lần đặt là 1 giờ.
- Quy tắc trạng thái sân: Khách hàng chỉ được phép tạo lịch đặt mới đối với những sân đang có trạng thái là ACTIVE (không được đặt sân đang trong trạng thái MAINTENANCE).

(c) Ràng buộc toàn vẹn 
- Ràng buộc duy nhất (Unique Constraint): Số điện thoại (phone_number) và Email (email) của Khách hàng trong hệ thống phải là duy nhất (không được trùng lặp giữa hai khách hàng khác nhau).
- Ràng buộc chống trùng lịch (No Double-Booking Constraint): Không được tồn tại 2 Lịch đặt sân (Booking) có trạng thái CONFIRMED hoặc PENDING trên cùng một Sân (court_id) trong cùng một Ngày (booking_date) mà có khung giờ bị giao nhau (Overlapping time slots).
 Công thức logic ràng buộc thời gian: (Start A < End B) và (End A > Start B)
 không được phép xảy ra.
- Ràng buộc khóa ngoại (Referential Integrity): Không được xóa một Sân cầu lông (Court) hoặc Khách hàng (Customer) nếu đang tồn tại lịch đặt (Booking) liên kết với họ trong tương lai.
