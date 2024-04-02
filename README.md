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
Ở phần thay đổi password này cho phép truyền tham số qua URL nên có thể bị tấn công CSRF bằng cách thay đổi param truyền vào URL 
![image](https://github.com/chi442000/CSRF/assets/84699930/b13809ba-0830-4915-bed3-75a681650cfd)
####  POST Requests
Ngược lại nếu trình duyệt web chấp nhận các yêu cầu POST, nội dung của yêu cầu POST có thể làm phức tạp cuộc tấn công CSRF hơn một chút. Tình huống đơn giản nhất liên quan đến một yêu cầu POST với content-type applica-tion/x-www-form-urlencoded hoặc text/plain. Content-type là một header mà trình duyệt có thể bao gồm khi gửi yêu cầu HTTP. Nó cho người nhận biết phần body của yêu cầu HTTP được mã hóa như thế nào. Ở đây, một ví dụ về một yêu cầu loại text/plain content-type: 
![image](https://github.com/chi442000/CSRF/assets/84699930/8a1fee30-dddb-45ee-bc3c-c12211506354)
Bây giờ, trong tình huống này, có thể một trang web độc hại có thể tạo một `form` HTMl ẩn và gửi nó một cách âm thầm đến trang đích mà nhạn nhân không biết. `Form` có thể được sử dụng để gửi yêu cầu POST hoặc GET tới URL và thậm chí có thể gửi các tham số (parameters) và giá trị của chúng. Dưới đây là một ví dụ về một số mã độc:
![image](https://github.com/chi442000/CSRF/assets/84699930/ef06a1ed-06ef-4ff1-b706-1d846ef37412)
### Attack-testing
Kiểm tra ứng dụng để xác định xem quản lý phiên của nó có dễ bị tấn công hay không. Nếu quản lý phiên chỉ dựa vào các giá trị phía máy khách (thông tin có sẵn cho trình duyệt) thì ứng dụng sẽ dễ bị tấn công. “Giá trị phía máy khách” đề cập đến cookie và thông tin xác thực HTTP (Xác thực cơ bản và các hình thức xác thực HTTP khác; không phải xác thực dựa trên biểu mẫu, là xác thực cấp ứng dụng).
Các tài nguyên có thể truy cập thông qua các yêu cầu HTTP GET rất dễ bị tấn công, mặc dù các yêu cầu POST có thể được tự động hóa thông qua JavaScript và cũng dễ bị tấn công; do đó, việc sử dụng POST một mình là không đủ để khắc phục sự xuất hiện của các lỗ hổng CSRF.
### Exploit
#### Explopit GET Requests
Đơn giản với GET requests ta chỉ cần thay đổi param truyền vào và lừa nạn nhân thực hiện thao tác truy cập vào URL đó. Hoặc có thể lợi dụng thẻ 
		`<img>` để truyền vào URL chứa param cần tấn công 
  ![image](https://github.com/chi442000/CSRF/assets/84699930/a4250307-5ea3-462e-80ed-66f247b0bac4)
Kết quả là khi truy cập trang web thuộc sở hữu của kẻ tấn công, nó bao gồm thẻ `<img>` trong phản hồi HTTP và trính duyệt sau đó thực hiện yêu cầu HTTP GET. Trình duyệt gửi cookie xác thực, để lấy những gì nó nghĩ là hình ảnh khi thực tế nhận được yêu cầu, xử lý URL trong thuộc tính thẻ src và xử lý thao tác mà hacker mong muốn. 
#### Explopit POST Requests
Trong trường hợp POST, mẫu sau có thể được sử dụng.
		1. Tạo một trang HTML
		2. tương tự như hiển thị bên dưới
		3. Lưu trữ HTML trên một trang web độc hại hoặc bên thứ ba
		Gửi liên kết của trang cho (những) nạn nhân và khiến họ nhấp vào liên kết đó.
  ![image](https://github.com/chi442000/CSRF/assets/84699930/4e55eab6-15d4-46dc-a1e2-6811e21df02c)


