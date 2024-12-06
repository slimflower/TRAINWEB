---
title: Task 4

---

# PICO CTF
## GET AHEAD
- Khi truy cập vào trang web ta thấy được giao diện với 2 nút có thể thay đổi màu giao diện trang web
- Khi kiểm tra thử html của trang ta không nhận thấy có gì thay đổi
- Vì vậy chúng ta hãy để ý đến đề vài `GET AHEAD` có thể thay đổi giữa phương thức GET sang HEAD vì vậy chúng ta hãy sài brup suite để tìm ra lá cờ 
- flag : `picoCTF{r3j3ct_th3_du4l1ty_70bc61c4}`
## COOKIES
- 
# ROOT-ME
## HTTP - IP restriction bypass
- Để truy cập vào web mà không cần đăng nhập chúng ta cần sử dụng `X-Forwarded-For` trong request 
- `X-Forwarded-For: 192.168.1.100`
- flag : `Ip_$po0Fing`
## HTTP - User-agent
- khi truy cập vào đường liên kết chúng ta sẽ nhận được một gợi s từ web `Wrong user-agent: you are not the "admin" browser!` ,chúng ta phải trở thành admin thì mới có thể tìm thấy flag
- sử dụng brup suite để repeater để edit user-agent thành admin
- flag : `rr$Li9%L34qd1AAe27`
## HTTP - Headers
- khi truy cập vào trang web chúng ta sẽ nhận được gợi ý `Content is not the only part of an HTTP response!`
- chúng ta sẽ sử dụng brup suite để xem response của headers
- chúng ta sẽ thấy `Header-RootMe-Admin: none` ở response .Vì vậy chúng ta cần sửa thành true ở request.
- flag : `HeadersMayBeUseful`

## HTTP - POST 
- khi truy câpj vào trang web chúng ta sẽ thấy gợi ý `Here is my new game. It's not totally finished but I'm sure nobody can beat me! ;)
Rules: click on the button to hope to generate a great score
Score to beat: 999999`.Chúng ta cần đổi số ở resquest lớn hơn 999999 
- chúng ta sử dụng brup suite để sửa request 
- flag : `H7tp_h4s_N0_s3Cr37S_F0r_y0U`
