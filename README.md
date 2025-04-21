# Baitap5
# NguyenThiLinh_K225480106040
## SUBJECT: Trigger on mssql

A. Trình bày lại đầu bài của đồ án PT&TKHT:
1. Mô tả bài toán của đồ án PT&TKHT, 
   đưa ra yêu cầu của bài toán đó
2. Cơ sở dữ liệu của Đồ án PT&TKHT :
   Có database với các bảng dữ liệu cần thiết (3nf),
   Các bảng này đã có PK, FK, CK cần thiết
 
B. Nội dung Bài tập 05:
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

# A. Trình bày lại đầu bài của đồ án PT&TKHT:
  1.Yêu cầu của đồ án: Phân tích thiết kế hệ thống quản lý hiệu thuốc
  2.Cơ sở dữ liệu của hệ thống quản lý hiệu thuốc
## Tạo bảng Database mới mang tên QLHieuThuoc
![Screenshot 2025-04-21 151626](https://github.com/user-attachments/assets/ffb2f68f-efa8-46fa-b647-eb4ece0fc4d6)
## Tạo bảng mang tên Phieu_Nhap
![Screenshot 2025-04-21 152853](https://github.com/user-attachments/assets/bcfd738b-3e8d-4ec4-8ad1-2500863cfe8b)
## Tạo bảng mang tên Phieu_Xuất
![Screenshot 2025-04-21 152804](https://github.com/user-attachments/assets/d6e7ee6c-465a-49bb-bf1b-1dbc8b5313ad)
## Tạo bảng Khách Hàng
![Screenshot 2025-04-21 152812](https://github.com/user-attachments/assets/cc9d8263-a058-4a44-bae1-4afc768db404)
## Tạo bảng Sản Phẩm
![Screenshot 2025-04-21 152921](https://github.com/user-attachments/assets/0817589b-8c8c-47b4-a91d-00eecceddfba)
## Tạo bảng Nhà Cung Cấp
![Screenshot 2025-04-21 152820](https://github.com/user-attachments/assets/31abbc9f-afaa-4efd-8f79-ff300904309f)
## Tạo bảng chi tiết phiếu nhập
![Screenshot 2025-04-21 152755](https://github.com/user-attachments/assets/d6e1013e-0f46-4195-9137-d917c2c843fb)
## Tạo bảng chi tiết phiếu xuất
![Screenshot 2025-04-21 152804](https://github.com/user-attachments/assets/9b5681c6-3369-4550-a863-b436b4d62b75)
## Tạo bảng Log
![Screenshot 2025-04-21 154801](https://github.com/user-attachments/assets/500645a3-a4bc-4dd6-938b-0f3c330645c9)
## CÁC KHÓA NGOẠI LIÊN KẾT CHO CÁC BẢNG
![Screenshot 2025-04-21 153025](https://github.com/user-attachments/assets/411c815b-64cf-4beb-9f68-90aafb707511)
![Screenshot 2025-04-21 153106](https://github.com/user-attachments/assets/076a25f1-1ba2-4ad5-8fb3-fedf53a6e805)
![Screenshot 2025-04-21 152936](https://github.com/user-attachments/assets/ad2247c8-5f6e-4063-82f7-c42e84ba0c16)
![Screenshot 2025-04-21 152951](https://github.com/user-attachments/assets/33ca833d-b8fa-4cb5-913a-0d471c3563ce)
![Screenshot 2025-04-21 153007](https://github.com/user-attachments/assets/ac14bc7d-bde7-42fd-a42f-6b30829e3f20)
![Screenshot 2025-04-21 153124](https://github.com/user-attachments/assets/1677d983-5059-4a79-9a8c-0b066f149fc4)
![Screenshot 2025-04-21 153151](https://github.com/user-attachments/assets/33e05592-7c93-4ce1-bce8-2a410fb47ee0)
## Tạo bảng liên kết của Quản lý hiệu thuốc
![Screenshot 2025-04-21 155235](https://github.com/user-attachments/assets/5f307259-26c0-4513-ba56-b71865d21b0e)

B. Nội dung Bài tập 05:
1. Tạo csdl cho hệ thống quản lý hiệu thuốc
2. Bổ sung thêm trường phi chuẩn: Tính tổng số tiền và cảnh báo sô tiền vượt >10tr
3. Viết trigger cho bảng chi tiết phiếu xuất để đạt được mục tiêu
 - Bấm vào dấu "+" của bảng chi tiết phiếu xuất và chuột phải vào trigger rồi ấn new trigger   
![Screenshot 2025-04-21 160154](https://github.com/user-attachments/assets/255ed54b-a6fb-44d9-a135-008718756b86)
## Trigger tự động tính tổng tiền và cảnh báo tiển vượt >10Tr
- Ở đoạn code tính tổng tiền này có mục tiêu là tự động tính lại tổng số tiền của các phiếu xuất mỗi khi nó thay đổi, để phục vụ cho kiểm tra, giám sát hoặc các bước xử lý sau như cảnh báo, giúp cho hệ thống quản lý hiệu thuốc chạy mượt và chính xác hơn.
![Screenshot 2025-04-21 162336](https://github.com/user-attachments/assets/0db0c72a-47e2-42fe-9af0-ef1825adb8a1)
- Trigger cảnh báo tiền vượt >10tr
- Ở đoạn trigger này sẽ cho phép em thêm, sửa hoặc xóa chi tiết trong bảng Chi tiết phiếu xuất thì trigger sẽ tự động tính lại tổng tiền của các phiếu xuất bị ảnh hưởng
- Nếu tổng tiền vượt quá ngưỡng 10tr thì hệ thống nó sẽ cảnh báo 
![Screenshot 2025-04-21 145815](https://github.com/user-attachments/assets/365e8bae-d949-497a-a2d2-8720ba05b21e)
![Screenshot 2025-04-21 145825](https://github.com/user-attachments/assets/f160299c-756e-46c3-84f6-c17833354d91)
4. Nhập dữ liệu có kiểm soát, 
   nhằm để test sự hiệu quả của việc trigger auto run.
### Kiểm tra kết quả
  ![Screenshot 2025-04-21 144253](https://github.com/user-attachments/assets/3de20f18-4fcc-4e7b-b5ec-937a8cdbae1e)
5. Kết luận về Trigger đã giúp gì cho đồ án của em.
- 2 Trigger này giúp cho em có thể tự động tính cho mỗi phiếu xuất mỗi khi dữ liệu chi tiết bị thay đổi và nó hạn chế việc sai khi khi tính thủ công, cũng như tăng hiệu quả xử lý , không cần lưu trường tổng tiền vào trong bảng chính. Ngoài ra nó còn có thể cảnh báo khi số tiền vượt quá ngưỡng 10 triệu VNĐ, từ đó sẽ ghi lại log để theo dõi.Và nó còn kiểm soát các giao dịch lớn và phát hiện bất thường.
