# Chính sách bảo mật

## Báo lỗ hổng

Nếu bạn tìm thấy lỗ hổng trong NextCore Browser:

1. **Không đăng công khai** trên issue, mạng xã hội hay diễn đàn.
2. Dùng [Báo cáo lỗ hổng riêng tư của GitHub](https://github.com/kennetvn/nextcore-browser-releases/security/advisories/new) trên repo này, hoặc gửi email tới `nextcore@homestaynextcore.org` với tiêu đề bắt đầu bằng `[SECURITY]`.
3. Ghi rõ: phiên bản app, hệ điều hành, các bước tái hiện, tác động bạn thấy được. Đừng đính kèm mật khẩu, token hay khoá 2FA thật.

Chúng tôi xác nhận đã nhận báo cáo, đánh giá mức độ, rồi thông báo khi có bản vá. Vui lòng không truy cập dữ liệu của người khác và không công bố trước khi có bản vá.

## Phiên bản được hỗ trợ

Chỉ **bản phát hành mới nhất** nhận bản vá bảo mật. App tự tải bản mới và cập nhật khi bạn khởi động lại.

## Kiểm tra bản tải về

Mỗi bản phát hành kèm tệp `SHA512SUMS`:

```bash
# Linux, macOS
sha512sum -c SHA512SUMS --ignore-missing
```

```powershell
# Windows
(Get-FileHash .\NextCoreBrowser-Setup-0.3.191.exe -Algorithm SHA512).Hash.ToLower()
```

So kết quả với dòng tương ứng trong `SHA512SUMS`. Khác một ký tự thì đừng chạy tệp, tải lại từ [homestaynextcore.org](https://homestaynextcore.org/nextcore-browser).

## Phạm vi

Trong phạm vi: app NextCore Browser, Local API, máy chủ MCP trong app, trạm nhiều máy, cơ chế cập nhật.
Ngoài phạm vi: trang web của bên thứ ba mà bạn mở trong profile, proxy và VPN của bên thứ ba.
