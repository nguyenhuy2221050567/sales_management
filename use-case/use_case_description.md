# USE CASE 1: ĐĂNG NHẬP HỆ THỐNG (UC-01)
1. Tên Use Case
Đăng nhập hệ thống
2. Mã Use Case
UC-01
3. Actor
Người dùng
Quản trị viên (Admin)
Nhân viên bán hàng
4. Mô tả tổng quát
Use case này mô tả quá trình người dùng truy cập vào hệ thống quản lý bán hàng thông qua việc nhập thông tin xác thực (tên đăng nhập và mật khẩu). Hệ thống sẽ tiến hành kiểm tra tính hợp lệ của dữ liệu đầu vào, xác thực thông tin với cơ sở dữ liệu, phân quyền truy cập và tạo phiên làm việc (session) cho người dùng.
5. Mục tiêu
Đảm bảo chỉ người dùng hợp lệ mới truy cập được hệ thống
Bảo vệ dữ liệu hệ thống khỏi truy cập trái phép
Phân quyền đúng chức năng cho từng loại người dùng
6. Tiền điều kiện (Pre-condition)
Người dùng đã được cấp tài khoản hợp lệ
Hệ thống server đang hoạt động
Cơ sở dữ liệu có thể truy cập
Trình duyệt hoặc ứng dụng client hoạt động bình thường
7. Hậu điều kiện (Post-condition)
Thành công:
Người dùng được chuyển đến giao diện chính (Dashboard)
Hệ thống tạo session đăng nhập
Ghi log đăng nhập thành công
 Thất bại:
Không tạo session
Hiển thị thông báo lỗi
Ghi log đăng nhập thất bại
8. Luồng chính (Main Success Scenario)
Người dùng truy cập vào trang đăng nhập
Hệ thống hiển thị form đăng nhập gồm:
Username
Password
Người dùng nhập thông tin đăng nhập
Người dùng nhấn nút “Đăng nhập”
Hệ thống kiểm tra:
Dữ liệu không rỗng
Đúng định dạng
Hệ thống gửi yêu cầu đến server (Auth Service)
Server thực hiện:
Mã hóa (hash) mật khẩu
So sánh với dữ liệu trong database
Nếu thông tin chính xác:
Lấy thông tin quyền (role)
Tạo session/token
Ghi log đăng nhập
Hệ thống chuyển hướng đến:
Trang Dashboard (Admin)
Trang bán hàng (Nhân viên)
9. Luồng thay thế (Alternate Flow)
9.1. Dữ liệu đầu vào không hợp lệ
5a. Nếu bỏ trống username/password:
Hiển thị: “Vui lòng nhập đầy đủ thông tin”
Quay lại bước 3
9.2. Sai tài khoản hoặc mật khẩu
7a. Nếu không tìm thấy tài khoản:
Hiển thị: “Tài khoản không tồn tại”
7b. Nếu sai mật khẩu:
Hiển thị: “Sai mật khẩu”
Cho phép nhập lại
Quay lại bước 3
9.3. Tài khoản bị khóa
7c. Nếu trạng thái tài khoản = “LOCKED”:
Hiển thị: “Tài khoản đã bị khóa”
Không cho đăng nhập
9.4. Quên mật khẩu
Người dùng chọn “Quên mật khẩu”
Chuyển sang use case UC-06
10. Luồng ngoại lệ (Exception Flow)
Mất kết nối database
Server không phản hồi
Lỗi hệ thống nội bộ

Xử lý:

Hiển thị: “Hệ thống đang bảo trì”
Ghi log lỗi
11. Quy tắc nghiệp vụ (Business Rules)
Username là duy nhất
Mật khẩu phải được mã hóa (SHA-256 / bcrypt)
Giới hạn 5 lần đăng nhập sai
Sau 5 lần sai → khóa tài khoản 5 phút
12. Yêu cầu phi chức năng (Non-functional Requirements)
Thời gian phản hồi < 3 giây
Bảo mật cao (HTTPS)
Không lưu mật khẩu dạng plaintext
13. Tần suất sử dụng 
Rất thường xuyên (mỗi lần truy cập hệ thống)
# USE CASE 2: ĐĂNG KÝ TÀI KHOẢN (UC-02)
Mô tả chi tiết
Cho phép người dùng tạo tài khoản mới để truy cập hệ thống.

Main Flow
1. Người dùng chọn “Đăng ký”
2.Nhập:
Username
Password
Email
3.Kiểm tra:
Định dạng email
Độ mạnh mật khẩu
4.Kiểm tra trùng username
5.Lưu vào database
6.Thông báo thành công
Business Rules
Password ≥ 6 ký tự
Email phải hợp lệ
Username không trùng
