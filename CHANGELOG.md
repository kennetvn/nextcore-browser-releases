# Có gì mới

Chỉ ghi những thay đổi người dùng nhìn thấy. Danh sách đầy đủ theo từng bản: [Releases](https://github.com/kennetvn/nextcore-browser-releases/releases).

## 0.3.192 · 14/11/2026

- **NCB không còn cần Orca:** mọi tab agent mở thẳng trong NEXTCORE TERMINAL. Nâng cấp từ 0.3.191, app tự chuyển tài khoản Claude từ Orca sang NCB một lần (sao lưu trước, tài khoản đã có thì không nhập trùng). Profile, tài khoản và trạng thái đăng nhập giữ nguyên.
- **Lưu ý khi cập nhật:** phần terminal khởi động lại theo bản mới, lệnh đang chạy nền trong tab agent sẽ dừng. Claude tự nối lại phiên, lệnh nền cần chạy lại.
- **macOS:** tài khoản Claude mới chép từ Orca (chưa có sẵn trong NCB) cần đăng nhập lại một lần, vì Orca giữ phiên đăng nhập trong Keychain của macOS. Tài khoản đã có trong NCB giữ nguyên đăng nhập.
- **NEXTCORE TERMINAL:** kéo một tab thả vào mép khung để chia đôi màn. Thả giữa khung là thay tab, kéo ra ngoài cửa sổ vẫn là tách riêng.
- **NEXTCORE DESIGN:** trang chủ có ô tìm và lọc trên một hàng, nút chính «Tạo / Nhập». Canvas có thước, thanh công cụ nổi và thanh zoom: kéo nền để di chuyển, lăn chuột để zoom quanh con trỏ, nhấn đúp vào bảng để phóng tới, phím Z. Mở lại trang 55 bảng mất 21 ms thay vì 1,1 s; ảnh SVG nhập vào giữ đúng độ rộng chữ.
- **Đồng bộ profile:** kéo profile chạy nền hiện tiến độ theo %, thứ tự trong hàng chờ, lỗi chia theo loại và nhãn «Đã về» khi xong.
- **Chân app gọn hơn:** chip NextCore Command và chip Máy gộp thành một viên, điều khiển máy trạm nằm ngay trong chip Command. Cửa sổ hẹp 800 px không còn tràn chân app, thẻ máy trạm không tràn khỏi cửa sổ.
- **Màn hình nhỏ:** vùng làm việc dưới 1100×640 thì app tự thu giao diện về 90 % để không mất nút.
- **App nhẹ hơn khi để rảnh:** CPU dưới 3 % trên máy đo Windows (chân app, bộ đo hiệu năng và lệnh git nền không còn chạy lặp). Bật công tắc Toàn quyền cho Command mất 40 ms thay vì 2,8 s.
- **Hook nhịp chờ bạn đồng ý:** lần đầu dùng tab Claude Code, app hỏi trước khi cài hook nhịp; bật hoặc tắt lại ở *Cài đặt › Agent*.
- **Hồ sơ làm việc:** điều bạn đã nói rõ trong tab agent được ghi lại để lần sau khỏi hỏi lại. Bí mật bị lọc trước khi lưu, dữ liệu mã hoá trên chính máy bạn, không gửi lên máy chủ NextCore.
- **NextCore Command:** linh vật Nhịp mới hai cỡ, báo theo mức vướng và trồi lên khi có việc quan trọng.
- **Tài khoản và quota:** tài khoản chưa mở tab vẫn đọc lại quota mà không mở khung 5 giờ mới. Thanh quota màu vàng dễ đọc hơn trên nền sáng.
- **Màn đăng nhập:** mất kết nối thì hiện dải báo lỗi có biểu tượng và địa chỉ máy chủ, thay cho dòng chữ nhỏ.

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
