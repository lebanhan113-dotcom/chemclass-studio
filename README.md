# ChemClass Studio – Triển khai bằng GitHub Pages

Đây là **website tĩnh dùng thử** dựa trên đề Hóa học thật gồm **21 câu**, giữ nguyên ba phần và các công thức/hình ảnh đã chuẩn hóa. Không có backend hoặc cơ sở dữ liệu chung.

## Cách nhanh nhất (không viết mã)

1. Vào https://github.com/new và đăng nhập GitHub. Tạo repository **Public** tên `chemclass-studio`, có thể để trống.
2. Giải nén `ChemClass_Studio_GITHUB_PAGES.zip`. **Tải nội dung thư mục giải nén lên gốc repository**, KHÔNG tải nguyên file ZIP làm một file vào repository. GitHub hỗ trợ Add file > Upload files; đảm bảo có `index.html`, `exam.html`, thư mục `assets`, và `.github/workflows/pages.yml`.
3. Vào **Settings > Pages > Build and deployment > Source: GitHub Actions**. Workflow **Deploy ChemClass Studio to GitHub Pages** chạy khi có commit ở nhánh `main`; cũng có thể chọn tab Actions > workflow > Run workflow.
4. Khi workflow thành công, URL thường là `https://TEN-TAI-KHOAN.github.io/chemclass-studio/` (tên tài khoản và repository thực tế do GitHub quyết định). Trang phòng thi: `.../exam.html?portal=student`.
5. Thay đổi tệp, commit vào nhánh `main`: GitHub Actions sẽ triển khai phiên bản mới.

**Cách thay thế nếu không tải lên được thư mục `.github`:** Vào Settings > Pages > Source: Deploy from a branch, chọn `main` và `/(root)`, rồi Save. Cách này không cần workflow, chỉ cần các trang tĩnh và `.nojekyll` ở gốc.

## Quan trọng về bảo mật và giới hạn

- GitHub Pages **không phải máy chủ chấm thi**. Trình duyệt học sinh lưu bài trong `localStorage`; giáo viên trên máy khác không tự động nhận bài.
- Nếu có tính năng xuất phiếu JSON, cần chuyển phiếu thủ công; phiếu có thể bị chỉnh sửa, không dùng làm căn cứ thi chính thức.
- Passcode chỉ bảo vệ giao diện và có thể bị phân tích qua mã nguồn. Đáp án/đề không thể giữ bí mật tuyệt đối trong trang tĩnh.
- Không đưa danh sách học sinh có dữ liệu cá nhân, bảng điểm, mật khẩu thật hay mã khóa API lên repository công khai.
- Thang điểm và các câu cần giáo viên duyệt (I-12, II-02) phải được xác nhận trước khi cho chấm chính thức.
- Không cấu hình thêm server.py, localhost, Python hay Node.js cho GitHub Pages.

## Khắc phục lỗi phổ biến

- **404:** kiểm tra `index.html` nằm ở gốc, Pages đã bật, workflow xanh, và đường dẫn có tên repository.
- **Logo/công thức không hiện:** kiểm tra thư mục `assets` và các đường dẫn tương đối có đầy đủ file.
- **Không thấy bài học sinh trên máy giáo viên:** vì chưa có backend; không phải lỗi Pages.
- **Passcode mặc định không nhận:** mật khẩu có thể đã thay đổi trong localStorage của chính trình duyệt đang mở.
