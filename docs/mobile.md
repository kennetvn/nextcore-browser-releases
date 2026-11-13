# NCB Mobile: điều khiển đội agent từ điện thoại

[← Về trang chính](../README.md) · [English](en/mobile.md)

> **Trạng thái: đang phát triển, chưa phát hành công khai.** Trang này mô tả phạm vi và kiến trúc đã chốt. Bản thử sẽ phát qua **TestFlight** (iOS) và **tệp APK** (Android); khi có, liên kết sẽ nằm ở trang [Releases](https://github.com/kennetvn/nextcore-browser-releases/releases) của repo này.

## Để làm gì (phạm vi bản đầu)

Bạn không phải ngồi trước máy chính để biết đội agent đang làm gì. App NCB Mobile cho iPhone và Android nối tới NextCore Browser của bạn để:

| Việc | Cụ thể |
|---|---|
| **Xem máy và quota** | Danh sách máy cùng tài khoản, trạng thái từng máy, quota 5 giờ và 7 ngày của từng tài khoản Claude, tab đang làm |
| **Chat với NextCore Command** | Gửi chữ và ảnh, nhận tin mới kèm thông báo đẩy, xem trước nội dung |
| **Điều khiển terminal từ xa** | Danh sách tab của từng máy, mở tab mới, xem màn, gõ lệnh, **duyệt hộp xin quyền** khi agent hỏi |
| **Giao việc và xem sổ việc** | Giao issue cho agent, xem việc đang làm, đang chờ, đã xong |
| **Hộp thư của bạn** | Việc cần bạn quyết định hiện thành câu hỏi kèm phương án, chạm để chọn |

Màn Terminal trên điện thoại được thiết kế cho thao tác ngón tay: hàng phím phụ với Ctrl và Alt dính, thanh chuyển phiên, cử chỉ, và gửi được phím thô như Ctrl-C, ký tự đơn và phím chức năng.

## Kiến trúc kết nối

- **Ghép đôi bằng mã QR kèm mã so khớp (SAS).** Điện thoại quét QR trên máy chính và đối chiếu mã ngắn hai bên trước khi tin nhau.
- **Mã hoá đầu cuối.** Nội dung đi qua trạm đã được mã hoá bằng AES-GCM; trạm chỉ chuyển tiếp bản mã. Thông báo đẩy (APNs cho iOS, FCM cho Android) cũng chở **bản mã**, không chở nội dung rõ.
- **Chịu trễ và mất mạng.** Trạm giữ hàng đợi khi máy đích vắng mặt, app nối lại và nhận bù.
- **Đăng nhập tài khoản NextCore trên điện thoại.** Mỗi điện thoại nhận một token thiết bị loại mobile; thu hồi từng thiết bị được.
- **Phân quyền.** Chọn mức quyền cho điện thoại: chỉ xem, gõ vào terminal, hay duyệt cả hành động phá huỷ.
- **Cùng khung với NextCore Browser.** App dùng chung giao thức với bản desktop, nên mọi thứ điều khiển được từ điện thoại là thứ máy chính vốn đã làm được.

## Công nghệ

App xây trên **Capacitor 8 và React**, bám theo bản vẽ NEXTCORE DESIGN của từng màn (mỗi màn đủ 5 trạng thái ở các khổ 375, 390, 430 và 768 px). Phát hành iOS qua TestFlight (kênh thử bên ngoài kèm liên kết công khai) và Android qua APK ký.

## Lộ trình phát hành bản thử

1. **Giao thức và cầu nối trên NCB:** sự kiện, lệnh terminal, sổ việc, hộp thư, một cửa gọi chức năng của app. Phần lớn đã xong, đang nối nốt.
2. **Bản vẽ và app:** bản vẽ 9 màn cộng màn Đồng bộ và Tính năng NCB, app Capacitor bám bản vẽ, đăng nhập NextCore trên điện thoại. Đã xong.
3. **Ghép đôi và kênh mã hoá thật qua trạm, màn Terminal, thông báo đẩy:** đang làm.
4. **Bản thử iOS (TestFlight) và Android (APK), hướng dẫn cài ba bước có ảnh:** kế tiếp.

Mọi nghiệm thu của NCB Mobile chỉ tính trên **app cài vào thiết bị thật** (iPhone, Android), không tính trên bản web hay trình giả lập, vì push, camera, sinh trắc và bàn phím chỉ kiểm được trên máy thật.

## Muốn dùng thử sớm

Theo dõi trang [Releases](https://github.com/kennetvn/nextcore-browser-releases/releases) hoặc [mở issue](https://github.com/kennetvn/nextcore-browser-releases/issues/new/choose) báo bạn muốn tham gia bản thử, kèm hệ điều hành điện thoại (iOS hay Android).
