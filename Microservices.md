### Microservices

1. Monolith
- một ứng dụng lớn trong kiến trúc Monolith:
    1. khó deploy (một thay đổi nhỏ cần phải deploy cả khối lớn),
    2. dẫn đến thời gian release kéo dài,
    3. khả năng mở rộng hạn chế (ứng dụng lớn nên mở rộng quy mô sẽ tốn nhiều tài nguyên, toàn bộ ứng dụng cần mở rộng ngay cả khi chỉ có 1 phần của nó cần nhiều dung lượng hơn)
    4. sự cố định về công nghệ, toàn bộ ứng dụng được xây dựng trên một nền tảng công nghệ duy nhất dẫn đến việc áp dụng công nghệ mới trở thành thách thức
⇒ microservices

2. Microservices
   1. là những services nhỏ, độc lập và hoạt động cùng nhau
   2. mỗi service chạy quy trình riêng và giao tiếp với nhau thường thông qua API
   3. các service này có thể được viết bằng các ngôn ngữ lập trình khác nhau và có thể sử dụng các công nghệ lưu trữ dữ liệu khác nhau
   
3. Lợi ích 
   1. Tính linh hoạt: có thể áp dụng công nghệ và quy trình mới cho từng service. Dễ dàng hơn trong khi thử và chuyển đổi công nghệ
   3. Khả năng mở rộng động: chỉ mở rộng các service cần thiết, giảm chi phí 
   4. Quá trình release nhanh hơn: các service nhỏ và độc lập có thể developed, tested, deployed nhanh hơn

4. Thách thức và giải pháp
   1. Spring Cloud 
      1. Centralized configuration: quản lý các cấu hình của các microservices trong GIT  repository
      
      ![img.png](images/img.png)
      2. Load balancing (cân bằng tải): giúp phân phối các request một cách linh hoạt
      
      ![img_1.png](images/img_1.png)
      3. Service discovery: tự động phát hiện các microservices
      4. Distributed tracing: giúp xác định chính xác service nào khi nó xảy ra lỗi và điều gì đang gây ảnh hưởng tới performance của ứng dụng.
      5. Edge server: gần người dùng, nó giống như gateway, một điểm vào duy nhất (single entry point) cho các microservices       
      6. Fault tolerance: khả năng chịu lỗi: một microservice bị lỗi không ảnh hưởng đến service khác 
   2. Docker
      - triển khai nhất quán các service, 
      - làm cho ngôn ngữ lập trình và môi trường trở nên độc lập
   3. Kubernetes
   
      - cung cấp service discovery, load balancing, release mgmt,...
      - 