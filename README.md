# Psychiatry Offline — Safari/iPad PWA

## Quan trọng
- Thư mục app (`index.html`, `sw.js`, `manifest.webmanifest`, icons) **không chứa dữ liệu bệnh nhân**.
- File `psychiatry_data_IMPORT_ON_IPAD.json` **có dữ liệu bệnh nhân thật**. KHÔNG upload file này lên GitHub/Netlify/Cloudflare hoặc nơi công khai.

## Cách dùng
1. Đưa **chỉ 5 file app shell** lên một static HTTPS host: `index.html`, `sw.js`, `manifest.webmanifest`, `icon-180.png`, `icon-512.png`.
2. Trên iPad mở URL bằng Safari.
3. Share → Add to Home Screen → Open as Web App.
4. Mở app từ Home Screen.
5. Bấm **Nhập dữ liệu** → chọn `psychiatry_data_IMPORT_ON_IPAD.json` từ Files.
6. Sau khi import, dữ liệu được lưu trong IndexedDB trên iPad. App shell được Service Worker cache để mở khi không có Internet.
7. Dùng **Backup mã hóa** định kỳ; lưu file `.psybackup` ở vị trí an toàn.

## Lưu ý Safari/iPad
- Không xóa Website Data/Safari data của site này, vì có thể xóa IndexedDB.
- Không xóa app web trước khi đã tạo backup mã hóa.
- Dữ liệu không được gửi lên server bởi code app. Static host chỉ phục vụ app shell không chứa PHI.
- Nếu dùng Private Browsing, persistence có thể không ổn định; không dùng Private Browsing.

## Backup
Backup sử dụng Web Crypto: PBKDF2-SHA256 (250,000 vòng) + AES-256-GCM. Mật khẩu không được lưu trong app.
