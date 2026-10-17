**Sửa: Engine offline chạy ổn định, không còn lỗi junction** (CHUNG › Engine và Model)
- Engine không còn phụ thuộc **junction của uv** trong `pyvenv.cfg` (lỗi Windows RedirectionGuard 448 khiến engine lúc chạy lúc không). App **tự phục hồi**: sửa `pyvenv.cfg` ngay sau từng bước cài, giữ nguyên xuống dòng; gợi ý lỗi junction hiện ngay ở trang tạo giọng.
- Đã kiểm thử đầu-cuối thật: dựng giọng và trộn một dự án bằng engine offline.

**Sửa: Điểm Vbee chỉ hiện khi đã đăng nhập**
- Chưa đăng nhập / đã đăng xuất thì thẻ hiện **"Điểm còn lại: 0"**, không còn số điểm cũ của phiên trước; xoá thông tin API cũng đưa điểm về 0. Không còn số điểm hiện lại khi đăng xuất lúc đang đọc.

**Mới: Tách kho giọng OFFLINE / ONLINE**
- Trang **OFFLINE** chỉ hiện giọng offline (OmniVoice, Windows); trang **ONLINE** chỉ hiện giọng online (Vbee, Edge, OpenAI, Gemini). Không còn lẫn giọng "ONLINE · tốn điểm Vbee" trong nhóm OFFLINE; mục *Giọng đám mây* không còn ghi chữ "Windows".

**Mới: Bản dựng native biên dịch bằng Nuitka**
- Mã Python được biên dịch sang mã máy C, chạy nhanh hơn và bảo vệ mã nguồn. Dạng **một thư mục chương trình** (không còn bản 1 tệp), không giải nén ra `%TEMP%` ổ C. `MikeVoice-Setup.exe` và `MikeVoice-win.zip` đóng cả thư mục; `files.sha256` kiểm tra toàn vẹn từng tệp trước khi cài.

**Từ 4.1 — dành cho máy đang dùng 4.0**
- **Menu chia ba nhóm:** *ONLINE · cần mạng* · *OFFLINE · trên máy* · *CHUNG*. Rê chuột để biết mục nào online / offline, có tốn điểm hay không. Phím Ctrl+1..8 giữ đúng trang như 4.0.
- **Giọng đám mây:** **Edge** (miễn phí, cần mạng), **ChatGPT (OpenAI)** và **Google Gemini** (tính phí vào tài khoản của bạn); khoá API cất trong Windows Credential Manager; danh sách giọng, nghe thử.
- **Giọng Windows** (offline, miễn phí) dùng ngay trong dự án.
- **Dự án dùng mọi nguồn giọng** (Vbee, offline, Windows, Edge, OpenAI, Gemini), hiện **số điểm Vbee từng câu**.
- **Thuyết minh slide PowerPoint:** đọc `.pptx`, tạo audio từng slide theo tốc độ đọc, xuất WAV + `.srt`, PPTX có thuyết minh, video MP4.
- **Dịch phụ đề bằng LLM** (ChatGPT / Gemini): giữ mốc thời gian, bảng tên riêng, gửi thẳng sang Lồng tiếng.
- **Whisper chia lại phụ đề** không cần nhận dạng lại; **mẫu hội thoại** và **tốc độ riêng từng nhân vật**.
- **Dữ liệu theo ổ của ứng dụng:** app ở ổ nào thì dữ liệu ở ổ đó (`<ổ>:\MikeVoiceStudio\data`); lần đầu tự chép, không xoá, dữ liệu cũ từ ổ hệ thống.
- Sửa lỗi: không mất audio Vbee đã trả tiền; hỏi trước khi đổi chế độ dự án làm mất audio; dịch phụ đề không chạy song song hai lượt tính phí; không ghi đè dữ liệu người dùng.

> Engine offline vẫn **tải ở lần dùng đầu (~3 GB)** vào thư mục engine ở ổ không phải ổ hệ thống. Trọng số OmniVoice theo **CC BY-NC — chỉ dùng phi thương mại**.

---
Cài mới: tải **MikeVoice-Setup.exe** (bộ cài từng bước, không cần quyền quản trị, có lối tắt Desktop). Máy đang dùng bản cũ: chạy đè `MikeVoice-Setup.exe` — dữ liệu, giọng và engine offline giữ nguyên.
Windows hiện "Windows protected your PC" (bản chưa ký mã): bấm **More info → Run anyway**. Kiểm tra tệp tải về bằng `SHA256SUMS.txt` (PowerShell: `Get-FileHash .\MikeVoice-Setup.exe -Algorithm SHA256`).
