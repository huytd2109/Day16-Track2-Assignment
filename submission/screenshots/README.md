# Ảnh bằng chứng

| File | Nội dung và nguồn | Giới hạn |
|---|---|---|
| [benchmark_terminal.png](benchmark_terminal.png) | Screenshot terminal local chạy `cat submission/benchmark_output.txt`, hiển thị toàn bộ log benchmark EC2 ngày 02/10/2026 17:55 (UTC+7). | Xem lại log đã lưu sau cleanup, không chạy lại benchmark. |
| [resource_usage.png](resource_usage.png) | Screenshot terminal local chạy `cat submission/resource_usage.txt`, có `top`, `free -h`, `ip -s link` thu qua SSH lúc benchmark đang chạy. | Không phải tài nguyên máy local hay peak trong fit. |
| [billing.png](billing.png) | Ảnh Console có sẵn do người dùng cung cấp, giữ nguyên. | Chỉ thấy tháng 4–9/2026, $0.00 và 0 dịch vụ; chưa chứng minh chi phí ngày lab 02/10/2026. |

Hai ảnh terminal được chụp từ cửa sổ xterm thực trong màn hình ảo Xvfb ngày 04/10/2026. Nội dung log hiển thị nguyên văn; dòng chú thích phía trên ảnh ghi rõ đây là xem lại log. Chi tiết nguồn và SHA-256 ở `../evidence/screenshot_provenance.json`.

Để hoàn thiện Billing: mở Bills/Cost Explorer, chọn ngày 02/10/2026 hoặc khoảng bao gồm ngày đó, phân nhóm Service và chụp cả bộ lọc lẫn bảng/biểu đồ. Khoảng API tương ứng là Start=2026-10-02, End=2026-10-03 (End không bao gồm). Nếu không có dữ liệu, chụp đúng kỳ và ghi lại thông báo thực tế; không suy ra chi phí bằng 0 từ ảnh hiện tại.
