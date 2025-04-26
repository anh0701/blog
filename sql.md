# Tối ưu câu lệnh truy vấn

1. Chỉ SELECT những cột cần thiết
2. Dùng index đúng chỗ
3. Tránh dùng hàm lên cột trong Where
4. Dùng LIMIT để phân trang hoặc giới hạn kết quả
5. Join đúng kiểu, đúng điều kiện
6. Tránh subquery lồng quá sâu, dùng JOIN thay
7. Dùng các bảng tạm / materialized view nếu truy vấn nặng
8. Tránh OR trong WHERE dùng UNION ALL nếu được
9. Luôn kiểm tra bằng EXPLAIN/ EXPLAIN ANALYST
10. Dùng Catching nếu truy vấn lặp lại nhiều lần
