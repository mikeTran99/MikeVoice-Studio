# Hướng dẫn sử dụng cho khách hàng — Mike Voice Studio 4.1.1

## 1. Giới thiệu

**Mike Voice Studio** là ứng dụng Windows chuyển văn bản thành giọng nói và giọng nói thành chữ. Vừa dùng **online**
(Vbee 1.700+ giọng, Edge, OpenAI, Google Gemini) vừa dùng **offline** ngay trên máy (OmniVoice + Whisper, không tốn
điểm, không cần mạng sau khi tải model).

| Thành phần | Yêu cầu |
|---|---|
| Hệ điều hành | Windows 10 / 11 bản 64-bit |
| Màn hình | Từ 1024 × 600 trở lên (laptop 1366 × 768 dùng thoải mái) |
| Mạng Internet | Cần cho các mục ONLINE và khi tải engine offline. Mục OFFLINE không cần mạng |
| Card NVIDIA (tuỳ chọn) | Engine offline chạy nhanh trên GPU NVIDIA; không có GPU vẫn chạy được, chậm hơn |
| Microsoft PowerPoint (tuỳ chọn) | Chỉ cần khi xuất PPTX / MP4 ở trang Thuyết minh slide |

## 2. Cài đặt

### 2.1 Tải về

Vào trang phát hành <https://github.com/mikeTran99/MikeVoice-Studio/releases/latest> và chọn một tệp:

| Tệp | Dùng khi | Ghi chú |
|---|---|---|
| `MikeVoice-Setup.exe` | Cài lên máy (khuyên dùng) | Bộ cài đủ bước: chọn thư mục → ☑ lối tắt Desktop → Cài đặt → ☑ Mở Mike Voice ngay |
| `MikeVoice-win.zip` | Cài bằng script (không cần quyền quản trị) | Giải nén **cả thư mục** rồi bấm đúp `Cai_dat.cmd` |
| `SHA256SUMS.txt` | Kiểm tra tệp tải về | So với lệnh `Get-FileHash .\MikeVoice-win.zip` trong PowerShell |

> Bản mới biên dịch native (chạy nhanh, bảo vệ mã nguồn) là **nguyên một thư mục chương trình**, không còn
> bản 1 tệp. Giải nén giữ nguyên cả thư mục rồi mới chạy `Cai_dat.cmd`.

> [!IMPORTANT]
> **Nên cài ở ổ khác ổ C** (ví dụ ổ D hoặc E). Dữ liệu của app (dự án, lịch sử, audio) luôn nằm **cùng ổ với app**:
> app ở ổ nào thì dữ liệu ở `<ổ đó>:\MikeVoiceStudio\data`. Chỉ khi app nằm ở ổ C, dữ liệu mới vào
> `%LOCALAPPDATA%\MikeVoiceStudio`.

### 2.2 Bộ cài `MikeVoice-Setup.exe`

1. Chép `MikeVoice-Setup.exe` sang ổ muốn cài (ví dụ ổ D hoặc E) rồi bấm đúp. Bộ cài **tự đề xuất thư mục cùng ổ**
   (`<ổ đó>:\MikeVoiceStudio\app`); chạy từ ổ C thì đề xuất `%LOCALAPPDATA%\Programs\MikeVoice`. Bấm **Chọn...** để đổi.
2. Không cần quyền quản trị. Đang mở Mike Voice thì bộ cài tự đóng app trước khi thay bản mới.
3. Nếu Windows hiện bảng xanh **"Windows protected your PC"**: bấm **More info** → **Run anyway**. Bản phát hành
   chưa được ký mã nên Windows cảnh báo ở lần đầu — đây không phải virus.

### 2.3 Cài bằng `Cai_dat.cmd`

1. Giải nén `MikeVoice-win.zip` ra ổ muốn cài (chuột phải → Extract All).
2. Bấm đúp **`Cai_dat.cmd`** → app cài vào `<ổ đó>:\MikeVoiceStudio\app` (giải nén ở ổ C thì vào
   `%LOCALAPPDATA%\Programs\MikeVoice`), có lối tắt Start + Desktop và mục gỡ trong **Settings › Apps**.
3. Bộ cài tự kiểm tra mã SHA-256: tệp chép dở / bị sửa sẽ không được cài.

## 3. Bản đồ menu

Menu dọc bên trái chia ba nhóm. Rê chuột lên từng mục để xem mục đó online hay offline, có tốn điểm hay không.

| Nhóm | Mục | Dùng để |
|---|---|---|
| **ONLINE · cần mạng** | Phòng thu Vbee | Đọc văn bản bằng 1.700+ giọng Vbee |
| | Giọng đám mây | Giọng Windows, Edge, OpenAI, Gemini: nhập khoá API, nghe thử |
| | Giọng → Chữ (Vbee) | Nhận dạng giọng nói bằng Vbee, xuất `.txt` / `.srt` / `.vtt` |
| | Dịch phụ đề | Dịch `.srt` bằng ChatGPT / Gemini, giữ mốc thời gian |
| **OFFLINE · trên máy** | Đọc văn bản | Dự án văn bản, mỗi câu một giọng, xuất WAV/MP3 kèm `.srt` |
| | Hội thoại nhóm | Kịch bản `Tên: lời`, gán giọng + tốc độ từng nhân vật |
| | Lồng tiếng theo phụ đề | Đọc đúng mốc thời gian của `.srt` |
| | Thuyết minh slide | Đọc ghi chú (không có thì chữ trên slide) của `.pptx`, xuất WAV + `.srt`, PPTX, MP4 |
| | Giọng → Chữ (Whisper) | Nhận dạng trên máy, chia lại phụ đề, *Lồng tiếng lại* |
| | Giọng của tôi | Sao chép giọng từ tệp mẫu, thiết kế giọng bằng mô tả, gói `.vcp` |
| **CHUNG** | Lịch sử · Engine và Model · Nhật ký · Cài đặt | Tệp đã tạo, cài engine offline / REST API, nhật ký lỗi, kết nối Vbee |

## 4. Giọng nào tốn tiền, giọng nào miễn phí

| Nguồn giọng | Chi phí |
|---|---|
| **Vbee** | Trừ **điểm Vbee** theo số ký tự (điểm đã dùng hiện ở đầu cửa sổ và từng câu dự án). Nghe mẫu giọng miễn phí |
| **OpenAI**, **Google Gemini** | Tính phí vào **tài khoản OpenAI / Google của bạn** (khoá API của bạn) |
| **Windows** | Miễn phí, offline (giọng có sẵn của Windows) |
| **Edge** | Miễn phí, cần mạng |
| **OmniVoice** (engine offline) | Miễn phí, chạy trên máy. Trọng số model theo giấy phép **CC BY-NC — chỉ dùng phi thương mại** |

Khoá API (Vbee App ID / Token, OpenAI, Gemini) và phiên đăng nhập Vbee được cất trong **Windows Credential Manager**,
không nằm trong tệp văn bản và luôn được che trong nhật ký.

## 5. Cài engine offline (không chiếm ổ C)

1. Mở **CHUNG › Engine và Model** → bấm **Cài engine offline**.
2. Lần đầu tải khoảng 3 GB (Python + PyTorch CUDA), sau đó là model. Mọi thứ — Python, PyTorch, model, cache, tệp tạm,
   audio dự án — nằm trong **thư mục engine**.
3. Mặc định thư mục engine ở `<ổ của app>:\MikeVoiceStudio\offline` (app ở ổ C thì ở `%LOCALAPPDATA%`). Muốn để ổ khác:
   **Đổi thư mục engine** trước khi cài.

## 6. Cập nhật và gỡ cài đặt

- **Cập nhật**: tải bản mới, chạy lại `MikeVoice-Setup.exe` (hoặc `Cai_dat.cmd` của bản mới). Bản cũ được thay đúng chỗ;
  dữ liệu, giọng và engine offline giữ nguyên.
- **Gỡ**: **Settings › Apps › Mike Voice Studio › Uninstall**. Chỉ xoá chương trình; **dữ liệu**
  (`<ổ>:\MikeVoiceStudio\data`) và **engine offline** vẫn giữ lại — muốn xoá hẳn thì tự xoá hai thư mục đó.

## 7. Khi có sự cố

- Mở **CHUNG › Nhật ký** → **Xuất .txt** rồi gửi kèm khi báo lỗi (Token / App ID đã được che sẵn).
- Kiểm tra môi trường: chạy `MikeVoice_Vbee.exe --self-test`; báo cáo lưu ở `<thư mục dữ liệu>\logs\self-test.txt`.
