# BÁO CÁO THIẾT LẬP BẢO MẬT KHO MÃ NGUỒN

## 1. Pre-push Checklist (Rà soát chống Hardcode API Keys)
Toàn bộ thành viên trong team bắt buộc phải thực hiện 4 bước kiểm tra (Pre-push Check) sau đây trước khi gõ lệnh `git push`:
* [ ] **1. Kiểm tra lá chắn `.gitignore`:** Xác nhận đã khai báo `.env` bên trong.
* [ ] **2. Rà soát trạng thái chờ Commit:** Chạy lệnh `git status` tuyệt đối không được có sự xuất hiện của file `.env`.
* [ ] **3. Truy quét Hardcode toàn dự án:** Tìm kiếm các từ khóa `sk-proj`, `AKIA`, `password`, `secret` đảm bảo không còn chuỗi tĩnh.
* [ ] **4. Nghiệm thu `.env.example`:** Đảm bảo toàn bộ giá trị khai báo là rỗng hoặc chuỗi giả vô hại.

## 2. Hướng dẫn thiết lập 2FA bắt buộc cho Team
1. **Team Lead (Cấp tổ chức):** Vào GitHub Settings ➔ Authentication security ➔ Require two-factor authentication for everyone.
2. **Thành viên (Cấp cá nhân):** Vào Settings ➔ Password and authentication ➔ Enable 2FA (Dùng Authenticator App). Quan trọng: Lưu bộ 10 Mã khôi phục (Backup Codes) vào Két sắt Bitwarden.

## 3. Báo cáo Đánh giá Rủi ro (Nếu thiếu tệp `.gitignore`)
Nếu thiếu tệp `.gitignore`, một chuỗi rủi ro Domino sẽ xảy ra:
* Lệnh `git push` sẽ vô tình tải tệp `.env` chứa chìa khóa thật lên GitHub Public.
* Mã nguồn sẽ bị các Scraper Bots của tin tặc phát hiện trong vòng chưa tới 3 giây.
* Thiệt hại nghiêm trọng về tài chính do hacker dùng AWS Keys mở máy chủ đào coin ảo, và mất mát dữ liệu do bị tải trộm và xóa sạch Database (Ransomware).
* Lỗi sai phổ biến: Lập trình viên cố tạo một commit mới để xóa file, điều này là vô nghĩa do Git vẫn lưu lịch sử cũ.
* Cách khắc phục duy nhất: Lập tức truy cập vào các nền tảng gốc, chọn **Revoke (Thu hồi)** các chìa khóa đã lộ để vô hiệu hóa chúng vĩnh viễn.
