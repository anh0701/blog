### APIs
API (Application Programming Interface) 
là một giao diện lập trình ứng dụng, cho phép các phần mềm hoặc dịch vụ giao tiếp và tương tác với nhau.API hoạt động như một cầu nối, giúp các ứng dụng có thể truy cập và sử dụng các chức năng hoặc dữ liệu từ một ứng dụng hoặc dịch vụ khác một cách dễ dàng.
#### Vì sao cần API?
- Tăng cường khả năng tích hợp: cho phép các hệ thống khác nhau kết nối và làm việc cùng nhau.
- Tiết kiệm thời gian và công sức: giúp các nhà phát triển không cần phải viết lại các chức năng từ đầu.
- Tăng cường bảo mật: API có thể kiểm soát quyền truy cập và bảo vệ dữ liệu.
- Tạo điều kiện cho sự đổi mới: cho phép các nhà phát triển xây dựng các ứng dụng mới dựa trên các dịch vụ hiện có.
#### Cách API hoạt động
API hoạt động dựa trên mô hình client-server:
1. Client gửi yêu cầu đến server thông qua API
2. Server nhận yêu cầu, xử lý và gửi phản hồi lại cho client
3. Client nhận phản hồi và sử dụng dữ liệu hoặc chức năng được cung cấp.
#### Authentication
##### 1. JWT
JWT (JSON Web Token) là một chuẩn mở (RFC 7519) dùng để tạo ra các token truyền tải thông tin giữa các bên một cách an toàn dưới dạng JSON.

**Cấu trúc của JWT**

JWT gồm ba phần chính, được phân tách bởi dấu chấm (.):
- Header: Chứa thông tin về kiểu token và thuật toán mã hóa, VD: `{"alg": "HS256", "typ": "JWT"}`
- Payload: Chứa dữ liệu (claims) mà bạn muốn truyền tải, VD: `{"sub": "1234567890", "name": "John Doe", "admin": true}`
- Signature: Được tạo ra bằng cách mã hóa header và payload với một khóa bí mật hoặc một cặp khóa công khai/riêng tư

**Làm sao JWT hoạt động?**

Khi một người dùng đăng nhập, server sẽ tạo một JWT với các thông tin cần thiết và gửi lại cho client. Client sẽ lưu trữ JWT này, thường là trong local storage hoặc session storage.Khi client thực hiện các yêu cầu tiếp theo, JWT sẽ được gửi kèm theo (thường là trong header của HTTP request).Server sẽ kiểm tra JWT để xác thực và phân quyền.

**Ưu điểm của JWT**
- Độc lập: JWT không phụ thuộc vào cơ sở dữ liệu hoặc session server-side để xác thực.
- Bảo mật: được mã hóa, giúp bảo vệ thông tin trong payload.
- Tiện lợi: JWT có thể chứa nhiều thông tin và dễ dàng truyền tải giữa các hệ thống khác nhau.

**Khi nào dùng JWT**
- Xác thực người dùng (authentication): thường được sử dụng để xác thực người dùng trong các ứng dụng web và di động.
- Ủy quyền (Authorization): có thể được sử dụng để phân quyền truy cập vào các tài nguyên cụ thể dựa trên thông tin trong payload.
##### 2. OAuth
OAuth (Open Authorization) là một chuẩn mở cho phép các ứng dụng của bên thứ ba có thể truy cập một số thông tin của người dùng trên một dịch vụ mà không cần phải cung cấp mật khẩu. Đây là một trong những phương pháp xác thực hiện đại giúp bảo mật và tiện lợi hơn.

**Cách hoạt động** 

 OAuth cho phép bạn cấp quyền truy cập cho ứng dụng bằng cách sử dụng một token thay vì chia sẻ mật khẩu của bạn.
1. Người dùng yêu cầu dịch vụ cấp quyền truy cập: Người dùng sẽ được chuyển hướng đến trang đăng nhập của dịch vụ yêu cầu xác thực (VD: Google, Facebook)
2. Người dùng đăng nhập và cấp quyền: Người dùng đăng nhập và cho phép ứng dụng truy cập các thông tin cụ thể.
3. Dịch vụ trả về token: Sau khi xác thực và cấp quyền, dịch vụ sẽ trả về một token cho ứng dụng.
4. Ứng dụng sử dụng token để truy cập: Ứng dụng sử dụng token này để truy cập các thông tin đã được người dùng cho phép.

**Lợi ích**
- Bảo mật: Người dùng không cần chia sẻ mật khẩu của họ với ứng dụng, giảm nguy cơ mất mật khẩu.
- Tiện lợi: Người dùng có thể dễ dàng cấp quyền truy cập mà không cần phải tạo tài khoản mới.
- Kiểm soát: Người dùng có thể quản lý và thu hồi quyền truy cập của các ứng dụng bất kì lúc nào.

**Các phiên bản của OAuth**
- OAuth 1.0a: Phiên bản đầu tiên, khá phức tạp và ít sử dụng hiện nay.
- OAuth 2.0: Phiên bản mới nhất, đơn giản hơn và được sử dụng rộng rãi.
##### 3. Basic Authentication
Là một phương thức xác thực đơn giản trong HTTP, trong đó user gửi tên đăng nhập và mật khẩu được mã hóa cơ bản (Base64) cùng với mỗi yêu cầu HTTP.Đây là một trong những phương thức xác thực phổ biến nhất nhưng cũng là 1 trong những phương thức ít an toàn nhất.

**Cách hoạt động**
1. Client gửi yêu cầu: Khi client gửi yêu cầu tới server, server sẽ trả về mã trạng thái 401 Unauthorized cùng với tiêu đề WWW-Authenticate yêu cầu xác thực.
2. Client gửi thông tin đăng nhập: Client sẽ mã hóa tên đăng nhập và mật khẩu bằng Base64 và gửi chúng trong tiêu đề Authorization của yêu cầu tiếp theo.
3. Server xác thực: Server xác thực: Server giải mã Base64 để lấy tên đăng nhập và mật khẩu, sau đó xác thực chúng để quyết định cấp quyền truy cập hay từ chối.

**Cú pháp của Basic Authentication**
```shell  
    Authorization: Basic base64(username:password)  
    #  ví dụ username = admin, password = password GET /protected-resource HTTP/1.1
    Host: example.comAuthorization: Basic YWRtaW46cGFzc3dvcmQ=
```
**Ưu điểm**
- Đơn giản và dễ triển khai: không yêu cầu cấu hình phức tạp hay cài đặt thêm phần mềm.
- Phổ biến: hỗ trợ rộng rãi trên các trình duyệt và ứng dụng.

**Nhược điểm**
- Không an toàn nếu không sử dụng HTTPS: thông tin đăng nhập có thể bị đánh cắp nếu không sử dụng kết nối bảo mật.
- Không hỗ trợ các tính năng bảo mật nâng cao: Như xác thực hai yếu tố hay token-based authentication.

**Cách cải thiện bảo mật**
- Sử dụng HTTPS: Đảm bảo kết nối an toàn để mã hóa thông tin đăng nhập.
- Sử dụng phương thức xác thực khác: Như OAuth, JWT hoặc token-based authentication để tăng cường bảo mật.
##### 4. Token Authentication
Là một phương thức xác thực an toàn và hiện đại, trong đó server tạo ra 1 token cho người dùng sau khi xác thực thành công.Token này này được sử dụng để xác thực các yêu cầu tiếp theo mà không cần phải gửi lại thông tin đăng nhập như tên người dùng và mật khẩu.

**Cách token authentication hoạt động**
1. Client gửi thông tin đăng nhập: client gửi yêu cầu đăng nhập cùng thông tin đăng nhập (tên người dùng và mật khẩu) tới server.
2. Server xác thực thông tin đăng nhập: server kiểm tra thông tin đăng nhập, nếu đúng sẽ tạo ra một token.
3. Client nhận token: client lưu trữ token này (thường là trong bộ nhớ tạm thời hoặc cookies).
4. Client gửi yêu cầu với token: trong các yêu cầu tiếp theo, client gửi token này trong header của yêu cầu HTTP.
5. Server kiểm tra token: server xác minh token nếu hợp lệ thì xử lý yêu cầu, không thì từ chối.
##### 5. Cookie Based Auth
##### 6. OpenID
##### 7. SAML
#### REST
##### 1. JSON APIs
##### 2. SOAP
##### 3. gRPC
##### 4. GraphQL
#### HATEOAS
#### Open API Specs
