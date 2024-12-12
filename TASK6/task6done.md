# SQL Injection là gì 
- SQL injection (SQLi) là một lỗ hổng bảo mật web cho phép kẻ tấn công can thiệp vào các truy vấn mà ứng dụng thực hiện đối với cơ sở dữ liệu của ứng dụng.
- SQL injection là một kỹ thuật chèn mã có thể phá hủy cơ sở dữ liệu của bạn.
- Điều này có thể cho phép kẻ tấn công xem dữ liệu mà thông thường chúng không thể truy xuất được. Dữ liệu này có thể bao gồm dữ liệu thuộc về người dùng khác hoặc bất kỳ dữ liệu nào khác mà ứng dụng có thể truy cập.
## Có những loại tấn công SQL Injection nào?
-  **In-band SQLi (Classic)**: Là loại SQLi truyền thống, kết quả của câu truy vấn bị tấn công được trả về dưới dạng phần của ứng dụng web. Ví dụ điển hình là tấn công thông qua các trường nhập dữ liệu như biểu mẫu.
-  **Inferential (Blind)** SQLi: Khi dữ liệu nhạy cảm được lấy từ cơ sở dữ liệu mà không hiển thị trực tiếp trên ứng dụng web, tin tặc phải suy luận thông qua các phản hồi khác như HTTP response code.
-  **Out-of-band SQLi**: Tin tặc có thể truyền dữ liệu nhạy cảm trực tiếp từ cơ sở dữ liệu tới một máy chủ khác thông qua kỹ thuật như DNS hoặc ghi vào một tệp.
- **Union-based SQLi**: Kết hợp nhiều câu truy vấn SQL lại với nhau bằng câu lệnh `UNION` để trích xuất nhiều dữ liệu hơn.
- **Error-based SQLi**: Khai thác các thông báo lỗi sinh ra bởi cơ sở dữ liệu để trích xuất thông tin và cấu trúc của cơ sở dữ liệu.
- **Time-based Blind SQLi**: Khi ứng dụng không trả về kết quả SQL Injection, tin tặc có thể suy luận thông qua sự chậm trễ trong thời gian đáp ứng để truy xuất dữ liệu.
