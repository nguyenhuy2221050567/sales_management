Chuyên đề 13/4

Nguyễn Quang Huy
2221050567
DCCTCT67_05C
1. THIẾT KẾ HỆ THỐNG (System Design)
📌 Kiến trúc tổng thể: MVC

Hệ thống được xây dựng theo mô hình:

Model: Xử lí dữ liệu (Product, Order…)
View: Giao diện (HTML, JS)
Controller: Xử lí logic (PHP)

👉 Luồng:
View → Controller → Model → Database → trả về View

📌 Các module chính

Hệ thống gồm 4 module:

Quản lí sản phẩm
Quản lí bán hàng
Quản lí tồn kho
Thống kê – báo cáo
🧱 2. PHÂN TÍCH CÁC LỚP (Class Analysis)
🍎 1. Lớp Product
Vai trò:

Lưu thông tin hoa quả trong hệ thống

Thuộc tính:
id
name
price
quantity
expiry_date
Phương thức:
addProduct()
updateProduct()
deleteProduct()
getAllProducts()

👉 Đây là lớp trung tâm

🧾 2. Lớp Order
Vai trò:

Đại diện cho một hóa đơn bán hàng

Thuộc tính:
id
created_at
total
Phương thức:
createOrder()
calculateTotal()
saveOrder()
📄 3. Lớp OrderDetail
Vai trò:

Chi tiết từng sản phẩm trong hóa đơn

Thuộc tính:
id
order_id
product_id
quantity
price
Phương thức:
addItem()
getItemsByOrder()

👉 Quan hệ:

1 Order → nhiều OrderDetail
1 Product → nhiều OrderDetail
👤 4. Lớp User (nếu có đăng nhập)
Thuộc tính:
id
username
password
role
Phương thức:
login()
logout()
⚙️ 5. Lớp Database (kết nối)
Vai trò:

Quản lí kết nối MySQL

Phương thức:
connect()
query()
🔗 3. MỐI QUAN HỆ GIỮA CÁC LỚP

👉 Quan hệ chính:

Product ↔ OrderDetail (1 - nhiều)
Order ↔ OrderDetail (1 - nhiều)

👉 Hiểu đơn giản:

Order = hóa đơn
OrderDetail = từng dòng sản phẩm
🧠 4. PHÂN TÍCH THIẾT KẾ (ĐIỂM ĂN ĐIỂM)
✔️ Tính đóng gói (Encapsulation)
Dữ liệu được quản lí trong class
Không thao tác trực tiếp database từ View
✔️ Tính phân tách trách nhiệm
Product chỉ lo sản phẩm
Order chỉ lo hóa đơn
✔️ Tính mở rộng
Có thể thêm:
Discount (giảm giá)
Supplier (nhà cung cấp)
🎯 5. MÔ TẢ UML (viết vào báo cáo)

Bạn có thể ghi:

Hệ thống được thiết kế theo hướng đối tượng với các lớp chính như Product, Order, OrderDetail và User. Các lớp này liên kết với nhau thông qua các mối quan hệ một – nhiều, đảm bảo tính chặt chẽ trong quản lí dữ liệu và dễ dàng mở rộng trong tương lai.

🔥 TÓM LẠI (ĐỂ BẠN NHỚ NHANH)
Product → sản phẩm
Order → hóa đơn
OrderDetail → chi tiết
User → người dùng
Database → kết nối
