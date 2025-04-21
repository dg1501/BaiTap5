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

# BÀI LÀM
## Bổ xung thêm 1 (hoặc vài) trường phi chuẩn.
### 1. Khái niệm trường phi chuẩn: Là trường có thể tính toán ra được từ các trường khác, nhưng bạn vẫn chủ động lưu nó vào bảng để tăng tốc truy vấn hoặc phục vụ một mục đích cụ thể.
### 2. Thêm trường phi chuẩn cho bảng **Suất_Chiếu**
![image](https://github.com/user-attachments/assets/f2df226c-d780-4f36-9e8b-cf39ab29d370)

- 2.1. Tại sao lại thêm trường phi chuẩn doanh thu? Tại vì khi đặt vé, chọn suất chiếu, nếu hệ thống có nhiều vé, việc tính tổng mỗi lần truy vấn (SUM(Đặt_Vé.tong_tien) GROUP BY ma_chieu) sẽ rất tốn tài nguyên. Việc lưu sẵn doanh_thu giúp đọc nhanh hơn.

+ Thay vì phải tính lại thủ công khi cần, ta lưu luôn trường giờ kết thúc để tiết kiệm thời gian truy vấn, dễ dàng lọc suất còn trống, tránh trùng lịch chiếu khi cần.

- 2.2. Sử dụng lệnh để tiến hành thêm thay vì thêm thủ công.
![image](https://github.com/user-attachments/assets/fd9f7ac3-7653-40af-8bbf-14516dd7c781)

### 3. Nhập thông tin demo cho các bảng
- 3.1. Bảng Nguoi_Dung
![image](https://github.com/user-attachments/assets/c7093143-c48d-45e7-81ba-a21df04f7a07)

- 3.2. Bảng Phim
![Untitled](https://github.com/user-attachments/assets/54899bbc-7b2b-4b32-8fd8-d3111255608d)

- 3.3. Bảng Rạp_Phim
![Untitled](https://github.com/user-attachments/assets/41228de7-4a34-4ec0-89f1-25f6cc764142)

- 3.4. Bảng Suất_Chiếu
![Untitled](https://github.com/user-attachments/assets/5a0c8567-a4bd-4c66-8759-ac95f3a62e0b)

- 3.5. Bảng Đặt_Vé
![Untitled](https://github.com/user-attachments/assets/5e184700-f420-405a-b568-4142aefe7a87)

### 4. Viết TRIGGER cho Bảng Đặt_Vé
![image](https://github.com/user-attachments/assets/7e6fc75a-8f7c-4327-87e7-1e7ea3804c3a)

- 4.1. Sau khi hoàn thành việc tạo Trigger ta tiến hành kiểm tra như sau:
+ Ban đầu ta có trường doanh thu ở bảng Suất_Chiếu là giá trị NULL
![Untitled](https://github.com/user-attachments/assets/b029755c-d1d9-4a14-ac1b-f72fece6b108)

+ Kết quả đạt được khi thay đổi dữ liệu ở bảng Đặt_Vé
![Untitled](https://github.com/user-attachments/assets/325e3aff-ef2a-4493-9e7e-ef0426caffc9)

- 4.2. CODE
``` 
CREATE TRIGGER TR_CapNhatDoanhThu_Ve
ON Đặt_Vé
AFTER INSERT, DELETE, UPDATE
AS
BEGIN
    SET NOCOUNT ON;
    UPDATE SC
    SET SC.doanh_thu = ISNULL(SC.doanh_thu, 0) - ISNULL(D.tong_tien, 0)
    FROM Suất_Chiếu SC
    JOIN deleted D ON SC.ma_chieu = D.ma_chieu;
    UPDATE SC
    SET SC.doanh_thu = ISNULL(SC.doanh_thu, 0) + ISNULL(I.tong_tien, 0)
    FROM Suất_Chiếu SC
    JOIN inserted I ON SC.ma_chieu = I.ma_chieu;
END;
```

### 5. Công dụng của Trigger trong đồ án **ĐẶT VÉ XEM PHIM ONLINE**
- Trigger TR_CapNhatDoanhThu_Ve đã được xây dựng và áp dụng thành công trên bảng Đặt_Vé nhằm tự động cập nhật cột doanh_thu trong bảng Suất_Chiếu mỗi khi có thao tác thêm, xóa hoặc chỉnh sửa vé.

- Việc sử dụng trigger giúp:

+ Tự động hóa quá trình tính toán doanh thu mà không cần người dùng can thiệp thủ công.

+ Đảm bảo tính toàn vẹn dữ liệu, tránh trường hợp doanh_thu bị sai lệch hoặc bỏ quên khi cập nhật vé.

+ Tăng hiệu quả và độ tin cậy trong quản lý hệ thống rạp chiếu phim.

- Nhờ trigger này, hệ thống luôn phản ánh doanh thu thực tế của từng suất chiếu một cách chính xác và kịp thời, góp phần nâng cao chất lượng quản lý và hỗ trợ ra quyết định trong quá trình vận hành rạp phim.
