# Lỗ hổng File Inclusion
## Lỗ hổng File Inclusion là gì ?
- Lỗ hổng File Inclusion (bao gồm file) là một lỗ hổng bảo mật thường xuất hiện trong các ứng dụng web, xảy ra khi ứng dụng cho phép người dùng chỉ định tệp tin được đưa vào (**include**) và không kiểm tra hoặc xử lý hợp lệ các tham số đầu vào. Điều này có thể dẫn đến việc kẻ tấn công chèn hoặc tải các tệp tin độc hại, gây ra rủi ro lớn cho hệ thống.
## Lỗ hổng Local file inclusion(LFI)
- Lỗ hổng Local file inclusion nằm trong quá trình `include file` cục bộ có sẵn trên server. Lỗ hổng xảy ra khi đầu vào người dùng chứa đường dẫn đến file bắt buộc phải include. Khi đầu vào này không được kiểm tra, tin tặc có thể sử dụng những tên file mặc định và truy cập trái phép đến chúng, tin tặc cũng có thể lợi dụng các thông tin trả về trên để đọc được những tệp tin nhạy cảm trên các thư mục khác nhau bằng cách chèn các ký tự đặc biệt như `/`, `../`, `-`.
- Lỗi LFI thường đi kèm với lỗi về Upload. Kẻ tấn công upload một file có chứa mã php lên server mà không cần thiết file đó phải có kiểu là .php. Sau đó sử dụng LFI này để đọc ra nội dụng file đã upload lên. Khi server đọc các file này, gặp mã php sẽ thực thi các mã này và như thế là thực hiện ý đồ của hacker.
- 
