# HoYo Launcher Mods
> Launcher quản lý mod **3DMigoto (GIMI)** cho Genshin Impact trên Windows — bật/tắt mod bằng một cú nhấp, sửa lỗi mod hàng loạt, macro, ReShade và nhiều hơn nữa. Giao diện tiếng Việt, thiết kế cho người mới.

![Platform](https://img.shields.io/badge/platform-Windows%2010%2F11-blue)
![.NET](https://img.shields.io/badge/.NET-8.0-purple)
![Version](https://img.shields.io/badge/version-2.0.11-green)

---

## 📌 Đây là gì?

**HoYo Launcher Mods** là ứng dụng desktop Windows (WinUI 3 / .NET 8) giúp bạn **quản lý mod 3DMigoto cho Genshin Impact** mà không cần làm thủ công bằng cách copy – đổi tên – dán thư mục như trước.

Nguyên tắc cốt lõi: toàn bộ mod được quản lý ở một nơi, việc **bật/tắt mod chỉ là tạo/xoá liên kết thư mục (junction)** — không copy file, không di chuyển file, bật/tắt tức thì và không tốn dung lượng.

Ngoài launcher, gói còn kèm:

| Thành phần | Công dụng |
|---|---|
| `HoYo Launcher Mods.bat` | Cách mở launcher nhanh nhất (double-click là chạy) |
| `HoYo Launcher Update.exe` | Chương trình cập nhật launcher bằng file `.zip` (chạy được cả khi launcher hỏng/bị xoá) |
| `3DMigoto/` | Loader 3DMigoto + thư mục `Mods` + shader cache (phần game đọc vào) |
| `Data Mods/` | "Kho" dữ liệu: icon nhân vật/vũ khí, thư mục Effects, thư mục Plugins |
| `HoYo Launcher Mods/` | **Mã nguồn** (Visual Studio 2022, solution `HoYoLauncherModsWinUI.sln`) |

---

## ⚙️ Các chức năng chính

### 1. 🎮 Tab Khởi chạy (màn hình chính)
- Nút **Chơi / Kết thúc game**, tự dò tiến trình game đang chạy hay chưa.
- **Album ảnh** xoay vòng (tuỳ chỉnh tỉ lệ khung dọc/ngang bằng thanh trượt).
- Danh sách **nhân vật đã ghim** + **mod dùng gần đây** để bật/tắt nhanh không cần vào tab khác.
- Thanh thông tin: số mod đang bật/tổng số, nhân vật nào đang có mod bật, các thống kê nhân vật/vũ khí/hiệu ứng.
- **Kéo–thả tuỳ chỉnh bố cục** các khối trên trang.

### 2. 🧑‍🤝‍🧑 Tab Nhân vật / Vũ khí / Hiệu ứng (quản lý mod)
- Lưới danh sách bên trái: **tìm kiếm theo tên**, sắp xếp (A-Z / thay đổi gần nhất / số lượng mod), **ghim lên đầu**, đổi icon, tạo mới.
- Lưới mod bên phải: **bật/tắt mod bằng cách chạm vào thẻ**, ghim mod, đổi icon, mở thư mục gốc, gán vào **Thư Mục Mod** (nhóm tô màu), xoá (vào Thùng rác, không xoá thẳng).
- Menu chuột phải từng mod: **🛠️ Sửa lỗi mod** / **↩️ Khôi phục định dạng gốc**.
- **Thêm Mod** nhận cả file nén (`.zip`, `.rar`, `.7z`, `.tar`, `.gz`…) lẫn thư mục đã giải nén — tự giải nén tạm bằng SharpCompress, **không cần cài 7-Zip/WinRAR**.
- Mod chỉ có `ini` + texture (không có ảnh thumbnail) tự dùng icon nhân vật/vũ khí chứa nó.

### 3. 🗂️ Tab Chưa phân loại
Mod đã thêm vào launcher nhưng chưa gán cho nhân vật/vũ khí/hiệu ứng nào — cùng bộ thao tác như trên, dùng để chứa mod "linh tinh" trước khi phân loại.

### 4. 🎨 Tab Thư Mục Mod (nhóm mod)
Tạo các **nhóm mod tô màu** tuỳ ý (theo bộ trang phục, theo tác giả…), gán nhiều mod bất kể thuộc nhân vật/vũ khí nào vào cùng một nhóm. Thẻ mod ở các tab khác hiện dải màu nhỏ theo nhóm — quản lý bộ mod theo "era"/theo mùa rất tiện.

### 5. 🔧 Tab Fix Mods (sửa lỗi mod hàng loạt)
Nhiều mod texture-override thiếu/sai lệnh `run =` nên không hiện đúng với **ORFix / NNFix / GIMI** (dự án LeoTools). Launcher tự quét và sửa theo đúng chuẩn `ORFixGuide.md`:

- Sắp lại thứ tự `NormalMap → Diffuse → LightMap` + đánh số lại slot `ps-t0/1/2`.
- Thêm `run = CommandList\global\ORFix\ORFix` (hoặc `NNFix`) nếu thiếu.
- Xử lý khối `Resource\GIMI\...` ở section Face → thêm `run = CommandList\GIMI\SetTextures`.
- **Tự bỏ qua section "Face"** (theo khuyến cáo của guide — thêm ORFix dưới face texture sẽ gãy mod).
- Hiểu mod gộp nhiều biến thể (hậu tố `.0`, `_1`, `6_2`…), khối có dòng overlay/viền, mod chia nhiều tầng `if/elif/else/endif`.

**2 cách dùng:**
- **FIX ALL MODS** — quét toàn bộ (hoặc 1 nhân vật/vũ khí/hiệu ứng cụ thể), tự tải `ORFix.ini`/`ORFixAPI.ini` mới nhất từ GitHub (kiểm tra mỗi 24h), hỏi xác nhận, chạy thêm công cụ ngoài `57ReleaseVersion.exe`.
- **Sửa lỗi mod / Khôi phục định dạng gốc** — bản thu nhỏ cho **đúng 1 mod**, làm thẳng trên thư mục thật, không cần mod đang bật.

→ Mọi lần sửa đều **tự sao lưu**, lưu vào "Lịch sử sửa lỗi" kèm nút **Hoàn tác**.

### 6. ⌨️ Tab Macro (2 chế độ)

**Macro Cơ Bản** — ghi/phát lại bàn phím:
- Ghi đúng thứ tự bấm/nhả phím thật + khoảng nghỉ (hook `WH_KEYBOARD_LL` toàn hệ thống — ghi được cả khi Game đang focus).
- Phát lại qua `SendInput`, mỗi khoảng nghỉ cộng thêm **độ trễ ngẫu nhiên ±10–30ms** (chỉnh được) cho tự nhiên hơn.
- **3 điều kiện dừng**: bấm phím bất kỳ / bấm lại tổ hợp phím tắt / lặp đủ N lần.
- Tổ hợp phím tắt **tối đa 3 phím**, tuỳ ý (không bắt buộc có modifier).
- Chế độ **"Chỉ chạy trong Game"**: chỉ nhận phím tắt khi Game đang là cửa sổ foreground, tự dừng nếu Game mất focus — tránh gõ nhầm phím sang ứng dụng khác.
- Chỉ 1 macro được phát cùng lúc (tránh 2 luồng SendInput giẫm lên nhau).

**Macro Pro** — ghi cả bàn phím **lẫn chuột**:
- Ghi di chuyển/lia chuột, bấm/nhả nút, cuộn wheel — phát lại y hệt 1 combo phức tạp.
- Di chuyển chuột ghi kiểu **TƯƠNG ĐỐI qua Windows Raw Input** — đúng loại dữ liệu mà game 3D tự đọc, tái tạo được góc quay camera kể cả khi con trỏ bị khoá/ẩn trong game.
- **Phím tắt Bật/Tắt GHI toàn cục** (1 phím duy nhất, dùng chung cho danh sách) — vì Game chạy toàn màn hình nên không thể bấm nút trên UI; chọn macro trước khi quay sang Game rồi bấm phím.
- **Thông báo Windows (toast)** thật ở góc màn hình khi bắt đầu/kết thúc ghi và phát — vì launcher chạy nền sau Game.
- ⚠️ **Cảnh báo quyền Admin**: nếu Game chạy quyền cao hơn, Windows UIPI có thể chặn `SendInput` → banner gợi ý khởi động lại launcher bằng quyền Quản trị.
- Không có UI sửa từng bước đã ghi (dữ liệu chuột quá lớn, sửa tay dễ hỏng thứ tự) — ghi sai thì xoá ghi lại.

### 7. 🗑️ Tab Thùng rác
Mod bị xoá **không mất ngay** — vào Thùng rác kèm mốc thời gian + mục sở hữu cũ, có thể khôi phục lại hoặc dọn vĩnh viễn.

### 8. ⚙️ Tab Cài đặt
- Khai báo/tự dò toàn bộ đường dẫn: `GenshinImpact.exe`, `3DMigoto Loader.exe`, thư mục `Mods`, thư mục dữ liệu launcher, thư mục Album.
- **Đồng bộ `target =` trong `d3dx.ini`** theo đường dẫn game đã chọn.
- Kiểm tra cấu hình còn hợp lệ hay không, bật/tắt **khởi chạy cùng Windows**, các tuỳ chọn giao diện.

### 9. 🧩 Hệ thống Plugin (thêm tab mới mà không sửa code lõi)

| Plugin | Công dụng |
|---|---|
| **ReShade – chỉnh màu game** | Tích hợp ReShade (từ gói XXMI ReShade Add-On). Bật plugin là junction `reshade-shaders` + `ReShade.ini` được tạo ngay vào thư mục game; mỗi lần bấm Bắt đầu Game là injector canh sẵn tiêm ReShade vào đúng khoảnh khắc game xuất hiện. **Phím Home** = bật/tắt ReShade, **F8** = bảng chỉnh màu, **PrintScreen** = chụp không UI. |
| **Chạy chương trình sau khi vào game** | Gán nhiều chương trình (Discord, tool overlay, RPC…) tự chạy kèm ngay sau khi game khởi động thành công — mỗi chương trình đặt delay riêng, bật/tắt độc lập. |
| **Thêm mod nhanh (kéo–thả file nén)** | Cửa sổ thả mod luôn mở: kéo `.zip/.rar/.7z/...` hoặc thư mục vào → chọn vị trí (nhân vật/vũ khí/hiệu ứng), chọn icon, đặt tên → thêm. Cửa sổ không tự đóng nên thêm liên tục nhiều mod mà không mở lại tab. |
| **Gộp mod đang bật thành thư mục** | Tick chọn nhiều Nhân vật/Vũ khí/Hiệu ứng → tạo 1 thư mục mod gom toàn bộ mod đang bật của các mục đó vào tab "Thư Mục Mod" với 1 nút bấm. |

*(Có cả `SamplePlugin/` — ví dụ cách viết plugin riêng: Hello, GachaHistory, TabDemo…)*

### 10. 🔄 Tích hợp hệ thống
- **Khay hệ thống (tray)** + **phím tắt toàn cục** — thu nhỏ về khay vẫn chạy nền.
- **Khởi động cùng Windows** (ghi Registry `HKCU\...\Run`, không cần Admin).
- **Ghim cửa sổ luôn trên cùng khi game đang chạy** (dò tiến trình mỗi 2 giây).
- **Phím F10**: tự gửi cho 3DMigoto sau mỗi lần bật/tắt/xoá mod để nạp lại mod **không cần restart game**.
- **Cập nhật launcher**: nút trong Cài đặt → mở `HoYo Launcher Update.exe` → kéo-thả file `.zip` → xác minh (giải nén, kiểm tra có `HoYoLauncherModsWinUI.exe`, chặn đường dẫn nguy hiểm `..`) → tự thay thế (giữ backup `.bak_<thời gian>`).

---

## 🚀 Hướng dẫn cho người mới (5 phút là chạy)

### Bước 1 — Yêu cầu
- Windows 10/11 (64-bit), đã cài Genshin Impact bản PC.
- Không cần cài .NET (bản đã đóng gói sẵn), không cần 7-Zip/WinRAR.

### Bước 2 — Giải nén
Giải nén toàn bộ gói vào **một thư mục riêng**, ví dụ:

```
C:\HoYo Launcher\
├── 3DMigoto\
├── Data Mods\
├── HoYo Launcher Mods\
├── HoYo Launcher Mods.bat
└── HoYo Launcher Update.exe
```

⚠️ **Quy tắc quan trọng :** mọi đường dẫn phải nằm **trong cùng một thư mục gốc** với launcher (thư mục chứa `3DMigoto`, `Data Mods`, `HoYo Launcher Mods.bat`).
- ❌ Đặt `Data Mods` ở `C:\Data Mods` và launcher ở ổ khác → bị từ chối.
- ❌ Đặt thư mục ở ngay **gốc ổ `C:\`** → bị từ chối.
- ✅ Gom tất cả vào 1 thư mục gốc, ví dụ `C:\HoYo Launcher\...`

> Mẹo: nếu bạn copy gói ra chỗ khác rồi chạy, launcher **tự khởi tạo như người mới** — không đụng tới dữ liệu `datalauncher.json` của bản đang dùng hằng ngày.

### Bước 3 — Mở launcher
Double-click **`HoYo Launcher Mods.bat`** (hoặc `HoYoLauncherModsWinUI.exe` trong `HoYo Launcher Mods\HoYo Launcher Mods\bin\x64\Debug\...`).

### Bước 4 — Thiết lập lần đầu
Lần đầu mở, launcher chỉ hiện **1 trang thiết lập duy nhất**, bạn khai 3 đường dẫn:

1. **Thư mục Game** — đường dẫn `GenshinImpact.exe` (nhập tay / nút "Chọn…" / **Quét tự động**).
2. **Thư mục 3DMigoto** — nút "Chọn…" hoặc Quét tự động (tự suy ra `3DMigoto Loader.exe` và thư mục `Mods`).
3. **Thư mục Data Mods** — mặc định sẵn, Quét tự động chờ kết quả.

> Launcher tự quét thư mục gốc khi mở, nên 3 ô thường **đã điền sẵn** — bạn chỉ cần bấm ✔ **"Vào Launcher"** (nút chỉ hiện khi đủ 3 đường dẫn hợp lệ).

### Bước 5 — Thêm mod
Vào tab **Nhân vật** (hoặc Vũ khí / Hiệu ứng) → **Thêm Mod** → chọn file `.zip/.rar/.7z/...` hoặc thư mục đã giải nén → chọn nhân vật → đặt tên → xong.
*Hoặc dùng plugin **Thêm mod nhanh** rồi kéo–thả file vào khung.*

### Bước 6 — Bật/tắt mod
**Chạm vào thẻ mod** là bật/tắt. Launcher tự:
- tạo/xoá junction trong thư mục `Mods` của 3DMigoto,
- gửi **F10** để 3DMigoto nạp lại,
- ghi vào "mod gần đây" cho tab Khởi chạy.

### Bước 7 — Vào game
Tab **Khởi chạy** → bấm **Chơi**. Muốn đổi mod giữa chừng → ra ngoài bật/tắt, vào game bấm **F10** là mod áp dụng ngay.

### Bước 8 — Mod lỗi (không hiện / vỡ texture)?
Tab **Fix Mods** → **FIX ALL MODS** (hoặc chuột phải → **Sửa lỗi mod** trên từng thẻ) → xác nhận → chờ. Lỗi gì cũng bấm **Hoàn tác** trong Lịch sử sửa lỗi là về lại như cũ.

### Bước 9 — (Tuỳ chọn) Macro & ReShade
- **Macro**: tab Macro → tạo macro → ghi thao tác → đặt phím tắt. Bật **"Chỉ chạy trong Game"** để không gõ nhầm ra app khác.
- **ReShade**: tab Plugin → bật **ReShade – chỉnh màu game** → vào game bấm **F8** để mở bảng chỉnh màu.

---

## ❓ Xoá/ghi chú an toàn

- **Không xoá thẳng mod**: mọi thao tác xoá đều đưa vào Thùng rác của launcher.
- **Mọi lần Sửa lỗi đều có bản sao lưu** tại `%LocalAppData%\HoYoLauncherModsWinUI\FixBackups\` (giữ tối đa 15 mục).
- **Thùng rác mod**: `%LocalAppData%\HoYoLauncherModsWinUI\Trash\`
- **Log crash**: `%LocalAppData%\HoYoLauncherModsWinUI\crash.log`
- **Cấu hình + database**: 1 file JSON (`datalauncher.json`) trong thư mục Data Mods.

## 🛠️ Troubleshooting (hay gặp)

| Sự cố | Cách xử lý |
|---|---|
| Launcher không mở / báo lỗi đường dẫn | Kiểm tra mọi thứ nằm trong **1 thư mục gốc** và **không ở gốc ổ đĩa** (xem Bước 2) |
| Bật mod nhưng trong game không thấy | Bấm **F10** trong game; kiểm tra tab Cài đặt → đường dẫn `Mods` đúng; chạy lại **FIX ALL MODS** |
| Game không khởi động từ launcher | Kiểm tra đường dẫn `GenshinImpact.exe` + `3DMigoto Loader.exe` ở Cài đặt (nút kiểm tra cấu hình) |
| Macro không gõ được vào game | Game chạy quyền cao hơn → chạy launcher bằng **quýền Quản trị** (banner trong tab Macro sẽ nhắc) |
| Mod bị xoá nhầm | Tab **Thùng rác** → Khôi phục |
| Sửa lỗi mod làm mod hỏng | Tab Fix Mods → **Lịch sử sửa lỗi** → **Hoàn tác** |
| Đổi thư mục Data Mods | Cài đặt → chọn thư mục mới → file `datalauncher.json` tự đi theo |

---

## 🏗️ Dự án dành cho người phát triển

- **UI**: WinUI 3 + `NavigationView` (không dùng BackStack — tránh rò rỉ bộ nhớ khi chạy dài hạn có minimise-to-tray).
- **MVVM**: `CommunityToolkit.Mvvm` (`ObservableObject`, `[RelayCommand]`).
- **DI**: `Microsoft.Extensions.DependencyInjection`, service đăng ký `AddSingleton` trong `App.xaml.cs`.
- **Dữ liệu**: 1 file JSON duy nhất qua `DatabaseService` / `AppStateService` (phát sự kiện `DatabaseChanged` để UI tự làm mới).
- **Cấu trúc**: `Views/` (XAML + code-behind) · `ViewModels/` · `Services/` (logic thuần C#) · `Models/` · `Behaviors/`, `Converters/` · `Assets/`.
- **Build**: Visual Studio 2022 với workload *.NET Desktop Development* + *Windows App SDK C# Templates*, .NET 8 SDK → mở `HoYoLauncherModsWinUI.sln` → Restore NuGet → F5.
- Plugin viết bằng .NET 8 thuần, giao tiếp qua `PluginContracts/ILauncherPlugin.cs` (`IPluginHost`, `IGameLaunchListener`, `IGamePreLaunchListener`).

## 📖 Thư mục mã nguồn

```
HoYo Launcher Mods v2.0.11/
├── 3DMigoto/                     # Loader + Mods + ShaderCache/ShaderFixes
├── Data Mods/                    # Database (icon Characters/Weapons, Effects, Plugins)
├── HoYo Launcher Mods/           # NGUỒN NẰM Ở ĐÂY
│   ├── HoYoLauncherModsWinUI.sln
│   ├── ORFixGuide.md             # Chuẩn sửa lỗi mod mà Fix Mods tuân theo
│   ├── CHANGELOG_*.md            # Lịch sử thay đổi chi tiết
│   ├── PluginContracts/          # Hợp đồng API cho plugin
│   ├── Plugins/                  # 4 plugin chính (ReShade, PostLaunch, QuickImport, BulkFolder)
│   ├── SamplePlugin/             # Ví dụ plugin để học cách viết plugin mới
│   └── HoYo Launcher Mods/       # Project WinUI 3 (Views/ViewModels/Services/Models)
├── HoYo Launcher Mods.bat        # Bấm đúp để mở launcher
└── HoYo Launcher Update.exe      # Cập nhật launcher bằng file .zip
```

## ⚠️ Disclaimer

- Đây là **dự án cá nhân**, không liên kết với miHoYo/HoYoverse.
- Mod chỉ chỉnh sửa **client phía máy bạn** (3DMigoto inject vào DirectX 11), không đụng tới server.
- Tuy nhiên, **sử dụng mod vẫn có thể vi phạm Điều khoản Dịch vụ của Genshin Impact** — rủi ro khóa tài khoản là do **bạn tự chịu**. Nên dùng tài khoản phụ nếu muốn an toàn.
- Luôn tải mod từ nguồn uy tín; sao lưu file game trước khi cài bất cứ thứ gì lạ.

## 🙏 Credits

- [3DMigoto](https://github.com/bo3b/3Dmigoto) (bo3b) — core inject/render hook
- [GIMI – GI Model Importer](https://github.com/SilentNightSound/GI-Model-Importer) (SilentNightSound) — chuẩn mod nhân vật
- [ORFix / LeoTools](https://github.com/leotorrez/LeoTools) — fix `run =` cho ORFix/NNFix
- ReShade (crosire) + gói XXMI ReShade Add-On (Caverabbit/SpectrumQT)
- Các tác giả mod trong gói — credit nằm trong từng thư mục mod

## 📜 License

Miễn trừ trách nhiệm — dùng trên rủi ro của bạn. Nếu bạn chia sẻ lại mã nguồn, vui lòng ghi credit.

