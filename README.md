# HoYo Launcher Mods
> Launcher quản lý mod **3DMigoto (GIMI)** cho Genshin Impact trên Windows — bật/tắt mod bằng một nhấp chuột, sửa lỗi mod hàng loạt, macro chuyên nghiệp, ReShade/StarLuxe, điểm danh HoYoLAB đa tài khoản và giao diện đa phong cách.

![Platform](https://img.shields.io/badge/platform-Windows%2010%2F11-blue)
![.NET](https://img.shields.io/badge/.NET-8.0-purple)
![Version](https://img.shields.io/badge/version-2.2.01-green)

---

## 📥 Tải về

| Gói | Link |
|---|---|
| 🚀 Launcher (bản mới nhất) | [Releases](https://github.com/manh00937-ui/HoYo_Launcher_Mods/releases/latest) |
| ⭐ Tài nguyên StarLuxe (ReShade preset pack, ~151 MB) | [StarLuxe.zip](https://github.com/manh00937-ui/HoYo_Launcher_Mods/releases/download/StarLuxe/StarLuxe.zip) — khuyến nghị: để launcher tự tải (mở tab **StarLuxe** → bấm tải) |
| 🛠 Trình Update (tự cập nhật) | `Launcher Update.zip` ở root repo — launcher tự tải về và thay thế khi bạn bấm **Cập nhật trình Update** |

---

## 📌 Đây là gì?

**HoYo Launcher Mods** là ứng dụng desktop Windows (WinUI 3 / .NET 8) giúp bạn **quản lý mod 3DMigoto cho Genshin Impact** một cách tự động, thông minh mà không cần thao tác thủ công rườm rà.

Nguyên tắc cốt lõi: toàn bộ mod được quản lý ở một kho lưu trữ tập trung, việc **bật/tắt mod thực chất là tạo/xoá liên kết thư mục (junction - `mklink /J`)** — không copy file, không di chuyển dữ liệu, bật/tắt tức thời và hoàn toàn không tốn dung lượng ổ đĩa.

Bên cạnh launcher, gói ứng dụng còn bao gồm:

| Thành phần | Công dụng |
|---|---|
| `HoYoLauncher.bat` | Lối tắt khởi động nhanh (tự kiểm tra tiến trình và chạy ngầm tray) |
| `HoYoLauncher.exe` | Tệp thực thi chính — nằm trong `System\Resources\bin\` |
| `launcher Update.exe` | Trình cập nhật độc lập (giúp cập nhật ngay cả khi launcher gặp sự cố) |
| `3DMigoto/` | Bộ loader 3DMigoto + thư mục `Mods` + Shader cache |
| `Data Mods/` | Kho dữ liệu trung tâm: icon nhân vật/vũ khí, thư mục Effects, Plugins, và cơ sở dữ liệu `datalauncher.json` |
| `System/` | Mã nguồn, tài nguyên, trình cập nhật và các plugin đi kèm |

> ⭐ **Tài nguyên StarLuxe** (ReShade + bộ preset ~151 MB) **không đóng gói sẵn** để tối ưu dung lượng gói tải — mở tab **StarLuxe** lần đầu, launcher sẽ tự động tải, cài đặt vào `System\StarLuxe` và khởi động lại ứng dụng.

---

## ⚙️ Các chức năng chính

### 1. 🎮 Tab Khởi chạy (Giao diện Khung Kính & Album động)
- **Nút Chơi / Kết thúc game lớn**, tự động dò trạng thái tiến trình game thời gian thực.
- **Trình chiếu ảnh thẻ (Hero Album)** xoay vòng tự động với nhiều hiệu ứng chuyển cảnh mượt mà (Fade, Push, Perspective).
- Thẻ **Ghim nhân vật** (chia lưới cột tự động cuộn mượt mà) và **Mod dùng gần đây** giúp bật/tắt nhanh mà không cần chuyển tab.
- **Lớp thấu kính kính mờ (Composition Blur)** nguyên bản giúp các khối thẻ hiển thị nổi bật, hài hòa và không bị tách lớp trên mọi tỉ lệ cửa sổ.
- **Tùy chỉnh bố cục kéo-thả** trực quan và chế độ **Cửa sổ trong suốt** (tắt hình nền để nhìn xuyên thấu desktop).

### 2. 🧑‍🤝‍🧑 Tab Nhân vật / Vũ khí / Hiệu ứng (Quản lý Mod thông minh)
- Tìm kiếm nhanh theo tên, sắp xếp linh hoạt, ghim lên đầu, tuỳ chỉnh icon đại diện.
- **Bật/tắt mod tức thì** chỉ bằng một cú nhấp vào thẻ mod.
- **Thêm Mod hàng loạt**: Nhận diện thông minh file nén (`.zip`, `.rar`, `.7z`, v.v.) hoặc thư mục, tự động quét tệp `.ini` bên trong để đoán và phân loại vào đúng nhân vật tương ứng, giảm thiểu thao tác thủ công.
- Hỗ trợ menu chuột phải để **Sửa lỗi mod** hoặc **Khôi phục định dạng gốc**.

### 3. ⭐ Tab StarLuxe (ReShade tích hợp)
- **Tự động tiêm ReShade** vào game đúng thời điểm khởi chạy.
- Quản lý kho preset (SPECTRA, Stella Mod, Alchemy, v.v.), tự động áp dụng vào `ReShade.ini` của game.
- Giao diện quản lý trạng thái tài nguyên: Tải tự động từ GitHub, gỡ bỏ trực tiếp vào Thùng rác của launcher, và **cơ chế bảo vệ thông minh** không làm mất tài nguyên của người dùng khi cập nhật launcher.

### 4. 🌐 Tab Admin [Quản trị viên] — HoYoLAB đa tài khoản
- Quản lý **tối đa 5 tài khoản HoYoLAB** đồng thời với giao diện chip chuyển đổi nhanh chóng.
- **Điểm danh ngầm tự động hằng ngày** cho toàn bộ tài khoản đã liên kết.
- Theo dõi chỉ số thời gian thực (Nhựa nguyên chất, Xu Chén Âm Trấn Ca) cập nhật mỗi 10 phút kèm hệ thống thông báo trạng thái gần đầy.
- Đổi mã quà tặng (redeem code) trực tiếp trong launcher.

### 5. 📦 Tab Cơ sở dữ liệu & 🧮 Dự Tính Bồi Dưỡng
- Tra cứu nguyên liệu theo ngày, đồng bộ trực tiếp với kho đồ HoYoLAB và phong cách Paimon.moe.
- Công cụ **HoYoLAB Calculator** nhúng trực tiếp qua WebView2 giúp tính toán nguyên liệu nâng cấp nhân vật/vũ khí chính xác.

### 6. 🔧 Tab Fix Mods (Chẩn đoán & Sửa lỗi cấu hình)
- Tự động quét các tệp `.ini` thiếu lệnh chạy `run =` cho **ORFix / NNFix / GIMI**.
- **Tra Cứu & Đề Xuất**: Chẩn đoán sâu các lỗi phổ biến như thiếu tệp `.dds`, dung lượng 0 byte, lệch định dạng DXGI/fourCC, hoặc xung đột `drawindexed` vượt quá giới hạn bộ đệm.
- Mọi thao tác sửa lỗi đều tạo bản sao lưu `.bak` và hỗ trợ **Hoàn tác (Undo)** an toàn.

### 7. ⌨️ Tab Macro (Macro Cơ Bản & Macro Pro)
- **Macro Cơ Bản**: Ghi/phát lại chuỗi phím bấm với độ trễ ngẫu nhiên tự nhiên, hỗ trợ điều kiện lọc "Chỉ chạy trong Game".
- **Macro Pro**: Ghi nhận cả bàn phím và chuyển động chuột thô thông qua Windows Raw Input, giúp tái hiện chính xác các combo phức tạp.
- **Phím thoát khẩn cấp (Panic Key)**: Sử dụng tổ hợp `Ctrl + Alt + Shift + F12` hoặc phím `Pause` để lập tức ngắt toàn bộ macro và nhả sạch phím/chuột bị kẹt.

### 8. 🎨 Giao diện & Đa ngôn ngữ (Hỗ trợ 3 kiểu giao diện)
- **Đa ngôn ngữ**: Hỗ trợ hoàn chỉnh 5 ngôn ngữ (Tiếng Việt, English, 简体中文, 日本語, 한국어).
- **Ba kiểu giao diện linh hoạt**:
  - **Cổ điển**: Giao diện truyền thống quen thuộc.
  - **Hiện đại**: Thanh điều hướng thu gọn với tuỳ chọn màu chủ đạo phong phú.
  - **Liquid Glass**: Trải nghiệm giao diện HTML nhúng qua WebView2 hiện đại, mượt mà.

---

## 🚀 Hướng dẫn nhanh cho người mới

1. **Giải nén:** Giải nén toàn bộ gói vào một thư mục riêng biệt (Ví dụ: `C:\HoYo Launcher\`). Đảm bảo mọi tệp cấu trúc nằm chung trong một thư mục gốc và không đặt trực tiếp tại thư mục gốc ổ đĩa (`C:\`).
2. **Khởi chạy:** Nhấp đúp vào **`HoYoLauncher.bat`** để mở ứng dụng (cần cấp quyền Quản trị viên - Administrator ở lần chạy đầu tiên).
3. **Thiết lập:** Hoàn tất trang hướng dẫn ban đầu để liên kết thư mục game, thư mục 3DMigoto và thư mục Data Mods.
4. **Sử dụng:** Thêm mod vào các tab tương ứng, bật mod bằng một nhấp chuột và bấm **Chơi** để bắt đầu trải nghiệm.

---

## 🛠️ Trình phát triển & Đóng gói

- **Công nghệ cốt lõi:** WinUI 3, .NET 8, WPF (Trình cập nhật), WebView2.
- **Cấu trúc Solution:** Mở `System\HoYoLauncher.sln` bằng Visual Studio 2022 để tiến hành phát triển hoặc biên dịch mã nguồn.

---

## ⚠️ Tuyên bố miễn trừ trách nhiệm
- Dự án này là công cụ quản lý cá nhân mã nguồn mở, không liên kết trực tiếp với miHoYo hay HoYoverse.
- Việc sử dụng mod có thể vi phạm Điều khoản Dịch vụ của trò chơi; người dùng tự chịu mọi rủi ro liên quan đến tài khoản cá nhân.