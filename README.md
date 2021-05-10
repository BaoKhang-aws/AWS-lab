**Nội dung**
- [Giới thiệu về Grafana](#giới-thiệu-về-grafana)
- [Các tính năng của Grafana](#các-tính-năng-của-grafana)

#### Giới thiệu về Grafana

**Grafana** là một phần mềm phân tích trực quan mã nguồn mở. Nó cho phép ta tạo nên các biểu đổ chỉ số dựa trên lượng dữ liệu không lồ đã thu thập được, từ đó giúp ta theo dõi được hoạt động của ứng dụng nói riêng và hệ thống nói chung. 
Bên cạnh đó sản phẩm còn cung cấp khả năng truy vấn tùy biến, trực quan hóa, tính năng cảnh báo và tìm kiếm các chỉ số bất kể chúng được lưu trữ ở đâu. Có thể nói rằng Grafana giúp biến đổi cơ sở dữ liệu chuỗi theo thời gian (TSDB) thành các biểu đồ và hình ảnh trực quan đẹp mắt được trình bày trên dashboard cho phép tùy chỉnh tuyệt vời.

Grafana có thể kết nối với gần như mọi nguồn dữ liệu có thể, chẳng hạn như Graphite, Prometheus, Influx DB, ElasticSearch, MySQL, PostgreSQL, v.v.
Nó giúp chúng ta theo dõi hành vi của người dùng, hành vi ứng dụng, tần suất xuất hiện lỗi trong quá trình sản xuất hoặc môi trường tiền sản xuất, loại lỗi xuất hiện và các tình huống theo ngữ cảnh khác nhau dựa trên dữ liệu liên quan mà nó được cung cấp.
Bên cạnh các giải pháp mà mã nguồn mở ban đầu cung cấp, còn có hai dịch vụ khác do nhóm Grafana cung cấp cho các doanh nghiệp được gọi là Grafana Cloud & the Enterprise.

#### Các tính năng của Grafana

Grafana cung cấp một số tinh năng như sau: 
- **Visualize**: Trực quan hóa một cách nhanh chóng và linh hoạt với vô số tùy chọn, trực quan hóa dữ liệu của bạn theo bất kỳ cách nào bạn muốn.
- **Dynamic Dashboards**: Cung cấp trang Dashboards động và có thể sử dụng lại với các biến mẫu xuất hiện dưới dạng danh sách thả xuống ở trang tổng quan. 
- **Explore Metrics**: Khai thác dữ liệu nhờ vào khả năng truy vấn nhanh chóng và chi tiết. Tách biệt khung nhìn và cung cấp khả năng so sánh giữa các khung thời gian khác nhau, các lệnh truy vấn khác nhau và nguồn dữ liệu khác nhau 
- **Explore Logs**: Khai thác dữ liệu nhờ vào khả năng chuyển đổi từ dữ liệu biểu đồ sang dữ liệu dạng nhật ký với bộ lọc đã được đánh nhãn từ trước. Cung cấp khả năng tìm kiếm một cách nhanh chóng dựa trên tất cả dữ liệu nhật ký đã lưu cũng như dữ liệu nhật ký thời gian thực. Grafana hoạt động tốt nhất với dữ liệu nguồn Loki nhưng trong tương lai nó cũng sẽ hỗ trợ rất tốt cho những nguồn dữ liệu khác nữa
- **Alerting**: Giúp định nghĩa các Alert rule một cách trực quan nhất dựa trên những biểu đồ hiển thị trên Dashboards. Trong tương lai, Grafana sẽ tiếp tục cải tiến cho phép gửi đánh giá và báo cáo tới các hệ thống khác như Slack, PagerDuty, VictorOps, OpsGenie.
- **Mixed Data Sources**: Khả năng biểu diễn dữ liêu hỗn hợp trên cũng một biểu đồ. Hoặc bạn có thể phân loại nguồn dữ liệu theo từng câu lệnh truy vấn, đồng tời cung cấp khả năng truy vấn đối với cơ sở dữ liệu tùy chỉnh.
- **Annotations**: Chú thích biểu đổ với nhiều nguồn dữ liệu sự kiện khác nhau. Khi rê chuột lên sự kiện, phần mềm sẽ cho ta biết thông tin chi tiết của sự kiện đó bao gồm cả các tag liên quan.
- **Ad-hoc Filters**: Bộ lọc đặc biệt cho phép bạn tạo nhanh chóng các bộ lọc khóa/giá trị mới, các bộ lọc này tự động được áp dụng cho tất cả các truy vấn sử dụng nguồn dữ liệu đó
