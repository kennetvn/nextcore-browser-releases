<div align="center">

<img src="assets/banner.svg" alt="NextCore Browser" width="100%">

# NextCore Browser

**Trình duyệt nhiều profile, tự động hoá và AI agent, trong một app cho Windows, macOS và Linux.**

[![Bản mới nhất](https://img.shields.io/github/v/release/kennetvn/nextcore-browser-releases?label=b%E1%BA%A3n%20m%E1%BB%9Bi%20nh%E1%BA%A5t&color=0293DA&style=flat-square)](https://github.com/kennetvn/nextcore-browser-releases/releases/latest)
[![Tải về](https://img.shields.io/github/downloads/kennetvn/nextcore-browser-releases/total?label=l%C6%B0%E1%BB%A3t%20t%E1%BA%A3i&color=16181D&style=flat-square)](https://github.com/kennetvn/nextcore-browser-releases/releases)
![Nền tảng](https://img.shields.io/badge/n%E1%BB%81n%20t%E1%BA%A3ng-Windows%20%C2%B7%20macOS%20%C2%B7%20Linux-0293DA?style=flat-square)
![Giấy phép](https://img.shields.io/badge/gi%E1%BA%A5y%20ph%C3%A9p-th%C6%B0%C6%A1ng%20m%E1%BA%A1i%20%C2%B7%20m%C3%A3%20%C4%91%C3%B3ng-16181D?style=flat-square)

[**Tải về**](#tải-về) · [Tính năng](#tính-năng) · [Ứng dụng thực tế](#ứng-dụng-thực-tế) · [Cho developer](#cho-developer-và-ai-agent) · [Tài liệu](https://docs.homestaynextcore.org/nextcore-browser/) · [Trang sản phẩm](https://homestaynextcore.org/nextcore-browser) · [English](README.en.md)

</div>

---

> **Repo này chỉ chứa bản cài đặt, ghi chú phát hành và tài liệu giới thiệu.** NextCore Browser là phần mềm thương mại, mã nguồn đóng. Mọi bản cài tại đây trùng từng byte với bản trên [homestaynextcore.org](https://homestaynextcore.org/nextcore-browser); đối chiếu bằng tệp [`SHA512SUMS`](https://github.com/kennetvn/nextcore-browser-releases/releases/latest) kèm mỗi bản phát hành.

## Vấn đề

Ai quản lý nhiều tài khoản trên cùng một trang web đều gặp cùng một chuỗi rắc rối:

| Vấn đề thường gặp | Hậu quả |
|---|---|
| Một Chrome dùng chung cho mọi tài khoản | Cookie lẫn nhau, phải đăng xuất, đăng nhập lại liên tục |
| Chuyển qua lại giữa nhiều cửa sổ, nhiều hồ sơ Chrome | Dễ thao tác nhầm tài khoản, khó nhìn tổng thể |
| Proxy chỉ đặt được cho cả trình duyệt | Không tách được mạng theo từng tài khoản, khó biết proxy nào đang hỏng |
| Công cụ tự động hoá mở trình duyệt trắng mỗi lần chạy | Mất đăng nhập, phải viết thêm bước đăng nhập, dễ vướng mã xác minh |
| Mã 2FA nằm ở điện thoại hoặc ứng dụng khác | Mỗi lần đăng nhập mất vài chục giây |
| Việc lặp lại làm tay trên hàng chục tài khoản | Tốn công, khó theo dõi tài khoản nào đã xong |
| AI agent chỉ điều khiển được một trình duyệt trắng | Không giao được việc cho nhiều tài khoản đã đăng nhập cùng lúc |
| Chạy Claude Code, Codex, Gemini trên nhiều máy, mỗi máy một cửa sổ riêng | Không biết máy nào đang làm gì, agent kẹt chờ bạn mà không ai thấy |
| Quota Claude cạn giữa chừng ở một tài khoản trong khi tài khoản khác còn dư | Agent đứng im tới giờ reset, phần quota đã trả tiền của khung 5 giờ bị mất trắng |

## Giải pháp

**NextCore Browser** gom các việc đó vào một app:

- **Mỗi tài khoản một profile.** Mỗi profile là một trình duyệt Chromium riêng, giữ cookie, đăng nhập, dữ liệu trang, tiện ích, proxy và vân tay của chính nó. Tài khoản vẫn đăng nhập giữa các lần mở.
- **Một chỗ nhìn và điều khiển tất cả.** Danh sách profile có số liệu thật: trạng thái, proxy, độ trễ, mã 2FA. Chọn nhiều profile rồi mở, đóng, gán proxy hoặc xếp cửa sổ trong một lượt bấm.
- **Kịch bản làm phần lặp lại.** Ghép các bước thành kịch bản, chạy trên nhiều profile, giãn nhịp giữa các lần, dừng lại chờ bạn ở chỗ cần quyết định.
- **AI agent làm cùng bạn.** App có sẵn máy chủ MCP và Local API. Claude Code, Cursor, VS Code, Antigravity hay script của bạn tạo, mở và điều khiển profile qua đó.
- **Một chỗ điều phối cả đội agent.** NEXTCORE TERMINAL gom mọi tab Claude Code, Codex, Gemini và Antigravity trên mọi máy của bạn về một màn hình, và tự cân bằng quota giữa các tài khoản Claude của bạn ([chi tiết](#nextcore-terminal-và-cân-bằng-quota)).
- **Dữ liệu ở lại máy bạn.** Profile, cookie và khoá 2FA nằm trên máy. Các máy chỉ trao đổi việc qua trạm, không trao đổi mật khẩu, 2FA hay cookie.

<div align="center">
<img src="assets/screens/nb-danh-sach.webp" alt="Màn Quản lý profile: danh sách 12 profile chia theo nhóm, có proxy, mã 2FA và trạng thái từng hàng" width="860">
<br><sub>Quản lý profile. Ảnh chụp từ app thật, dữ liệu mẫu.</sub>
</div>

## NEXTCORE TERMINAL và cân bằng quota

Nếu bạn chạy AI agent để viết mã, kiểm thử hay vận hành, đây là phần đáng xem nhất của NextCore Browser. NCB **không cài agent nào**: nó dùng Claude Code, Codex, Gemini, Antigravity bạn đã cài và các gói bạn đã mua, rồi lo phần điều phối quanh chúng.

<div align="center">
<img src="assets/screens/nb-terminal.webp" alt="NEXTCORE TERMINAL: cây máy bên trái, terminal của tab Claude Code đang chọn bên phải" width="860">
<br><sub>NEXTCORE TERMINAL. Cây máy, worktree, tab bên trái; terminal của tab đang chọn bên phải. Dữ liệu mẫu.</sub>
</div>

### Một màn hình cho mọi tab trên mọi máy

- **Cây máy, worktree, tab.** Vòng xoay là agent đang làm, dấu tích là agent xong, biểu tượng cảnh báo là tab đang chờ bạn duyệt, mặt trăng là máy đang ngủ.
- **Gõ vào tab của máy khác như gõ trên máy mình.** Chữ hiện ngay trong khung, không chờ máy kia gửi lại. Gõ tiếng Việt bằng Unikey/EVKey đúng thứ tự phím. Dán ảnh (tối đa 10 MB) sang tab của máy khác cũng được.
- **Giao issue GitHub cho agent bằng một phím** (`Alt+I`): gõ số hoặc vài chữ để lọc, Enter là tab nhận «Làm issue #N: tiêu đề — link» và bắt đầu làm. Bảng hiện nội dung issue, danh sách việc, commit gần nhất kèm trạng thái CI.
- **Mỗi tab nói rõ nó đang chạy gì:** động cơ (Claude, AGY, Codex, Gemini), model, mức suy luận, tài khoản, quota còn lại của khung 5 giờ và 7 ngày.
- **Chia khung, lưới 2×2, kéo thả tab, tách tab ra cửa sổ riêng.** Mở lại app thì về đúng máy, tab, bố cục lúc trước.
- **Máy nào cũng tự đo sức mình.** NCB đo RAM trống, CPU và độ trễ của từng máy rồi quyết định máy đó nhận thêm tab hay không; luôn chừa phần cho bạn dùng máy. Tiến trình `node` mồ côi sau khi tab đóng được dọn mỗi phút.
- **Giữ máy thức, đánh thức máy ngủ.** Máy trạm tự giữ thức khi còn agent đang làm; máy đang ngủ đánh thức được qua mạng LAN.

<div align="center">
<img src="assets/screens/nb-terminal-giao-issue.webp" alt="Bảng Giao issue: gõ số hoặc chữ để lọc, Enter giao vào tab đang xem" width="760">
</div>

### Cân bằng quota giữa các tài khoản Claude

Gói Claude tính quota theo khung 5 giờ và 7 ngày. Khung vừa làm mới mà mới dùng 20% thì 80% còn lại mất trắng; ngược lại một tài khoản cạn thì agent đứng im dù tài khoản khác còn dư. NCB coi **quota của mọi tài khoản bạn đã đăng nhập là một bể chung** và điều phối nó:

| Khi nào | NCB làm gì |
|---|---|
| Quota ước tính của một tài khoản **từ 85%** | **Xả dần:** không giao việc mới cho tài khoản này, đóng tab thợ đã xong, chờ tab đang làm hết lượt rồi mở lại tab đó trên tài khoản còn nhiều quota. |
| **Từ 95%** | **Đổi ngay**, kể cả tab đang làm: Claude tiếp tục đúng phiên cũ trên tài khoản mới, và NCB gõ «tiếp tục» vào tab đang kẹt. Không cần đăng nhập lại. |
| Tab báo chạm giới hạn quá 3 phút | Đổi sang tài khoản còn nhiều quota nhất. |
| Có từ 2 tài khoản | Dùng **trước** tài khoản sắp tới giờ làm mới. Quota sắp reset mà chưa dùng là quota bỏ phí. |
| Số quota đã cũ | Tính dè dặt hơn và đánh dấu `~`. Tài khoản rảnh mà số cũ quá 30 phút thì được làm mới bằng một lượt hỏi rất nhỏ. |
| **Mọi tài khoản cùng cạn** | NextCore Command **tự dừng, ghi giờ sẽ chạy lại** (giờ reset cộng 3 phút), tới giờ đó tự đọc lại quota và gõ «tiếp tục» vào các tab đang kẹt. |

<div align="center">
<img src="assets/screens/nb-terminal-tai-khoan.webp" alt="Menu Tài khoản và quota: quota 5 giờ và 7 ngày của từng tài khoản Claude, dự báo chạm 85% và 95%, công tắc Tự đổi khi chạm giới hạn" width="860">
<br><sub>Tài khoản và quota của một máy: quota 5 giờ và 7 ngày, giờ reset, dự báo chạm 85% / 95%, công tắc «Tự đổi khi chạm giới hạn».</sub>
</div>

Thêm vào đó:

- **Quota ước tính theo tốc độ đốt của cả đội.** Mọi máy gửi quota từng tài khoản qua trạm mỗi 30 giây; NCB gộp theo email, ước mỗi tab đốt bao nhiêu % mỗi giờ, rồi đổi **trước** khi chạm giới hạn thay vì chờ báo lỗi.
- **Màn Usage: bể quota chung.** Bốn ô số (còn bao nhiêu, nhịp đang dùng, dự báo lúc cạn, mốc làm mới), biểu đồ bể 7 ngày với đường đã đo và đường kế hoạch, bảng tài khoản kiểu «dùng hay mất», và lịch sử dùng quota theo việc, tab, máy. Nút **Áp kế hoạch** chạy ngay một lượt điều phối.
- **Báo cáo khai thác quota bằng số thật:** tài khoản nào hao dùng bao nhiêu %, thất thoát bao nhiêu % (kèm tab·giờ và những máy đã dùng), và đề xuất cụ thể: đổi tài khoản cho một máy, nâng số tab, nạp thêm việc. Mỗi đề xuất kèm % quota ước dùng thêm được. Thiếu số nào thì câu đó bị bỏ, không đoán.
- **Dự phòng khi gói Claude cạn:** nếu máy chính có Antigravity (`agy`), NextCore Command chuyển tạm sang đó và trả về Claude khi quota hồi từ 20%. Với tab thợ, bạn có thể bật chạy bằng khoá Anthropic API của chính mình: **mặc định tắt**, có trần chi **3 USD mỗi việc và 15 USD mỗi ngày**, và agent qua MCP không bật được, nên không agent nào tự chi tiền thay bạn.
- **Ba nhóm tab:** xử lý việc (50%), khám phá việc đáng làm (30%), dự phòng để nghiệm thu và gỡ kẹt (20%). Tỉ lệ co giãn theo sổ việc, và không nhóm nào khác có việc thì chỗ vẫn được lấp.

> Đây là cân bằng giữa các tài khoản và gói **của chính bạn**. NCB không thêm quota, không dùng tài khoản của người khác, và không thay đổi giới hạn của nhà cung cấp.

### NextCore Command: một chỉ huy cho cả đội

Mỗi tài khoản NextCore có đúng **một** NextCore Command, đặt ở máy chính. Nó đọc **Bàn giao** của tab thợ khi việc xong hoặc kẹt, nghiệm thu (đạt, giao lại, hoặc ghi câu hỏi cho bạn), chia việc lớn thành việc nhỏ trong sổ việc, và ghi mỗi quyết định thành một dòng nhật ký để bạn đọc lại.

- **Không chạy liên tục.** Không có sự kiện thì nó ngồi yên và không tốn token. Sự kiện đến sát nhau được gom vào một lần đánh thức.
- **Không làm thay bạn những việc không nên:** không tự viết code thay tab thợ, không nhập mã OTP, không trả tiền, không đổi giá bán hay quyết định kinh doanh. Việc cần bạn thì ghi thành câu hỏi kèm phương án đề xuất.
- **Tab hỏng thì tự dựng lại.** Tab Command bị đóng, hết phiên hay chạm giới hạn: NCB đóng tab hỏng và mở tab mới, việc đang theo dõi và nhật ký nằm trong NCB nên tab mới làm tiếp, không mất gì.
- **Chọn model theo độ khó của việc,** hạ model khi việc đang trễ, và dừng lượt nếu chạm trần chi.

<div align="center">
<img src="assets/screens/nb-command-luong.webp" alt="NextCore Command: luồng một việc từ lệnh tới tay người dùng" width="760">
</div>

Hướng dẫn chi tiết: [NEXTCORE TERMINAL](https://docs.homestaynextcore.org/nextcore-browser/nextcore-terminal/) · [Máy trạm và nhiều máy](https://docs.homestaynextcore.org/nextcore-browser/tram-nhieu-may/).

## Ứng dụng thực tế

| Ai dùng | Làm gì với NextCore Browser |
|---|---|
| **Người bán hàng nhiều cửa hàng, nhiều kênh** | Mỗi cửa hàng một profile, đăng nhập sẵn. Mở đúng cửa hàng cần xử lý, không lẫn cookie giữa các cửa hàng. |
| **Đội chăm sóc khách hàng** | Mỗi nhân viên và mỗi kênh một profile. Xếp nhiều cửa sổ thành lưới trên màn hình phụ để theo dõi cùng lúc. |
| **Agency và đội vận hành nội dung** | Quản lý trang và nhóm cộng đồng của nhiều khách hàng, tách tài khoản theo từng khách. Kịch bản đăng bài chạy theo giờ, giãn nhịp giữa các nhóm, báo kết quả từng nhóm. |
| **Nghiên cứu thị trường, đọc dữ liệu nhóm** | Kho nhóm cục bộ ghi số thành viên và nhịp bài đăng. Lọc theo vùng, quy mô, nhịp đăng để chọn nơi đáng làm việc. |
| **QA và kiểm thử web** | Mỗi vai trò người dùng một profile. Playwright hoặc Puppeteer nối thẳng vào profile qua CDP. Đo giao diện nhiều khổ máy bằng bộ e2e có sẵn. |
| **Developer dùng AI agent** | Để Claude Code, Cursor hay Antigravity tạo, mở và điều khiển nhiều profile đã đăng nhập thay vì mở một trình duyệt trắng mỗi lần chạy. |
| **Đội phát triển phần mềm với nhiều agent** | NEXTCORE TERMINAL chạy Claude Code, Codex, Gemini, Antigravity trong tab của app. NextCore Command giao issue GitHub cho tab rảnh, nghiệm thu Bàn giao, và [cân bằng quota](#nextcore-terminal-và-cân-bằng-quota) giữa các tài khoản Claude để agent không đứng im giữa chừng. |
| **Đội thiết kế giao diện** | NEXTCORE DESIGN cho nhiều agent vẽ song song mỗi màn 20 ô (5 trạng thái × 4 khổ máy), xuất PNG hoặc SVG, gửi link xem cho người không cài app. |

> Bạn chịu trách nhiệm tuân thủ điều khoản của các trang web mình sử dụng. NextCore Browser là công cụ quản lý, không thay đổi quy định của nền tảng nào.

## Tính năng

App hiện có **24 mô-đun** chia thành bốn nhóm. Danh sách đầy đủ và hướng dẫn từng mô-đun ở [tài liệu](https://docs.homestaynextcore.org/nextcore-browser/).

### Trình duyệt

| Mô-đun | Làm gì |
|---|---|
| **Profile và proxy** | Mỗi profile một trình duyệt tách biệt, mỗi profile một proxy (HTTP, HTTPS, SOCKS4, SOCKS5, có hoặc không mật khẩu). Proxy hỏng báo đỏ ngay trên hàng, kèm lý do. |
| **Vân tay trình duyệt** | Mỗi profile nhận một hạt giống riêng ngay khi tạo: màn hình, card đồ hoạ, số nhân CPU, RAM, Canvas, WebGL, âm thanh, phông chữ suy ra từ đó nên lần mở nào cũng giống lần trước. Múi giờ, ngôn ngữ và vị trí khớp IP của proxy. |
| **Thao tác hàng loạt** | Chọn 5 hay 50 profile rồi mở, đóng, gán proxy, đặt nhóm hoặc xoá trong một lượt. Tạo hàng loạt từ danh sách, nhập và xuất danh sách profile. |
| **Xếp cửa sổ** | Xếp gọn trên nhiều màn hình, kể cả màn xoay dọc. Lưới tự chọn hoặc tự đặt, thu phóng trang 25% đến 200%. |
| **Kho proxy** | Một proxy dùng chung cho nhiều profile, đổi một chỗ là đổi hết. Theo dõi GB và chi phí theo kỳ, biết profile nào tiêu nhiều. |
| **Mã 2FA** | Mã 6 số hiện ngay trên hàng profile, đổi màu khi sắp hết 30 giây. Khoá không rời máy. |
| **Sao lưu** | Đóng gói profile thành tệp `.ncbak` mã hoá AES-256, mang sang máy khác vẫn giữ đăng nhập. Tệp hỏng 1 byte là từ chối khôi phục. |
| **Kho VPN** | VPN theo từng profile. Node không ra mạng thì profile không mở, nên IP thật không lộ. |

### Dữ liệu và khách hàng

| Mô-đun | Làm gì |
|---|---|
| **NEXTCORE GROUPCRAWL** | Kho nhóm cục bộ có số liệu: thành viên, nhịp bài đăng, vai trò của từng profile trong nhóm. Lọc theo vùng, quy mô, nhịp đăng. |
| **NEXTCORE CUSTOMERPOST** | Đọc bài khách đang tìm phòng từ các nhóm Facebook, tự crawl bằng profile của bạn, lọc theo thời gian, khu vực, danh mục và bình luận chào phòng. |
| **NEXTCORE CRM, SHEET, PMS** | Mở hộp thư CRM, bảng lịch phòng và màn vận hành ngay trong app, tự đăng nhập đúng tài khoản NextCore, phiên web tách khỏi mọi profile. |

### Tự động hoá

| Mô-đun | Làm gì |
|---|---|
| **NEXTCORE AUTOMATIONS** | Kịch bản chạy trên nhiều profile. Ghép các bước thành luồng, chạy theo giờ hoặc bấm tay, xem từng bước đang ở đâu. Ghi thao tác trên một profile thành luồng rồi chạy lại trên profile khác. |
| **NEXTCORE AGENT** | Nối khoá API của bạn với Anthropic, OpenAI, Gemini và hơn chục nhà cung cấp khác, xếp thứ tự ưu tiên thành chuỗi dự phòng, xem model, giá, hạn mức và lượt gọi gần đây. |
| **NEXTCORE MEDIA** | Tạo ảnh, video và phim ngắn bằng lượt miễn phí của các profile đã đăng nhập các dịch vụ AI, có Đạo diễn AI soạn cảnh và kích thước theo từng nền tảng. |
| **NCB COMMAND** | Giao việc cho đội agent theo số issue GitHub, máy rảnh tự nhận việc từ sổ. |

### Cho developer

| Mô-đun | Làm gì |
|---|---|
| **Local API + CDP** | Mọi thứ bấm được trong app đều gọi được qua API, chỉ nghe trên `127.0.0.1`, có token riêng mỗi máy. Playwright và Puppeteer nối thẳng vào profile. |
| **MCP** | Máy chủ MCP có sẵn trong app, bộ công cụ `browser_*` cùng tên với Playwright MCP chính thức, thêm công cụ quản lý profile. |
| **NEXTCORE TERMINAL** | Terminal nhiều tab chạy Claude Code, Codex, Gemini, Antigravity, nhìn được mọi tab trên mọi máy. |
| **NCB_E2E** | Bộ kiểm thử giao diện nhiều khổ máy, nhiều chế độ, chạy trên app thật. |
| **NEXTCORE DESIGN** | Vẽ màn trước khi viết mã, nhiều agent cùng vẽ, xuất PNG và SVG. |

Thêm trong app: **NEXTCORE EXTENSIONS**, **NEXTCORE TOOLS**, **NEXTCORE GROUPINVEST**.

### Sắp tới

- Đồng bộ profile qua nhiều máy
- Lịch chạy kịch bản theo giờ, theo ngày, theo ca làm
- Nhóm làm việc nhiều người: phân quyền theo nhóm profile, nhật ký ai mở profile nào

## Làm việc nhiều máy

Các máy cùng tài khoản NextCore tự thấy nhau qua trạm trong mạng LAN, không mở cổng ra Internet. Chọn một **máy chính**, các máy còn lại nhận việc từ máy chính.

<div align="center">
<img src="assets/screens/nb-tram-nhieu-may.webp" alt="Cài đặt nhiều máy: máy chính, máy ngoại tuyến, nút Trao vai" width="760">
</div>

- Xem cùng lúc mọi tab trên mọi máy: tab đang chạy, tab chờ bạn duyệt, tab hết hạn mức.
- Trao vai máy chính sang máy khác bằng một nút trong Cài đặt.
- App sập hoặc bị tắt ngang thì tự mở lại sau vài giây, mở lại các profile đang chạy.
- Mật khẩu, 2FA, OTP và cookie không đi qua trạm.

## Cho developer và AI agent

```bash
# Mở profile, nhận wsEndpoint cho Playwright
curl -X POST -H "Authorization: Bearer $NCB_TOKEN" \
  http://127.0.0.1:19880/api/v1/profiles/p_7f3a/start
```

```json
{ "pid": 18244, "debugPort": 52144,
  "wsEndpoint": "ws://127.0.0.1:52144/devtools/browser/9c1e…" }
```

- **MCP có sẵn.** Agent nối vào `http://127.0.0.1:<cổng>/mcp` kèm token. Không mở gì ra Internet.
- **Kết nối một chạm** cho Claude Code, Cursor, VS Code và Antigravity: app tự ghi tệp cấu hình kèm token riêng cho từng trợ lý.
- **Điều khiển trang bằng `browser_*`**, cùng tên với Playwright MCP nên agent đã biết là dùng được ngay.
- **Một phiên MCP một profile.** Muốn chạy song song nhiều profile thì mở nhiều phiên. Profile phiên này đang giữ thì phiên khác bị từ chối, nên hai agent không dẫm lên nhau.

Bạn nói gì với agent:

- «Liệt kê các profile nhóm Shop đang lỗi proxy.»
- «Tạo 10 profile tên Shop 01 tới Shop 10, gắn lần lượt các proxy này.»
- «Mở 4 profile nhóm Farm 2 và xếp thành lưới 2×2 trên màn hình phụ.»

Tài liệu: [Local API](https://docs.homestaynextcore.org/developer/local-api/) · [MCP cho AI agent](https://docs.homestaynextcore.org/developer/mcp/).

## Bảo mật và quyền riêng tư

- Dữ liệu profile nằm trên máy bạn. Sao lưu `.ncbak` mã hoá AES-256.
- Local API và MCP chỉ nghe `127.0.0.1`, mỗi máy một token.
- Trạm nhiều máy không chở mật khẩu, 2FA, OTP hay cookie.
- App cần kết nối tới `homestaynextcore.org` ít nhất 3 ngày một lần để giữ phiên đăng nhập.
- Danh sách cập nhật (`latest*.yml`) có chữ ký số ed25519. Đối chiếu bản tải về bằng `SHA512SUMS`.
- Báo lỗ hổng bảo mật theo [SECURITY.md](SECURITY.md).

## Tải về

**Bản mới nhất: 0.3.191** (12/11/2026). Xem [trang Releases](https://github.com/kennetvn/nextcore-browser-releases/releases/latest) để lấy bản cài và tệp `SHA512SUMS`.

| Nền tảng | Tệp | Dung lượng |
|---|---|---|
| **Windows** 10 và 11, 64-bit | [Bộ cài `Setup.exe`](https://github.com/kennetvn/nextcore-browser-releases/releases/latest) | khoảng 145 MB |
| **Windows** Portable | [`Portable.exe`](https://github.com/kennetvn/nextcore-browser-releases/releases/latest), không cần cài | khoảng 145 MB |
| **macOS** Apple Silicon (M1 đến M4) | [`mac-arm64.dmg`](https://github.com/kennetvn/nextcore-browser-releases/releases/latest) | khoảng 163 MB |
| **macOS** Intel | [`mac-x64.dmg`](https://github.com/kennetvn/nextcore-browser-releases/releases/latest) | khoảng 171 MB |
| **Linux** | [`AppImage` và `.deb`](https://github.com/kennetvn/nextcore-browser-releases/releases/latest) (Ubuntu, Debian), bản 0.3.190 | khoảng 134 đến 179 MB |

Máy farm Windows có thể tải và cài bằng một dòng PowerShell, không hiện màn cảnh báo:

```powershell
curl.exe -L -o "$env:TEMP\ncb-setup.exe" https://homestaynextcore.org/downloads/nextcore-browser/moi-nhat/windows; & "$env:TEMP\ncb-setup.exe"
```

### Cài đặt trong ba bước, khoảng hai phút

1. **Tải bộ cài** từ bảng trên.
2. **Cài đặt.** Tải bằng trình duyệt thì Windows có thể hiện màn xanh «Windows bảo vệ máy tính của bạn»: bấm *Thông tin bổ sung*, rồi *Chạy dù thế nào đi nữa*.
3. **Đăng nhập NextCore.** App hiện mã 8 ký tự, bấm *Cho phép* trên [homestaynextcore.org](https://homestaynextcore.org). Trong giai đoạn beta không giới hạn số máy.

### Yêu cầu hệ thống

| | |
|---|---|
| Windows | 10 hoặc 11, 64-bit |
| macOS | Apple Silicon và Intel |
| Linux | AppImage, Ubuntu hoặc Debian |
| Bộ nhớ | Tuỳ số profile mở cùng lúc; chân app báo RAM vàng khi quá 70%, đỏ khi quá 90% |
| Tài khoản | Tài khoản NextCore đang hoạt động; dùng thử miễn phí trước khi chọn gói |

App tự tải bản mới và cập nhật khi bạn khởi động lại.

## Có gì mới

Xem [CHANGELOG.md](CHANGELOG.md) hoặc trang [Releases](https://github.com/kennetvn/nextcore-browser-releases/releases).

## Tài liệu

| | |
|---|---|
| [Tổng quan](https://docs.homestaynextcore.org/nextcore-browser/) | Bắt đầu nhanh |
| [Profile và proxy](https://docs.homestaynextcore.org/nextcore-browser/profile/) | Tạo profile, gán proxy |
| [Chọn nhiều profile](https://docs.homestaynextcore.org/nextcore-browser/chon-nhieu/) | Thao tác hàng loạt |
| [Mã 2FA](https://docs.homestaynextcore.org/nextcore-browser/ma-2fa/) | Mã đăng nhập ngay trên hàng |
| [Sao lưu và khôi phục](https://docs.homestaynextcore.org/nextcore-browser/sao-luu-khoi-phuc/) | Tệp `.ncbak` |
| [Đăng nhập và thiết bị](https://docs.homestaynextcore.org/nextcore-browser/dang-nhap/) | Quản lý máy đã đăng nhập |
| [NEXTCORE AUTOMATIONS](https://docs.homestaynextcore.org/nextcore-service/automations/) | Kịch bản chạy nhiều profile |
| [Local API](https://docs.homestaynextcore.org/developer/local-api/) | Điều khiển bằng script |
| [MCP](https://docs.homestaynextcore.org/developer/mcp/) | Điều khiển bằng AI agent |
| [Khắc phục lỗi thường gặp](https://docs.homestaynextcore.org/nextcore-browser/khac-phuc-loi/) | Khi app hoặc profile không chạy |

## Hỗ trợ

- **Lỗi và góp ý về app:** [mở issue](https://github.com/kennetvn/nextcore-browser-releases/issues/new/choose) kèm phiên bản app và hệ điều hành. Đừng dán mật khẩu, token hay khoá 2FA.
- **Hỗ trợ tài khoản và gói dịch vụ:** liên hệ qua [homestaynextcore.org](https://homestaynextcore.org).
- **Lỗ hổng bảo mật:** xem [SECURITY.md](SECURITY.md), không đăng công khai.

## Giấy phép

NextCore Browser là phần mềm thương mại, **mã nguồn đóng**. Bản cài trong repo này chỉ được dùng theo [Điều khoản sử dụng](https://homestaynextcore.org/terms) của NextCore. Không dịch ngược, không tách rời, không dùng kết quả của app để dựng sản phẩm cạnh tranh. Chi tiết ở [LICENSE.md](LICENSE.md).

---

<div align="center">
<sub>© 2026 NextCore · <a href="https://homestaynextcore.org/nextcore-browser">homestaynextcore.org/nextcore-browser</a></sub>
</div>
