### Sharing: chia sẻ dữ liệu trong mạng Lan trên Winserver với chức năng phân quyền cho từng nhóm người dùng

- Hoàn cảnh: Trong công ty sẽ có một server chạy AD chứa database của người dùng và nhóm người dùng được quản lý bằng một tên miền. Và có một server chạy là File Server để chứa dữ liệu cả công ty. Con này sẽ thể gắn rất nhiều ổ cứng để chia Raid tùy mục đích backup dữ liệu hay tăng tốc độ đọc dữ liệu.

- Ý tưởng làm: Server chạy FileServer sẽ join vào domain của Server chạy AD để truy cập được vào cơ sở dữ liệu người dùng của AD. Trên File server sẽ chia ra các thư mục để lưu dữ liệu của từng phòng ban trong công ty và khi join vào Domain thì File Server có thể phân quyền để tùy vào người dùng chỉ có thể truy cập được vào thư mục dữ liệu của phòng ban họ.

- Thực hiện: https://www.youtube.com/watch?v=TshHR0Zk1Vw

Chú ý:

Đây là quyền chỉ cho user administrator, kiennd truy cập thư mục share này qua mạng Lan. (Ví dụ thư mục share trên Server thì Client đăng nhập user kiennd mới truy cập được thư mục share này) Những user khác không được truy cập

![](/image/share1.png)



Đây là quyền của các User hiện có (trên chính Server share thư mục) để được quyền truy cập thư mục trên chính server đó => Với user kiennd phải có "2 quyền". Quyền vào được thư mục share trên máy client và quyền được truy cập thư mục này trên Server share thư mục (Bản chất để User kiennd vào được thư mục share trên client thì phải có quyền Sharing thưc mục trên Server và quyền được truy cập thư mục đó trên Server )

![](/image/share2.png)

### Tạo Shadow Copies: Là giải pháp backup dữ liệu của cả một volume tại một điểm thời gian

- Thực hiện: https://www.youtube.com/watch?v=P0x6G4RDRyk

- Note: Khi Restore lại dữ liệu thì dữ liệu hiện tại của Volume sẽ bị xóa hết để khôi phục lại dữ liệu cũ. Nhược điểm: khi khôi phục không biết được dữ liệu nào là dữ liệu cũ (dữ liệu đang backup) và dữ liệu mới (dữ liệu hiện có trong Volume). Khi khôi phục phát là mất hết data hiện tại, khôi phục mỗi cái cũ

### Backup dữ liệu sử dụng: Window Server Backup. 

- Ý tưởng làm: Cài đặt Feature Window Server Backup và vào Tool => Window Server Backup. Tính năng của nó: Backup một lần (Backup Once) và Backup theo kế hoạch (Backup Schedual). Cái này hay ở là nó có thể cho phép tùy chọn dữ liệu nào trong Volume (File hay Thư mục) để khôi phục và có thể Backup tự động hàng hàng.

- Thực hiện: https://www.youtube.com/watch?v=P0x6G4RDRyk
