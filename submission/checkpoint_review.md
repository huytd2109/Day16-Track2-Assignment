# Kiểm tra CP3–CP5

| Checkpoint | Kết luận | Bằng chứng / phần còn thiếu |
|---|---|---|
| CP3 | Đạt kiểm tra thực chạy | VM AWS t3.small; Python exit 0; JSON mới hợp lệ, đủ 10 metrics; SHA-256 local khớp VM; split/seed/repeats rõ ràng. |
| CP4 | Chưa hoàn tất | Đã thu top/free/ip trong benchmark; thiếu screenshot terminal, CPU/RAM/Network và Billing Console. API Billing bị từ chối quyền, không chứng minh $0 hoặc dữ liệu chưa cập nhật. |
| CP5 | Chưa hoàn tất | Đã tải code/JSON/log, đóng gói source và báo cáo 8 dòng; cleanup đã hoàn thành, Terraform state có 0 tài nguyên và không còn outputs; chưa push/nộp, còn thiếu ảnh bằng chứng. Xem evidence/cleanup_result.json; kế hoạch trước cleanup gồm 27 tài nguyên tại evidence/cleanup_plan_summary.json. |

`benchmark_output.txt` và `resource_usage.txt` là log thật thu qua SSH; không phải screenshot. Thư mục `screenshots/` dành cho ảnh thật còn cần bổ sung. Để chụp terminal từ bản đã tải: mở `benchmark_output.txt` và `resource_usage.txt` trong terminal và ghi rõ ảnh xem lại log đã thu lúc 17:55 ngày 02/10/2026 (UTC+7).

Billing: dùng Console phiên chủ tài khoản có quyền Billing, chọn Bills/Cost Explorer, ngày lab 02/10/2026, Group by Service, chụp bộ lọc và thời điểm. Nếu Console thực sự chưa có dữ liệu mới ghi “Billing chưa cập nhật tại thời điểm …”. Không cần duy trì VM để chờ Billing. Xem [quyền Billing AWS](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/control-access-billing.html).

CP3: lần tách thứ hai lấy 25% của 80% còn lại, nên validation bằng 20% toàn bộ. AUC dùng xác suất gian lận; nhãn 0/1 ở ngưỡng 0.5 dùng cho Accuracy/F1/Precision/Recall. Throughput = 1000 / median thời gian batch tính bằng giây. `top` lấy mẫu khi tiến trình đang import/load, không khẳng định đây là peak CPU/RAM trong fit. LightGBM 4.7.0 cảnh báo deprecation `eval_set` nhưng thực chạy thành công. Early stopping hiện kiểm tra cả AUC và binary_logloss mặc định trên validation; không dùng test. Xem [early stopping LightGBM](https://lightgbm.readthedocs.io/en/stable/pythonapi/lightgbm.early_stopping.html).

Infra giữ source Terraform và lock file thực dùng. Để tái tạo cấu hình compute đã đo, truyền `-var=cpu_instance_type=t3.small`; không đưa tfvars riêng vào gói. Dataset, lab-key, kaggle.json, credentials, state, plan nhị phân và .terraform không được đóng gói. Cleanup đã hoàn thành; Terraform state sau cleanup có 0 tài nguyên và không còn outputs. Bằng chứng tóm tắt nằm trong evidence/cleanup_result.json; state và state backup được giữ riêng, không đưa vào ZIP. ZIP hiện là bản chuẩn bị, chưa phải bài hoàn tất.
