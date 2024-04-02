# CSRF
### Contents
- [Khái niệm CSRF](https://github.com/chi442000/CSRF#Concept)
- [Phân loại](https://github.com/chi442000/CSRF#types-of-attacks)
    - [CSRF with GET Requests](https://github.com/chi442000/CSRF#get-requests)
    - [CSRF with POST Requests](https://github.com/chi442000/CSRF#post-requests)
- [Cách kiểm tra](https://github.com/chi442000/CSRF#attack-testing)
- [Khai thác](https://github.com/chi442000/CSRF#exploit)
    - [Exploit with GET Requests](https://github.com/chi442000/CSRF#exploit-get-requests)
    - [Exploit with POST Requests](https://github.com/chi442000/CSRF#exploit-post-requests)

### Concept
CSRF ( Cross Site Request Forgery) là kỹ thuật tấn công bằng cách sử dụng quyền chứng thực của người dùng đối với một website. CSRF là kỹ thuật tấn công vào người dùng, dựa vào đó hacker có thể thực thi những thao tác phải yêu cầu sự chứng thực. Hiểu một cách nôm na, đây là kỹ thuật tấn công dựa vào mượn quyền trái phép.
	CSRF còn được gọi là "session riding", "XSRF"
### Types of Attacks
#### GET Requests
CSRF with GET Requests là hình thức lợi dụng việc truyền param vào trong URL thông qua HTTP requests, kẻ tấn công có thể thay đổi giá trị của param truyền vào trong URL và đánh lừa nạn nhân thực hiện thao tác. 
![image](https://github.com/chi442000/CSRF/assets/84699930/59f84737-504d-4b6b-839e-3c63ab20829f)

####  POST Requests
### Attack-testing
### Exploit
#### Explopit GET Requests
#### Explopit POST Requests

