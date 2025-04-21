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

3. THIẾT LẬP RÀNG BUỘC CK CHO CÁC THUỘC TÍNH TRONG BẢNG
- 3.1. BẢNG *Suất_Chiếu*

- 3.2. BẢNG *Đặt_Vé*


# B. Nội dung Bài tập 05:
1. Dựa trên cơ sở là csdl của Đồ án
2. Tìm cách bổ xung thêm 1 (hoặc vài) trường phi chuẩn
   (là trường tính toán đc, nhưng thêm vào thì ok hơn,
    ok hơn theo 1 logic nào đó, vd ok hơn về speed)
   => Nêu rõ logic này!
3. Viết trigger cho 1 bảng nào đó, 
   mà có sử dụng trường phi chuẩn này,
   nhằm đạt được 1 vài mục tiêu nào đó.
   => Nêu rõ các mục tiêu 
4. Nhập dữ liệu có kiểm soát, 
   nhằm để test sự hiệu quả của việc trigger auto run.
5. Kết luận về Trigger đã giúp gì cho đồ án của em.

## BÀI LÀM
### Bổ xung thêm 1 (hoặc vài) trường phi chuẩn.
1. Khái niệm trường phi chuẩn: Là trường có thể tính toán ra được từ các trường khác, nhưng bạn vẫn chủ động lưu nó vào bảng để tăng tốc truy vấn hoặc phục vụ một mục đích cụ thể.
2. Thêm trường phi chuẩn cho bảng **Đặt_Vé**
![image](https://github.com/user-attachments/assets/fd944a17-468e-40f5-a9b6-c8779bafba38)

- 2.1. Tại sao lại thêm trường phi chuẩn giờ kết thúc? Tại vì khi đặt vé, chọn suất chiếu, hệ thống sẽ biết giờ bắt đầu chiếu và thời lượng phim -> Dễ dàng tính được giờ kết thúc:
+ giờ kết thúc = giờ bắt đầu chiếu + thời lượng phim.
+ Thay vì phải tính lại thủ công khi cần, ta lưu luôn trường giờ kết thúc để tiết kiệm thời gian truy vấn, dễ dàng lọc suất còn trống, tránh trùng lịch chiếu khi cần.

- 2.2. Sử dụng lệnh để tiến hành thêm thay vì thêm thủ công.
![Untitled](https://github.com/user-attachments/assets/f48fede4-8756-479e-83d1-3bb984511090)

3. Nhập thông tin demo cho các bảng
- 3.1. Bảng Nguoi_Dung
![image](https://github.com/user-attachments/assets/c7093143-c48d-45e7-81ba-a21df04f7a07)

- 3.2. Bảng Phim
![Untitled](https://github.com/user-attachments/assets/3ce31596-1406-4c4b-a6ab-5ab88f86d4b7)

- 3.3. Bảng Rạp_Phim
