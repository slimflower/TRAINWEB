---
title: Task1

---

# I. HTTP 
## 1. The HTTP Protocol là gì ?
- HTTP <Hypertext Transfer Protocol> là giao thức truyền tải siêu văn bản.
- The HTTP Protocol là giao thức HTTP cho phép `Web Client`<máy khách>  và `Web Server`<máy chủ> giao tiếp với nhau.
- Là nền tảng cho hoạt động cho ***World Wide Web<WWW>***.
- HTTP là một giao thức ứng dụng của bộ giao thức TCP/IP < *các giao thức nền tảng cho internet*>.
### Cách thức hoạt động của HTTP:
     1. Máy khách (web client) gửi một yêu cầu HTTP đến máy chủ web thông qua mạng internet.
     2. Máy chủ web (web server) nhận yêu cầu,xử lý nó và gửi phản hồi về lại máy khách.
     3. Máy khách nhận phản hồi từ máy chủ,sau đó trình duyệt sẽ hiển thị nội dung trang web hoặc dữ liệu cho người dùng.
    
    
## 2. HTTP Requests
- HTTP Request Method là yêu cầu HTTP chỉ ra hành động mong muốn được thực hiện trên tài nguyên đã xác định.
### Cấu trúc của một HTTP requests:
`I.Request-line= Phương thức + URI-request + Phiên bản HTTP`.
II. **URL(Uniform Resource Locator)** : Địa chỉ tài nguyên mà web client muốn truy cập.
III. **Tiêu đề yêu cầu (Request Headers)** : Chứa các thông tin bổ sung về yêu cầu.Một số loại nội dung mà web client chấp nhận được Accept-Charset, Accept-Encoding, Accept-Language, Authorization, Expect, From, Host, …
IV. **Phần thân yêu cầu (Request Body)**: Chỉ có khi phương thức là POST hoặc PUT, chứa dữ liệu mà máy khách muốn gửi đến máy chủ.
#### Một ví gì về GET:
    GET /index.html HTTP/1.1
    Host: www.example.com
    User-Agent: Mozilla/5.0
    Accept: text/html

    
## 3. HTTP Responses
- HTTP Responses là phản hồi của HTTP 
- Máy chủ nhận<server> yêu cầu và gửi lại một phản hồi HTTP chứa tài nguyên được yêu cầu,HTML, CSS,JavaScript, hoặc hình ảnh. Phản hồi cũng chứa mã trạng thái HTTP để cho biết tình trạng của yêu cầu (thành công, lỗi, không tìm thấy trang, v.v.).
### Một cấu trúc HTTP Responses:
       Status-line = Phiên bản HTTP + Mã trạng thái + Trạng thái
    I. Mã trạng thái(Status-code): Chỉ báo kết quả yêu cầu.Các mã phổ biến:
         1).200 OK: Yêu cầu thành công.
         2).404 Not Found: Tài nguyên không tồn tại.
         3).500 Internal Server Error: Lỗi máy chủ.
    II. Header: Thông tin bổ sung về phản hồi, ví dụ như loại dữ liệu trả về.
    III. Body: Nội dung chính của phản hồi, ví dụ như trang HTML, dữ liệu JSON, v.v.
#### Một HTTP Responses 
      HTTP/1.1 200 OK
      Content-Type: text/html
      Content-Length: 123
      <html>
        <body>Hello, world!</body>
      </html>
    
    
## 4. HTTP Methods
##### 1. GET 
###### Khái quát :
- Yêu cầu lấy dữ liệu từ máy chủ.
- Đây là phương thức phổ biến nhất,dùng để yêu cầu một trang web hoặc tài nguyên nào đó.
###### Đặc điểm:
- Không thay đổi trạng thái tài nguyên trên máy chủ.
- Dữ liệu yêu cầu được gửi trong URL (không bảo mật khi truyền dữ liệu nhạy cảm).
- Có thể được lưu vào bộ nhớ đệm (cache), hỗ trợ đánh dấu (bookmark).
- Ví dụ: Lấy danh sách sản phẩm từ một trang web.
##### 2. POST 
###### Khái quát : 
- Gửi dữ liệu đến máy chủ,thường dùng để gửi biểu mẫu hoặc tải tệp lên.
###### Đặc điểm : 
- Không được lưu vào bộ nhớ đệm hoặc đánh dấu (bookmark).
- Dữ liệu được gửi trong phần thân yêu cầu (body request).
- Ví dụ: Gửi form đăng ký hoặc thông tin đăng nhập.
##### 3. PUT : 
###### Khái quát : 
- Cập nhật tài nguyên trên máy chủ.
###### Đặc điểm : 
- Dữ liệu được gửi trong phần thân yêu cầu và nó sẽ thay thế toàn bộ tài nguyên hiện tại bằng dữ liệu mới.
- Ví dụ : Cập nhật thông tin một sản phẩm trong cơ sở dữ liệu.
##### 4. DELETE : 
###### Khái quát : 
-  Xoá tài nguyên trên máy chủ.
###### Đặc điểm : 
- Khi máy khách yêu cầu, tài nguyên tương ứng trên máy chủ sẽ bị xóa
- Ví dụ: Xóa một bài đăng trên trang blog.
##### 5. HEAD : 
###### Khái quát : 
 -  Giống như GET nhưng chỉ lấy tiêu đề của tài nguyên mà không lấy nội dung.
###### Đặc điểm : 
- Sử dụng để kiểm tra metadata của tài nguyên mà không cần tải toàn bộ nội dung.
- Ví dụ: Kiểm tra tiêu đề phản hồi để xác định xem tài nguyên có tồn tại hoặc đã được thay đổi.
##### 6. OPTIONS : 
###### Khái quát : 
- Trả về các HTTP mà máy chủ hỗ trợ đối với tài nguyên cụ thể.
###### Đặc điểm : 
- Trả về các phương thức mà máy chủ cho phép thực hiện trên tài nguyên đó.
- Ví dụ: Kiểm tra xem tài nguyên có hỗ trợ POST, PUT, DELETE hay không.
##### 7. PATCH : 
###### Khái quát : 
-  Áp dụng cho sửa đổi một phần tài nguyên đã xác định.
###### Đặc điểm : 
- Khác với PUT,PATCH chỉ thay đổi những trường nhất định trong tài nguyên,không thay thế toàn bộ.
- Ví dụ: Chỉ cập nhật giá của một sản phẩm,không thay đổi các trường khác.
##### 8. CONNECT 
###### Khái quát : 
- Thiết lập một kết nối tunnel đến máy chủ.
###### Đặc điểm : 
- Thường được sử dụng với các `proxy server` để thiết lập kết nối bảo mật (HTTPS)
- Ví dụ : Dùng để tạo kết nối an toàn client(khách) và máy server thông qua proxy.
##### 9.TRACE 
###### Khái quát : 
- Thực hiện một vòng lặp lại (loopback) với yêu nhận được trên máy chủ server.
###### Đặc điểm : 
- Sử dụng để chuẩn đoán các vấn đề trong mạng hoặc xác định thay đổi thực hiện bới proxy.
- Ví dụ: Kiểm tra xem dữ liệu yêu cầu có bị sửa đổi trên đường truyền hay không.
    
    
## 5. HTTP Headers
### Khái quát 
- HTTP headers là một phần quan trọng của giao thức HTTP, được sử dụng để trao đổi thông tin giữa máy khách (client) và máy chủ (server).
- Mỗi HTTP header bao gồm một `cặp khóa-giá trị`, với tên của header và nội dung tương ứng. HTTP headers có thể được sử dụng để truyền tải nhiều thông tin khác nhau như loại nội dung, phương thức xác thực, mã hóa, v.v.
### Các loại HTTP Headers : 
#### 1. Request Headers (Tiêu đề yêu cầu)
- **Đưa tới máy chủ server trong một yêu cầu được gửi từ client (máy khách).**
- ***Host***: Chỉ định tên miền và (nếu có) số cổng của tài nguyên được yêu cầu.
Ví dụ: `Host: www.example.com`
- ***UserAgent***:  Cung cấp thông tin về trình duyệt hoặc ứng dụng gửi yêu cầu.
Ví dụ:` User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)`
- ***Accept***: Xác định loại nội dung mà máy khách có thể xử lý.
 Ví dụ: `Accept: text/html,application/xhtml+xml`
- ***Authorization***: Chứa thông tin xác thực (token, username/password) để truy cập tài nguyên bảo vệ.
Ví dụ: `Authorization: Basic dXNlcjpwYXNz`
- ***Content-Type***: Xác định kiểu dữ liệu trong thân yêu cầu ( khi client gửi dữ liệu đến server).
Ví dụ : `Content-Type: application/json`
- ***Cookie***: Chứa thông tin phiên làm việc, thường được gửi lên để duy trì phiên người dùng.
Ví dụ : `Cookie: sessionId=abc123`
#### 2. Respone Headers (Tiêu đề phản hồi)
- **Được gửi bởi server để trả lời yêu cầu của client.**
- ***Content-Type***: Xác định loại nội dung mà máy chủ trả về (HTML,JSON,XML,v.v...)
Ví dụ : `Content-Type: text/html; charset=UTF-8`
- ***Content-Length***: Xác định kích thước dữ liệu trong thân phản hồi.
Ví dụ : `Content-Length: 348`
- ***Set-Cookie***: Dùng để gửi cookie từ máy chủ đến máy khách để lưu trữ thông tin phiên làm việc.
Ví dụ : `Set-Cookie: sessionId=abc123; HttpOnly`
- ***Cache-Control***: Chỉ định các quy tắc liên quan đến lưu trữ tạm thời(caching).
Ví dụ : `Cache-Control: no-cache, no-store`
- ***Location***:Dùng để chuyển hướng máy client tới một URL khác trong phản hồi với mã trạng thái 3xx(chuyển hướng).
Ví dụ : `Location: https://example.com/new-page`
- ***WWW-Authenticate***: Yêu cầu máy khách cung cấp thông tin xác thực để truy cập tài nguyên.
Ví dụ : `WWW-Authenticate: Basic realm="Access to the site"`
#### 3. Entity Headers(Tiêu đề thực thể)
- ** Áp dụng cho thân của thông điệp HTTP và mô tả nọi dung thực thể đó.
- ***Content-Encoding***: Cho biết kiểu mã hoá(như gzip,compress) được áp dụng cho nội dung.
Ví dụ : `Content-Encoding: gzip`
- ***Content-Language***: Chỉ định ngôn ngữ của tài liệu.
Ví dụ : `Content-Language: en`.
- ***Content-Location***: Địa chỉ thay thế tài nguyên(nếu khác URL yêu cầu).
Ví dụ : `Content-Location: /documents/file.pdf`.
- ***Last-Modified***: Xác định thời gian cuối cùng tài nguyên đó được thay đổi.
Ví dụ : `Last-Modified: Wed, 21 Oct 2020 07:28:00 GMT`.
#### 4.General Headers(Tiêu đề chung)
- **Áp dụng cho cả yêu cầu và phản hồi**.
- ***Connection***: Điều khiển việc giữ kết nối mở sau khi xử lý yêu cầu.
Ví dụ : `Connection: keep-alive`
- ***Date***: Thời gian mà thông điệp được gửi.
Ví dụ : `Date: Tue, 15 Nov 2020 08:12:31 GMT`
    
    
#  II.URLs
## I. Khái quát 
- URLs được viết tắt là ***Uniform Resource Locator*** có nghĩa là vị trí của một trang web trên internet.
-  URL được sử dụng để truy cập vào tài nguyên đó thông qua trình duyệt hoặc các phần mềm mạng khác.
## II. Cấu trúc của URLs
-  Có 6 phần quan trọng trong 1 cấu trúc URL : 
### 1. Scheme(Giao Thức)
- Giao thức với chức năng cung cấp cho trình duyệt biết cách giao tiếp với máy chủ của trang web để gửi và truy xuất thông tin. Nói cách khác, đây là thứ cho phép một URL hoạt động.
- Các giao thức thông thường là : 
    
      1. HTTP :http:// (Hypertext Transfer Protoco), không mã hoá.
      2. HTTPS: https:// (Hypertext Transfer Protocol Secure), mã hoá dữ liệu để bảo mật.
      3. Các giao thức khác : ftp://(File Transfer Protocol), mailto:// (để gửi email), file:// (truy cập tệp cục bộ).
      4. Ví dụ : https://play.picoctf.org/login?redirect=/login
### 2. Domain ( Tên Miền)
- Phần này xác định địa chỉ của máy chủ chứa tài nguyên.
- Ví dụ : `play.picoctf.org`
### 3. Port (Cổng)
- Không phải lúc nào cũng xuất hiện, nhưng khi có, nó xác định cổng cụ thể mà dịch vụ lắng nghe trên máy chủ. Cổng mặc định thường không được ghi rõ:
    
        - HTTP thường là cổng 80.
        - HTTPS thường là cổng 443.
        Ví dụ: https://www.example.com:8080 (Cổng 8080 được chỉ định).
### 4. Path ( Đường Dẫn)
- Đường dẫn đến tài nguyên cụ thể trên máy chủ. Nó có thể là thư mục hoặc tệp trên máy chủ.
- Ví dụ : `login?redirect=/login`
#### 5. Query String ( Chuỗi Truy Vấn)
- Phần này thường được bắt đầu bởi dấu ? và chứa các tham số để gửi dữ liệu đến máy chủ ,thường dùng trong truy vấn cơ sở dữ liệu hoặc gửi dữ kiệu từ from web.
- Các tham số thường có dạng cặp key=value,và các cặp được phân cách bởi dấu &.
- Ví dụ : `?id=123&category=books.`
### 6. Fragment( Mảnh)
- Bắt đầu bằng dấu #,được sử dụng để dẫn đến một phần cụ thể của tài nguyên (thường là một phần của trang web).
- Ví dụ : `#section2 sẽ dẫn đến phần "section2" của trang.`
#### Ví dụ về URL đầy đủ : 
    
        https://www.example.com:8080/products/item1?id=123&category=books#section2
- Trong ví dụ này : 

            - https://: Giao thức
            - www.example.com: Tên miền
            - :8080: Cổng
            - /products/item1: Đường dẫn đến tài nguyên
            - ?id=123&category=books: Chuỗi truy vấn với các tham số
            - #section2: Mảnh dẫn đến phần "section2" của trang.
    
    
    
## III. COOKIES
### Khái quát 
- Cookies là một tập hợp các tệp thông tin do chính người dùng tạo ra mỗi lần truy cập vào một website nào đó và để lại dữ liệu trình duyệt web. 
- Thông tin Cookie sẽ thường được lưu dưới dạng cặp name-value.
### Phân loại Cookies
#### Cookies phiên ( Session cookies)
- Tồn tại tạm thời trong khi người dùng đang duyệt web và sẽ bị xoá khi họ đóng trình duyệt.
- Chúng được sử dụng để theo dõi các hành động của người dùng trong một phiên làm việc trên trang web
Ví dụ: `Giữ thông tin giỏ hàng.`
#### Cookies lâu dài(Persistent cookies):
- Lưu trữ trong một khoảng thời gian cụ thể,ngay cả khi người dùng đã đóng trình duyệt.
- Thường được sử để ghi nhớ thông tin đăng nhập hoặc tuỳ chọn trang web của người dùng cho lần truy cập sau.
### Chức năng của cookies
- ***Ghi nhớ phiên đăng nhập***: Giúp người dùng không cần phải đăng nhập lại mỗi khi truy cập trang web.
- ***Ghi nhớ các tuỳ chọn các nhân***: Như ngôn ngữ,kích thước phông chữ hoặc giao diện người dùng.
- ***Theo dõi hoạt động người dùng***:Giúp nhà quản trị trang web hiểu cách mà người dùng tương tác với trang web,từ đó tối ưu hoá trải nghiệm người dùng.
- ***Quảng cáo được cá nhân hoá***:Cookies cho phép theo dõi các hoạt động của người dùng trên nhiều trang web khác nhau để hiển thị quảng cáo phù hợp.
### Quyền riêng tư và bảo mật
- Cookies có thể chứa thông tin người dùng, nhưng chỉ thông tin mà họ đã cung cấp.
- Một số cookies có thể gây lo ngại về quyền riêng tư,đặc biệt là khi theo dõi hành vi người dùng qua nhiều trang web(cookies như bên thứ ba).
- Để bảo vệ quyền riêng tư,các trình duyệt hiện tay thường cung cấp các tính năng cho phép người dùng kiểm soát và xoá cookies bất cứ lúc nào.
### Cách quản lí cookies 
- Người dùng có thể xoá cookies hoặc tuỳ chỉnh cài đặt cookies qua trình duyệt của mình.
- Một số trang web yêu cầu người dùng cho phép lưu trữ cookies ,đặc biệt là khi quy định vè bảo mật dữ liệu chung của EU(GDPR) có hiệu lực,yêu cầu các trang web phải minh bạch về việc sử dụng cookies.
## III. Status Codes
### Khái quát 
- **Status Codes** là mã trạng thái .Các mã phản hồi mà máy chủ gửi về thông báo cho trình duyệt hoặc ứng dụng biết về trạng thái của yêu cầu HTTP.
- Các mã này thường là một con số ba chữ số và được chia thành các nhóm theo ý nghĩa cụ thể .
### Phân Loại 
#### 1xx (Informational) - Thông tin:
- Các mã trạng thái trong nhóm này chỉ ra rằng yêu cầu đã được nhận và đang được xử lý.
Ví dụ : ***100 Continue***: `Máy chủ đã nhận một phần yêu cầu và client có thể tiếp tục gửi phần còn lại.`
#### 2xx (Success) - Thành công:
- Yêu cầu đã được xử lý thành công.
Ví dụ : ***200 OK***: `Yêu cầu đã thành công và thông tin mong đợi được trả về`
#### 3xx (Redirection) - Chuyển hướng:
- Yêu cầu cần có thêm hành động để hoàn tất.
Ví dụ : ***301 Moved Permanently***:` Tài nguyên đã được chuyển sang địa chỉ khác vĩnh viễn.`
#### 4xx (Client Error) - Lỗi từ phía client:
- Máy chủ không thể xử lý yêu cầu do lỗi từ phía client (người dùng).
Ví dụ : 
- ***400 Bad Request***: `Yêu cầu không hợp lệ hoặc không thể hiểu được.`
- ***401 Unauthorized***: `Client không có quyền truy cập tài nguyên (cần xác thực).`
- ***404 Not Found***: `Không tìm thấy tài nguyên yêu cầu.`
#### 5xx (Server Error) - Lỗi từ phía máy chủ:
- Máy chủ gặp sự cố khi xử lý yêu cầu.
Ví dụ : 
- ***500 Internal Server Error***: `Máy chủ gặp lỗi nội bộ và không thể hoàn tất yêu cầu.`
- ***502 Bad Gateway***: `Máy chủ trung gian nhận phản hồi không hợp lệ từ máy chủ khác.`
- ***503 Service Unavailable***: `Máy chủ tạm thời không khả dụng.`
## IV. Hypertext Transfer Protocol Secure
### Khái quát 
- HTTPS (Hypertext Transfer Protocol Secure) là một phiên bản an toàn của giao thức HTTP (Hypertext Transfer Protocol)
- Được sử dụng để truyền tải dữ liệu giữa trình duyệt web và máy chủ web.
### So sánh 
- Điểm khác biệt chính giữa HTTPS và HTTP là HTTPS sử dụng mã hóa SSL/TLS để bảo mật dữ liệu, đảm bảo rằng thông tin truyền tải giữa người dùng và máy chủ được bảo vệ khỏi các cuộc tấn công nghe lén (eavesdropping), tấn công trung gian (man-in-the-middle attack), và các hình thức tấn công khác.
## V. HTTP Proxies
### Khái quát 
- HTTP Proxy (hay Proxy HTTP) là một máy chủ trung gian đóng vai trò như một cầu nối giữa người dùng và Internet
-  Thay vì kết nối trực tiếp đến trang web hoặc tài nguyên trực tuyến mà bạn muốn truy cập, yêu cầu của bạn sẽ được gửi đến proxy, sau đó proxy sẽ tiếp tục gửi yêu cầu đó đến trang web hoặc tài nguyên mục tiêu.
- Khi nhận được phản hồi từ trang web, proxy sẽ trả dữ liệu lại cho bạn
#### Các đặc điểm và lợi ích của HTTP Proxies:
- Ẩn địa chỉ IP của người dùng:
- Kiểm soát truy cập
- Tăng cường bảo mật
- Tăng hiệu suất
- Vượt qua hạn chế địa lý
### Các loại HTTP Proxies phổ biến:
- ***Transparent Proxy***: Loại proxy này không ẩn địa chỉ IP của người dùng và thường được sử dụng để kiểm soát truy cập hoặc lưu trữ nội dung (cache).
- ***Anonymous Proxy***: Loại proxy này che giấu địa chỉ IP của người dùng nhưng vẫn tiết lộ rằng người dùng đang sử dụng một proxy.
- ***Elite/High Anonymity Proxy***: Proxy này che giấu cả địa chỉ IP của người dùng và việc họ đang sử dụng proxy, cung cấp mức độ ẩn danh cao hơn.
## VI. HTTP Authentication
### Khái quát 
- HTTP Authentication (Xác thực HTTP) là một cơ chế được sử dụng để xác minh danh tính của người dùng khi họ truy cập vào tài nguyên web được bảo vệ.
- Nó giúp kiểm soát truy cập và đảm bảo rằng chỉ những người dùng có quyền hợp lệ mới được phép truy cập vào các tài nguyên hoặc dịch vụ nhạy cảm
- **Các hoạt động**  : HTTP Authentication hoạt động thông qua các tiêu đề HTTP (HTTP headers) được gửi từ máy khách (client) tới máy chủ (server).
### Các phương thức HTTP Authentication chính:
#### 1. Basic Authentication (Xác thực Cơ bản)
##### Cách thức hoạt động
- Khi một người dùng truy cập vào tài nguyên được bảo vệ, máy chủ sẽ trả về mã trạng thái `HTTP 401 Unauthorized` cùng với tiêu đề yêu cầu xác thực `(WWW-Authenticate)`.
- Trình duyệt hoặc ứng dụng sẽ yêu cầu người dùng cung cấp tên đăng nhập (username) và mật khẩu (password).
- Thông tin xác thực (username và password) sẽ được mã hóa bằng Base64 và gửi tới máy chủ trong tiêu đề `Authorization`.
##### Nhược điểm 
- Basic Authentication không sử dụng bất kỳ cơ chế mã hóa bổ sung nào ngoài việc mã hóa bằng Base64 (không an toàn), vì vậy thông tin xác thực có thể bị đánh cắp nếu không được bảo mật bằng HTTPS.
- Ví dụ tiêu đề yêu cầu : 
   ` Authorization: Basic dXNlcm5hbWU6cGFzc3dvcmQ=`
#### 2. Digest Authentication (Xác thực Tiêu hóa)
##### Cách thức hoạt động : 
- Máy chủ trả về mã trạng thái `HTTP 401 Unauthorized `cùng với tiêu đề `WWW-Authenticate`, nhưng thay vì yêu cầu mật khẩu rõ ràng, `Digest Authentication` sẽ yêu cầu một mã băm (hash) của thông tin xác thực.
- Mật khẩu và thông tin liên quan (như nonce) sẽ được băm bằng thuật toán MD5 trước khi gửi đi =>> làm tăng bảo mật vì mật khẩu thực không bao giờ được gửi trực tiếp trong quá trình xác thực.
##### Lợi ích 
- An toàn hơn so với Basic Authentication vì mật khẩu không bao giờ được gửi dưới dạng văn bản thuần (plaintext) mà dưới dạng mã băm.
##### Nhược điểm 
- Mặc dù an toàn hơn Basic Authentication, nhưng Digest Authentication vẫn có thể bị tấn công với các kỹ thuật hiện đại, và ngày nay nó ít được sử dụng hơn, đặc biệt khi HTTPS trở nên phổ biến.
#### 3. Bearer Token Authentication (Xác thực bằng Mã thông báo Bearer)
##### Cách thức hoạt động 
- Thường được sử dụng trong các hệ thống `API RESTful và OAuth 2.0`.
- Khi người dùng đăng nhập thành công, họ nhận được một mã thông báo (token), mã này sau đó sẽ được gửi trong tiêu đề `Authorization` của mỗi yêu cầu tiếp theo.
- Mã thông báo có thể là một chuỗi dài, và nó thường có thời gian tồn tại giới hạn.
- Ví dụ : `Authorization: Bearer <access_token>`.
### Lợi ích 
- Token có thể được thu hồi hoặc thay đổi khi cần thiết mà không cần phải yêu cầu người dùng thay đổi mật khẩu.
- Token có thể chứa thông tin người dùng và quyền hạn, giúp đơn giản hóa việc kiểm tra xác thực và phân quyền.
####4. Token-based Authentication (Xác thực dựa trên mã thông báo)
##### Cách thức hoạt động:
- Người dùng đăng nhập và nhận được mã thông báo (token).
- Mỗi yêu cầu sau đó từ người dùng sẽ bao gồm token này để xác thực.
- Token thường được mã hóa, có thời gian tồn tại và có thể bị thu hồi nếu cần.
- Ví dụ: OAuth, JWT (JSON Web Token) là các ví dụ phổ biến về xác thực dựa trên token.
#### 5. Xác thực với OAuth 2.0
##### Cách thức hoạt động: 
- OAuth 2.0 là một giao thức ủy quyền cho phép người dùng cấp quyền truy cập cho ứng dụng bên thứ ba mà không cần phải chia sẻ thông tin đăng nhập.
- Người dùng sẽ đăng nhập qua một nhà cung cấp xác thực (như Google, Facebook), và một mã truy cập (access token) sẽ được cấp cho ứng dụng yêu cầu.


