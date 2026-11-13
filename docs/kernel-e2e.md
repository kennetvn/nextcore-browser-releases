# NextCore Kernel và NextCore E2E

[← Về trang chính](../README.md) · [English](en/kernel-e2e.md)

## NextCore Kernel là gì

**NextCore Kernel** là phần tri thức vận hành chạy bên trong NextCore Browser. Nó là bộ não của hai khả năng:

- **NextCore Command:** vai trò, cách nghiệm thu và cách điều phối đội agent ([chi tiết](terminal-command-quota.md)).
- **NextCore E2E:** kiểm thử giao diện và hành vi trên profile thật.

Điểm khác với một bộ prompt nằm trong repo: Kernel **không nằm trong bộ cài** và **không ghi vào repo của bạn**. App gửi cho agent đúng phần cần dùng lúc chạy, và quyết định được tính trên máy chủ NextCore.

## Mỗi quyết định có mã và lời giải thích

Kernel không trả về một câu trả lời trơn. Mỗi quyết định mang:

- một **mã quyết định** tiếng Anh ổn định, ví dụ `accepted` (nghiệm thu đạt), `kept-session` (giữ phiên còn sống), `parked-for-release` (chờ bản phát hành);
- một câu tiếng Việt hoặc tiếng Anh nói rõ **đã xét gì và kết luận gì**;
- danh sách hành động tiếp theo cho agent thi hành, theo thứ tự.

Sổ giá trị gộp các quyết định thành một câu đọc được, ví dụ «4 quyết định: 3 nghiệm thu đạt, 1 giữ phiên còn sống».

## Học từ kết quả thật

Kernel không chỉ quyết định rồi quên. App ghi lại **kết quả của từng quyết định có phiếu**: sau 24 giờ và 7 ngày, việc đó đạt, bị giao lại, issue mở lại, báo xong giả, hay vượt quá một ngày công. Nếu một người hoặc agent làm khác quyết định trong 30 phút (cùng việc, cùng issue hoặc cùng máy), app ghi một tín hiệu «làm khác».

Quyền riêng tư của phần này: **chỉ gửi mã, nhóm hành động và số đo**, không gửi chữ tự do, không gửi mã định danh thô.

## Thiết kế để vận hành thật

| Đặc tính | Cách làm |
|---|---|
| **Tính trên máy chủ, gắn giấy phép** | Quyết định gắn với giấy phép và khoá thiết bị của máy. Giấy phép bị thu hồi hoặc hết hạn thì dừng ngay. |
| **Chịu được mất mạng** | Mất mạng thì máy tiếp tục chạy bằng bản lưu trên máy tối đa 24 giờ; quá hạn thì báo `NCK-0009` (không khả dụng) cho tới khi có mạng lại. |
| **Bản cài không mang luật** | Phần tri thức không nằm trong bộ cài. Máy chủ cấp khoá cho máy đã đăng nhập, lưu mã hoá trên máy; máy bị thu hồi thì khoá bị xoá. |
| **Có trần lượt gọi** | Gọi quá nhiều trong một giờ báo `NCK-0010`; dùng bình thường không chạm trần. |
| **Ngưỡng chỉnh từ xa** | Ngưỡng canh tab thợ (đứng im, treo lệnh, chờ nhận…) và cấu hình điều phối mặc định được máy chủ gửi xuống mỗi 5 phút, nên chỉnh được mà người dùng không phải cập nhật app. Cấu hình bạn đã tự lưu vẫn được giữ. |
| **Mã lỗi ổn định** | Họ mã `NCK-*` cho mọi tình huống không khả dụng, vượt hạn mức, bị khoá, để agent xử lý đúng thay vì đoán. |

## Quyền sử dụng

Bạn được dùng NextCore Command và NextCore E2E cho công việc của mình. NextCore Kernel chỉ được **áp dụng (Apply)**, không được **bóc tách (Extraction)** hay **chưng cất (Distillation)**: bạn và AI agent của bạn gọi phần mềm để nhận kết quả, không đọc, chép hay suy ngược ra quy tắc, lời nhắc, cách chấm điểm từ nhiều lần áp dụng. Chi tiết ở [LICENSE.md](../LICENSE.md) và [Điều khoản sử dụng, mục 7](https://homestaynextcore.org/terms).

## NextCore E2E: đo trang trên profile thật

Bộ `ncb_e2e*` đo trang web của bạn **trên profile thật, đã đăng nhập sẵn**, không cần dựng tài khoản thử. Agent gọi kiểm thử cho repo của bạn và nhận lại báo cáo: đã đo gì, lỗi gì, hồi quy, ảnh, cùng bước nên làm kế tiếp. Kịch bản chấm nằm trong NCB, không gửi cho agent.

| Công cụ | Đo |
|---|---|
| `ncb_e2e` | Một URL qua nhiều khổ màn × sáng/tối × màn chạm × mạng chậm hoặc mất mạng: tràn ngang, chữ bị cắt, vùng bấm nhỏ, tương phản, lỗi console, header bảo mật |
| `ncb_e2e_lo` | Như trên cho cả danh sách URL, chia cho nhiều profile chạy song song (số profile theo RAM trống và số nhân máy) |
| `ncb_e2e_toc_do` | Chấm Lighthouse ngay trong trình duyệt của profile |
| `ncb_e2e_seo` | Quét site cùng tên miền (robots.txt, sitemap.xml, link nội bộ); kèm mức sẵn sàng cho máy tìm kiếm AI: llms.txt, bot AI trong robots.txt, dữ liệu có cấu trúc theo loại trang |
| `ncb_e2e_vai` | Mở cùng danh sách URL bằng nhiều profile khác vai (khách, nhân viên, quản trị) để so ai thấy gì |
| `ncb_e2e_dinh_vi` | Trước khi test, xác định đích thật: trang web, bản Dev hay bản phát hành của app; route ứng với tệp mã nào; bản đang chạy đã có commit cần thử chưa. Bản chưa có thay đổi thì dừng và nói rõ, thay vì test bản cũ rồi báo xanh |
| `ncb_e2e_kich_ban` | Chạy kịch bản nhiều bước (bấm, gõ, chọn, đo). Kịch bản chỉ «Đạt» khi biên bản đủ đích, bản, commit, ít nhất một bước kiểm kết quả và ảnh có giờ; kiểm rỗng bị từ chối |
| `ncb_e2e_tu_issue` | Đọc ô nghiệm thu `- [ ]` của một issue GitHub, mở trang đích trên profile, lấy vai và tên thật của phần tử rồi viết kịch bản: mỗi tiêu chí một nhóm bước, có ít nhất một bước kiểm |

`ncb_e2e` và `ncb_e2e_lo` nhận `quyTac` để đặt ngưỡng riêng của dự án (cỡ vùng bấm, mức tương phản AA hay AAA, ngưỡng LCP/CLS, vùng bỏ qua).

### Chế độ xem: thấy agent bấm thật

Bật `xem` thì cửa sổ profile hiện con trỏ của NextCore Browser bay tới từng đích, gõ từng phím, và chỉ gợn sóng khi trang thật sự nhận cú bấm. Trước mỗi cú bấm app ngắm đích: đích bị che, chưa hiện hoặc còn đang chạy hiệu ứng thì không bấm. Nhiều phiên agent cùng xem một trang thì mỗi phiên một màu con trỏ. Truyền `record: true` để ghi hình ra tệp `.webm` kèm tệp chương `.chapters.vtt`, mỗi bước một chương.

## Vì sao điều này quan trọng

Agent hay báo «xong» và «xanh» quá sớm. Kernel và E2E đặt hai chốt chặn vào đúng chỗ đó:

- **Nghiệm thu có bằng chứng.** Command không nghiệm thu một việc chỉ vì tab báo xong.
- **Test không tự báo xanh khi chưa test gì.** E2E từ chối kịch bản rỗng, ảnh trùng nhau, selector không khớp gì, và dừng khi bản đang chạy chưa chứa commit cần thử.

## Tài liệu chi tiết

[Về NextCore Kernel](https://docs.homestaynextcore.org/nextcore-browser/tong-quan/#ve-nextcore-kernel) · [NextCore E2E trong MCP](https://docs.homestaynextcore.org/developer/mcp/)
