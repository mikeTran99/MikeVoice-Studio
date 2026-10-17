# Nhật ký thay đổi — Mike Voice Studio

## 4.1.1 — 17/10/2026
**Engine offline chạy ổn định, điểm Vbee đúng, tách kho giọng, bản dựng native Nuitka**
- **Engine offline hết lỗi junction**: không còn phụ thuộc junction của uv trong `pyvenv.cfg` (lỗi Windows
  RedirectionGuard 448 khiến engine lúc chạy lúc không). Có kiểm thử E2E thật dựng giọng và trộn một dự án.
- **Điểm Vbee chỉ hiện khi đã đăng nhập**: chưa đăng nhập / đã đăng xuất thì hiện 0, không còn số điểm cũ của
  phiên trước; xoá thông tin API cũng đưa điểm về 0.
- **Tách kho giọng**: trang OFFLINE chỉ hiện giọng offline (OmniVoice, Windows), trang ONLINE chỉ hiện giọng online
  (Vbee, Edge, OpenAI, Gemini) — không còn lẫn giọng "ONLINE · tốn điểm Vbee" trong nhóm OFFLINE.
- **Bản dựng thương mại biên dịch native (Nuitka)**: mã Python được biên dịch sang mã máy C (bảo vệ mã nguồn), trình
  biên dịch C là Zig — không cần MSVC, không ghi GB nào lên ổ C. Chế độ thư mục (`--standalone`, không onefile nên
  không giải nén ra %TEMP% ổ C); LTO tắt vì trình liên kết của Zig không liên kết được khi bật. Bộ cài `MikeVoice-Setup.exe` và gói `MikeVoice-win.zip` nay
  đóng cả thư mục; bản kê `files.sha256` kiểm tra toàn vẹn từng tệp trước khi cài. (PyInstaller đã gỡ.)

## 4.1.0 — 16/10/2026
**Mới: menu ONLINE / OFFLINE / CHUNG, giọng đám mây, dịch phụ đề, thuyết minh slide PowerPoint**
- **Menu trái chia ba nhóm**: *ONLINE · cần mạng* (Phòng thu Vbee · Giọng đám mây · Giọng → Chữ (Vbee) · Dịch phụ đề),
  *OFFLINE · trên máy* (Đọc văn bản · Hội thoại nhóm · Lồng tiếng theo phụ đề · Thuyết minh slide · Giọng → Chữ
  (Whisper) · Giọng của tôi), *CHUNG* (Lịch sử · Engine và Model · Nhật ký · Cài đặt). Ctrl+1..8 giữ đúng trang như 4.0.
- **Giọng đám mây**: giọng Windows (offline, miễn phí), Edge (online, miễn phí), OpenAI và Google Gemini (tính phí theo
  tài khoản của bạn). Khoá API cất trong Windows Credential Manager; danh sách giọng và nghe thử.
- **Dự án dùng mọi nguồn giọng** (Vbee, offline, Windows, Edge, OpenAI, Gemini) và hiện số điểm Vbee từng câu.
- **Dịch phụ đề** bằng ChatGPT / Gemini: giữ mốc thời gian, bảng tên riêng, gửi thẳng sang Lồng tiếng.
- **Thuyết minh slide PowerPoint**: đọc .pptx, tạo audio từng slide theo tốc độ đọc, xuất WAV + .srt, PPTX, MP4.
- **Whisper chia lại phụ đề** không cần nhận dạng lại; **mẫu hội thoại** và **tốc độ riêng từng nhân vật**.
- **Dữ liệu theo ổ của ứng dụng**: app ở ổ nào thì dữ liệu ở `<ổ đó>:\MikeVoiceStudio\data`; lần đầu tự chép (không xoá) dữ liệu
  cũ từ ổ hệ thống.
- **Đóng gói chuẩn**: bộ cài `MikeVoice-Setup.exe` (Inno Setup), `Cai_dat.cmd`, gói phát hành có
  `SHA256SUMS.txt`, sổ tay khách hàng `docs/HUONG_DAN_KHACH_HANG.md`. Thư mục cài mặc định không nằm ở ổ C nếu tránh được.
- Sửa lỗi: không mất audio Vbee đã trả tiền (giữ WAV khi chưa đổi được 24 kHz, kể cả khi tạo lại); hỏi trước khi đổi chế
  độ dự án làm mất audio; dịch phụ đề không chạy song song hai lượt tính phí, lỗi giữa chừng giữ lô đã dịch; không ghi đè
  dữ liệu người dùng; PowerShell con không ghi ổ C; trang slide không kẹt khi mở tệp lúc đang tạo, không đóng PowerPoint
  của người dùng; Gemini trả nội dung rỗng được báo rõ.

## 4.0.0 — 15/10/2026
**Mới: vừa online (Vbee) vừa offline (OmniVoice + Whisper trên máy)**
- Engine offline chạy tiến trình riêng (Python + PyTorch CUDA do uv dựng trong thư mục engine), kiêm REST API cục bộ
  có `X-API-Key` cho n8n / Make / Zapier. Cài một nút; thư mục engine theo ổ của ứng dụng, không đụng ổ C.
- Dự án lai: văn bản / hội thoại / phụ đề .srt, mỗi câu một giọng Vbee hoặc offline, trộn + cân âm lượng, xuất WAV/MP3
  kèm .srt.
- Giọng của tôi: sao chép giọng từ tệp audio/video, thiết kế giọng bằng mô tả, 11 giọng có sẵn, gói `.vcp`.
- Nhận dạng: Vbee hoặc Whisper trên máy; nút *Lồng tiếng lại* sang Dự án. Menu dọc bên trái thay thanh tab ngang.

## 3.3.8 — 27/09/2026
- Client desktop cho Vbee AI Voice: TTS 1.700+ giọng, nhận dạng giọng nói, số điểm API tự đồng bộ, phiên âm Hán Việt.
