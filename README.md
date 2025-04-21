# BÀI TẬP VỀ NHÀ 05, Môn Hệ quản trị csdl.
## SUBJECT: Trigger on mssql
## HoTen: Nguyễn Đức Dương 
## MaSV: K225480106093
## Lớp: K58KTP
# A. PHÂN TÍCH THIẾT KẾ HỆ THỐNG ĐẶT VÉ XEM PHIM ONLINE
I. MÔ TẢ BÀI TOÁN
- Trong bối cảnh mà nhu cầu giải trí ngày càng cao như dịch vụ xem phim thì việc đặt được vé xem phim là mong muốn cũng như yêu cầu của mọi người, việc mua vé trực tiếp tại rạp gặp rất nhiều hạn chế như: Người mua khó sắp xếp thời gian, luôn phải theo dõi lịch chiếu phim để đặt vé cũng như gây trở ngại về doanh thu bán vé. Do vậy 1 hệ thống đặt vé xem phim online sẽ giúp ích rất nhiều cho người mua trong việc đặt vé, xem thông tin phim cũng như thanh toán 1 cách nhanh gọn và tiện lợi.

II. YÊU CẦU BÀI TOÁN
- Yêu cầu chức năng: Người dùng có thể đăng nhập, tra cứu thông tin phim( lịch chiếu, thời lượng, thể loại,...), chọn phòng chiếu và ghế ngồi, thanh toán online qua nhiều phương thức ( ngân hàng, ví điện tử ). Người quản trị viên có thể quản lý danh sách phim, ghế ngồi, giá vé, thống kê tình hình đặt vé, doanh thu.
- Yêu cầu phi chức năng: Giao diện thân thiện, dễ sử dụng, tốc độ xử lý nhanh, cập nhập thông tin nhanh chóng, bảo mật tốt.

III. CSDL CỦA HỆ THỐNG ĐẶT VÉ XEM PHIM ONLINE
1. DATABASE VÀ CÁC BẢNG.
- 1.1. BẢNG Nguoi_Dung: ma_nguoi_dung là khoá chính (PK).
![Untitled](https://github.com/user-attachments/assets/94d310c6-7b3b-4966-8963-0d5690995f34)

- 1.2. BẢNG PHIM: ma_phim là khoá chính (PK).
![Untitled](https://github.com/user-attachments/assets/fadfebf6-95be-49ef-b575-e2d089baba9c)

- 1.3. BẢNG RẠP_PHIM: ma_rap là khoá chính (PK).
![Untitled](https://github.com/user-attachments/assets/515f7aa3-283e-45fb-913a-aed5e5a6b59c)

- 1.4. BẢNG SUẤT_CHIẾU: ma_chieu là khoá chính (PK).
![Untitled](https://github.com/user-attachments/assets/f119cf36-2cba-403d-995d-dc1423c8c8ce)

- 1.5. BẢNG ĐẶT_VÉ: ma_ve là khoá chính (PK).
![Untitled](https://github.com/user-attachments/assets/b596edbf-08ee-4b76-a72c-44a3b4be94dd)

2. KHOÁ NGOẠI (FK) VÀ (CK).
- 2.1. LIÊN KẾT KHOÁ NGOẠI GIỮA BẢNG SUẤT_CHIẾU VỚI 2 BẢNG *PHIM* VÀ *RẠP_PHIM*.
![Untitled](https://github.com/user-attachments/assets/44f5ac59-4f57-41ab-946f-4b1cfd4721ed)

- 2.1.1. BẢNG *SUẤT_CHIẾU* LIÊN KẾT VỚI BẢNG *PHIM* QUA THUỘC TÍNH **ma_phim** ( tại BẢNG PHIM thì ma_phim là khoá chính, BẢNG SUẤT_CHIẾU thì là khoá ngoại ).
![image](https://github.com/user-attachments/assets/efe3e7ad-431a-445e-b4b5-f13da4c5fba2)

- 2.1.2. BẢNG *SUẤT_CHIẾU* LIÊN KẾT VỚI BẢNG *RẠP_PHIM* QUA THUỘC TÍNH **ma_rap** ( tại BẢNG RẠP_PHIM thì ma_rap là khoá chính, BẢNG SUẤT_CHIẾU thì là khoá ngoại ).
![image](https://github.com/user-attachments/assets/9312a8b3-ff11-47bf-abb5-e48ccdbc1a4f)

- 2.2. LIÊN KẾT KHOÁ NGOẠI GIỮA BẢNG ĐẶT_VÉ VỚI 2 BẢNG *Nguoi_Dung* VÀ *SUẤT_CHIẾU*.
![Untitled](https://github.com/user-attachments/assets/b3ae8e98-7546-4265-9c80-faa2801c2cb8)

- 2.2.1. BẢNG *ĐẶT_VÉ* LIÊN KẾT VỚI BẢNG *Nguoi_Dung* QUA THUỘC TÍNH **ma_nguoi_dung** ( tại BẢNG Nguoi_Dung thì ma_nguoi_dung là khoá chính, ĐẶT_VÉ thì là khoá ngoại ).
![image](https://github.com/user-attachments/assets/dc2bb848-a0f2-439f-bf84-7de6b1571f32)

- 2.2.2. BẢNG *ĐẶT_VÉ* LIÊN KẾT VỚI BẢNG *SUẤT_CHIẾU* QUA THUỘC TÍNH **ma_chieu** ( tại BẢNG SUẤT_CHIẾU thì ma_chieu là khoá chính, ĐẶT_VÉ thì là khoá ngoại ).
![image](https://github.com/user-attachments/assets/53136558-ddda-4801-b3e4-19eefefbc770)

## Bài Làm:
1. 

