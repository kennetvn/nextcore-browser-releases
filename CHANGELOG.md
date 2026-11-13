# Có gì mới

Chỉ ghi những thay đổi người dùng nhìn thấy. Danh sách đầy đủ theo từng bản: [Releases](https://github.com/kennetvn/nextcore-browser-releases/releases).

## 0.3.191 · 12/11/2026

- **NEXTCORE TERMINAL gần VSCode hơn:** Ctrl/⌘+F tìm trong tab, giữ 10.000 dòng cuộn ngược, Ctrl/⌘+bấm để mở link, cỡ chữ nhớ theo từng tab, thả tệp vào tab là dán đường dẫn.
- **NEXTCORE TERMINAL ổn định hơn:** hết ô chữ cũ còn sót sau khi đổi cỡ hay gõ emoji, hết chữ tiếng Việt (Unikey) hiện đôi, đổi tab không chớp trắng và không mất vị trí cuộn.
- **Mở thư mục bất kỳ:** «Mở thư mục…» (menu +, Ctrl+K Ctrl+O, mục Gần đây) mở tab ở bất kỳ thư mục nào, kể cả thư mục không có git. Tab giữ được khung màn sau khi mở lại app.
- **Dải tab gọn hơn:** ở cửa sổ hẹp, nút thừa gom vào «⋯», chuột phải tab mở menu.
- **Tài khoản và quota:** popup làm lại với ba ô Còn lại, Đủ tới, Dùng tiếp, mốc nạp lại 5h/7d, chữ không bị cắt. Thanh quota hiện ngay ở dòng tài khoản trong cây máy Terminal.
- **NextCore Command:** viên điều khiển ở chân app thành «dòng nghĩ» của Command, không còn đè lên terminal. Widget chat nhận ảnh dán hoặc kéo thả (tối đa 5 ảnh, 10 MB mỗi ảnh).
- **Sửa lỗi:** màn GROUP CRAWL không còn khựng khi cuộn trên máy Windows dựng hình bằng phần mềm. Tắt app bằng Task Manager không còn để lại tiến trình phụ của NEXTCORE TERMINAL chạy nền.

## 0.3.190 · 11/11/2026

- **NCB chạy độc lập, không cần Orca:** chọn *SETTINGS › AI agent (MCP) › Terminal chạy trên › NCB* thì mọi tab mới, kể cả tab NextCore Command giao việc vào, mở thẳng trong NEXTCORE TERMINAL. Đo trên Windows: tạo 10 tab ra 10 tab NCB.
- **Tab NCB mở là vào thẳng ô nhập:** đã có MCP, skill, hook và chế độ bypass của hồ sơ Claude trên máy.
- **Đổi cỡ cửa sổ, tách cửa sổ, xem từ máy khác:** mọi khung của cùng một tab nhận cỡ mới. Kéo đổi thứ tự tab, kéo tab ra ngoài app để tách cửa sổ.
- **Khoá Anthropic:** app chặn một tổ chức vừa có khoá FREE vừa có khoá CREDIT, vì hết credit tặng Anthropic sẽ trừ sang tiền nạp.
- **Quản lý profile:** chip đỏ «Tiện ích bị chặn host» khi tiện ích NextCore bị đặt quyền «Khi nhấp»; app tự đặt lại «Trên mọi trang web» trong vòng 60 giây. Cuộn mượt hơn trên màn tần số quét cao (rớt khung 42% còn 2 đến 4% ở 165 Hz), gõ ô tìm phản hồi nhanh hơn (độ trễ phím tối đa 96 ms còn 64 ms).
- **NextCore Command:** lịch sử quota ở màn Usage có thêm model và số token của từng tab.
- **Windows:** mở một bản NextCore Browser cài ở chỗ khác (bản Portable chẳng hạn) không còn làm bản đang chạy tự thoát. Ổ đĩa đầy không còn làm app sập: app giữ dữ liệu cũ và báo lỗi thay vì mất tệp cài đặt.
- **macOS:** app không còn nhận nhầm biến môi trường của bộ kiểm thử sau khi tự cập nhật.
