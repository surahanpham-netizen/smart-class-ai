# SMART CLASS – WEB APP QUẢN LÝ LỚP HỌC THÔNG MINH

## 1. Project Overview (Tổng Quan Dự Án)
**SMART CLASS** là nền tảng quản lý lớp học số thông minh toàn diện, hiện đại dành cho các trường học và trung tâm giáo dục. Hệ thống giải quyết trọn vẹn bài toán quản lý lớp học, theo dõi học sinh, điểm danh một chạm, giao và chấm bài tập, tổ chức thi trắc nghiệm trực tuyến, quản lý sổ điểm, khen thưởng thi đua, cảnh báo học sinh nguy cơ và kết nối chặt chẽ giữa Nhà trường - Giáo viên - Học sinh - Phụ huynh.

Hệ thống được thiết kế theo tiêu chuẩn phần mềm Giáo dục SaaS (Modern Education SaaS) với phân quyền nghiêm ngặt theo 4 vai trò (Role-Based Access Control - RBAC).

---

## 2. Features (Các Tính Năng Chính)

### 2.1. Phân Quyền 4 Role Chuyên Biệt
1. **Quản trị viên (ADMIN)**:
   - Dashboard quản trị toàn trường, chỉ số KPI cơ sở vật chất, giáo viên, học sinh.
   - Quản lý cấu hình trường học, năm học, khối lớp, môn học.
   - Quản lý danh sách tài khoản người dùng, cấp quyền, khóa tài khoản.
   - Nhật ký kiểm toán chi tiết (Audit Log) theo dõi ai sửa điểm, ai cập nhật điểm danh.
   - Trung tâm sao lưu dữ liệu toàn trường (Export JSON snapshot) và phục hồi khi có sự cố.

2. **Giáo viên (TEACHER)**:
   - **Dashboard**: Lời chào cá nhân hóa, lịch dạy hôm nay, các đầu việc cần xử lý (bài chưa chấm, học sinh vắng, cảnh báo học tập), thao tác nhanh.
   - **Quản lý lớp học**: Danh sách lớp, tạo lớp, sửa, sao chép lớp, lưu trữ, lọc theo khối/năm học, chuyển đổi dạng Thẻ (Grid) / Danh sách (Table).
   - **Workspace chi tiết lớp (`/teacher/classes/:id`)**: Giữ context lớp xuyên suốt với 8 tab: Tổng quan, Học sinh, Điểm danh, Bài tập, Điểm số, Thi đua, Thời khóa biểu, Báo cáo.
   - **Quản lý học sinh**: Danh sách học sinh, phân tổ, tìm kiếm, lọc, thêm/sửa/xóa học sinh, chuyển lớp, xuất CSV danh sách.
   - **Import Excel / CSV Wizard**: Quy trình 6 bước chuẩn (Tải file mẫu -> Tải file lên -> Khớp cột -> Xem trước -> Kiểm tra lỗi chi tiết từng dòng/cột -> Xác nhận nhập). Không âm thầm nhập dữ liệu lỗi.
   - **Hồ sơ 360° học sinh**: Xem toàn diện GPA, chuyên cần, lịch sử nộp bài tập, điểm rèn luyện hành vi, huy hiệu, thông tin phụ huynh; các thao tác nhanh (Ghi nhận hành vi, Thêm nhận xét học bạ với AI, Nhắn tin phụ huynh).
   - **Điểm danh một chạm**: Tối ưu hóa đặc biệt cho thiết bị di động/màn hình cảm ứng. Đánh dấu có mặt, đi trễ, vắng phép, không phép, về sớm; ghi lý do; nút "Đánh dấu tất cả có mặt"; cảnh báo mất dữ liệu chưa lưu; lịch sử điểm danh.
   - **Bài tập & Chấm bài**: Giao bài tập cho cả lớp/nhóm tổ/cá nhân, đính kèm file, hạn nộp. Giao diện chấm bài với nhập điểm, lời phê sư phạm (có AI hỗ trợ gợi ý lời phê).
   - **Kiểm tra trực tuyến & Ngân hàng câu hỏi**: Kho câu hỏi trắc nghiệm, đúng/sai, tự luận theo khối/môn/mức độ. Tạo bài kiểm tra tính giờ tự động, đảo câu hỏi, đảo đáp án.
   - **Sổ điểm điện tử**: Bảng điểm ma trận tính toán điểm trung bình tự động (Thường xuyên x1, Giữa kỳ x2, Cuối kỳ x3). Sửa điểm trực tiếp, xuất bảng điểm Excel/CSV.
   - **Bộ công cụ lớp học tương tác (Classroom Tools)**:
     - *Vòng quay may mắn*: Hiệu ứng xoay mượt mà, chúc mừng pháo hoa (confetti), tùy chọn loại bạn đã gọi.
     - *Bốc thăm ngẫu nhiên*: Chọn 1 hoặc nhiều học sinh, tránh lặp lại.
     - *Chia nhóm tổ*: Chia theo số lượng nhóm hoặc số học sinh/nhóm, chế độ cân bằng học lực GPA đều các nhóm, sao chép danh sách nhóm.
     - *Đồng hồ đếm ngược*: Vòng tròn tiến trình trực quan, các mốc 1p, 3p, 5p, 10p, 15p, chuông báo âm thanh Web Audio API.
     - *Khởi động nhanh*: Câu hỏi trắc nghiệm bấm chuông vui nhộn đầu tiết.
   - **Thi đua & Khen thưởng**: Bảng xếp hạng thi đua 4 tổ trong tuần, trao huy hiệu "Ngôi sao tuần", "Chiến binh chăm chỉ", vinh danh tiến bộ.
   - **Cảnh báo thông minh**: Tự động phát hiện nguy cơ học tập (vắng nhiều, sụt điểm, thiếu bài) với quy trình xử lý: Mới -> Đã xem -> Đang xử lý -> Đã giải quyết.
   - **Học liệu số**: Quản lý slide bài giảng, file PDF, tài liệu Word, video, hỗ trợ xem trước (preview) và tải về.
   - **AI Trợ lý giáo viên**: Soạn kế hoạch bài dạy (Giáo án 5512), tạo câu hỏi đề cương, gợi ý nhận xét học bạ. Tuân thủ nguyên tắc Review -> Edit -> Approve.
   - **Thông báo & Báo cáo**: Soạn thông báo gửi học sinh/phụ huynh; xuất báo cáo tổng hợp chất lượng in ấn và xuất file.

3. **Học sinh (STUDENT)**:
   - Dashboard học sinh, lịch học trong tuần.
   - Xem bài tập được giao, làm bài và nộp bài trực tuyến (gửi nội dung & đính kèm file).
   - Làm bài kiểm tra trực tuyến tính giờ với đồng hồ đếm ngược và biết kết quả, xem lời giải chi tiết ngay sau khi nộp bài.
   - Xem bảng điểm cá nhân, chuyên cần, huy hiệu thành tích và hồ sơ học sinh.
   - *Bảo mật*: Học sinh chỉ có quyền xem dữ liệu của chính mình.

4. **Phụ huynh (PARENT)**:
   - Chuyển đổi linh hoạt giữa các con (Ví dụ: Nguyễn Văn An - 6A1 và Nguyễn Mai Linh - 8A2).
   - Theo dõi điểm số các môn, tình hình chuyên cần từng ngày, bài tập về nhà của con.
   - Kênh trao đổi trực tiếp với Giáo viên chủ nhiệm (Chat tin nhắn hai chiều).
   - Xem thông báo nhà trường.
   - *Bảo mật*: Phụ huynh chỉ được xem dữ liệu của con mình được liên kết.

---

## 3. Tech Stack (Công Nghệ Sử Dụng)
- **Frontend Core**: React 19, TypeScript, Vite.
- **Routing**: React Router DOM (v7/v6) với RoleGuard phân quyền và bảo vệ route.
- **Styling**: Tailwind CSS v4, phong cách Modern Education SaaS, chuẩn Accessibility WCAG AA, responsive chuẩn trên Desktop (>= 1280px), Tablet (768px - 1279px) và Mobile (< 768px).
- **Icons**: Lucide React.
- **Hiệu ứng & Hoạt ảnh**: Canvas Confetti, Web Audio API (chuông báo đồng hồ).
- **Lưu trữ dữ liệu**: LocalStorage với Seed Data phong phú bằng tiếng Việt, thiết kế qua Service/Repository pattern để dễ dàng tích hợp Backend API.

---

## 4. Folder Structure (Cấu Trúc Thư Mục)
```
src/
├── assets/                  # Tài nguyên tĩnh
├── components/
│   ├── classroom-tools/     # Vòng quay, Bốc thăm, Chia nhóm, Đồng hồ, Quick Quiz
│   ├── common/              # Modal, ConfirmDialog, StatCard, Badge, Breadcrumb, EmptyState
│   └── layout/              # AppLayout, Header, Sidebar, GlobalSearch, QuickCreate, NotificationCenter
├── contexts/                # AuthContext, ToastContext, ClassContext
├── data/                    # SeedData tiếng Việt thực tế
├── pages/
│   ├── admin/               # Dashboard, Schools, Users, Audit Logs, Settings
│   ├── auth/                # Login, ForgotPassword, 403, 404
│   ├── parent/              # Dashboard, Grades, Attendance, Assignments, Chat
│   ├── student/             # Dashboard, Assignments, Quiz, Grades, Attendance, Profile
│   └── teacher/             # Dashboard, Classes, Students, Attendance, Assignments, Grading, Quizzes, QuestionBank, Resources, AI, Grades, Behavior, Alerts, Tools, Reports
├── routes/                  # RoleGuard kiểm soát quyền truy cập
├── services/                # StorageService, AiService
├── types/                   # Định nghĩa TypeScript Models hoàn chỉnh
├── App.tsx                  # Khai báo Routes tập trung
├── index.css                # Tailwind CSS v4 & Typography
└── main.tsx                 # Entrypoint
```

---

## 5. Demo Accounts (Tài Khoản Thử Nghiệm)
Hệ thống cung cấp sẵn các nút chọn nhanh tài khoản tại màn hình Đăng Nhập hoặc dropdown menu ở góc phải trên cùng để chuyển đổi vai trò ngay lập tức:

| Vai Trò | Email Đăng Nhập | Mật Khẩu | Mô Tả |
| :--- | :--- | :--- | :--- |
| **Giáo viên (TEACHER)** | `teacher@smartclass.local` | `123456` | Cô Trần Thị Mai Phương (GVCN Lớp 6A1) |
| **Học sinh (STUDENT)** | `student@smartclass.local` | `123456` | Em Nguyễn Văn An (Lớp 6A1) |
| **Phụ huynh (PARENT)** | `parent@smartclass.local` | `123456` | Ông Nguyễn Văn Hùng (PH em An & em Linh) |
| **Quản trị viên (ADMIN)** | `admin@smartclass.local` | `123456` | Thầy Nguyễn Quốc Huy (Ban Giám Hiệu) |

*(Lưu ý: Mật khẩu mặc định cho các tài khoản là `123456`)*

---

## 6. Development & Build (Cài Đặt & Chạy Dự Án)
```bash
# 1. Cài đặt các gói phụ thuộc
npm install

# 2. Khởi chạy môi trường phát triển (Port 3000)
npm run dev

# 3. Kiểm tra TypeScript & Linting
npm run lint

# 4. Build sản phẩm sẵn sàng triển khai (Production Build)
npm run build
```

---

## 7. Khôi Phục Dữ Liệu Ban Đầu
Nếu muốn làm mới toàn bộ dữ liệu mẫu, đăng nhập tài khoản **Admin**, vào **Cấu hình hệ thống** (`/admin/settings`) và bấm nút **"Đặt Lại Dữ Liệu"**.
