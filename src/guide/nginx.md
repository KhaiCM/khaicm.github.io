# Learning Nginx

## What Is a Web Server ?

Máy chủ Web (Web Server) là máy tính mà trên đó cài đặt phần mềm phục vụ web, đôi khi người ta cũng gọi chính phần mềm đó là web server.
Máy chủ web lưu trữ và cung cấp nội dung của một trang web - chẳng hạn như văn bản, hình ảnh, video và dữ liệu ứng dụng - cho các khách hàng yêu cầu nó. Loại ứng dụng khách phổ biến nhất là trình duyệt web, trình duyệt này yêu cầu dữ liệu từ trang web của bạn khi người dùng nhấp vào liên kết hoặc tải xuống tài liệu trên trang được hiển thị trong trình duyệt.
Máy chủ web giao tiếp với trình duyệt web bằng Giao thức truyền siêu văn bản (Hypertext Transfer Protocol: HTTP). Nội dung của hầu hết các trang web được mã hóa bằng Ngôn ngữ đánh dấu siêu văn bản (Hypertext Markup Language: HTML). Nội dung có thể tĩnh (ví dụ: văn bản và hình ảnh) hoặc động (ví dụ: giá đã tính hoặc danh sách các mặt hàng mà khách hàng đã đánh dấu để mua). Để cung cấp nội dung động, hầu hết các máy chủ web hỗ trợ ngôn ngữ kịch bản phía máy chủ (server‑side scripting languages) để mã hóa logic nghiệp vụ vào giao tiếp. Các ngôn ngữ được hỗ trợ phổ biến bao gồm Active Server Pages (ASP), Javascript, PHP, Python và Ruby,...

Máy chủ web cũng có thể lưu nội dung vào bộ nhớ cache để tăng tốc độ phân phối nội dung thường được yêu cầu. Quá trình này còn được gọi là tăng tốc web .

## Máy chủ Web có cần Public IP Addresses ?

Để được người dùng bên ngoài truy cập vào mạng của nó, web server cần có Public IP Addresses. Tuy nhiên, để cải thiện bảo mật, các máy chủ web thường được "hidden" sau proxy server or load balancer. Hầu hết các trang web lớn đều có nhiều máy chủ web, với load balancer để phân phối lưu lượng truy cập trên chúng. Nhiều trang web cũng có thể chia sẻ địa chỉ IP công cộng của một máy chủ web và trình cân bằng tải sau đó sử dụng thông tin trong URL yêu cầu để xác định trang web nào nhận được yêu cầu của khách hàng.

## Load Balancing and Web Servers

Bộ cân bằng tải (Load balancers) cải thiện hiệu suất và độ tin cậy bằng cách phân phối khối lượng công việc trên nhiều máy chủ. Khi bộ cân bằng tải được tích hợp vào cơ sở hạ tầng của bạn, trước tiên một yêu cầu sẽ chuyển đến bộ cân bằng tải, điều này sẽ hướng nó đến máy chủ phụ trợ chính xác. Trong việc chọn một máy chủ, bộ cân bằng tải trước tiên sẽ kiểm tra máy chủ nào đang đáp ứng các yêu cầu một cách thích hợp. Sau đó, nó sử dụng một quy tắc được định cấu hình sẵn để chọn trong số các máy chủ khỏe mạnh.

## Giới thiệu về NGINX

NGINX là một máy chủ web hiệu suất cao được phát triển để hỗ trợ nhu cầu ngày càng cao của web hiện đại. Nó tập trung vào high performance, high concurrency và sử dụng tài nguyên thấp. Mặc dù nó chủ yếu được biết đến như một máy chủ web, nhưng cốt lõi của NGINX là một máy chủ proxy ngược (reverse proxy server).

Tuy nhiên, NGINX không phải là máy chủ web duy nhất trên thị trường. Một trong những đối thủ cạnh tranh lớn nhất của nó là Apache HTTP Server (httpd), được phát hành lần đầu tiên vào năm 1995. Mặc dù Apache HTTP Server linh hoạt hơn, quản trị viên máy chủ thường thích NGINX vì hai lý do chính:
- Nó có thể xử lý số lượng request đồng thời cao hơn.

- Nó có khả năng phân phối nội dung tĩnh nhanh hơn với mức sử dụng tài nguyên thấp.

Nginx xuất hiện sau Apache, với nhận thức rõ ràng hơn về các vấn đề đồng thời sẽ phải đối mặt với các trang web trên quy mô lớn. Tận dụng kiến ​​thức này, Nginx được thiết kế ngay từ đầu để sử dụng thuật toán xử lý kết nối theo hướng sự kiện, không đồng bộ, không chặn.