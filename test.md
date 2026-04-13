# Test file
class SinhVien:
    def __init__(self, ma_sv, ten, diem):
        self.ma_sv = ma_sv
        self.ten = ten
        self.diem = diem

    def hien_thi(self):
        print(f"Mã SV: {self.ma_sv}, Tên: {self.ten}, Điểm: {self.diem}")


# Danh sách sinh viên
ds_sinh_vien = []

# Thêm sinh viên
def them_sinh_vien():
    ma = input("Nhập mã SV: ")
    ten = input("Nhập tên: ")
    diem = float(input("Nhập điểm: "))
    sv = SinhVien(ma, ten, diem)
    ds_sinh_vien.append(sv)

# Hiển thị danh sách
def hien_thi_ds():
    print("\nDanh sách sinh viên:")
    for sv in ds_sinh_vien:
        sv.hien_thi()

# Chạy thử
while True:
    print("\n1. Thêm SV")
    print("2. Hiển thị")
    print("3. Thoát")

    chon = input("Chọn: ")

    if chon == "1":
        them_sinh_vien()
    elif chon == "2":
        hien_thi_ds()
    elif chon == "3":
        break
    else:
        print("Chọn sai!")
Đây là file markdown đầu tiên của tôi 🚀
