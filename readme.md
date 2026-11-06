# GS.studio – Chụp ảnh kỷ yếu & tốt nghiệp TP.HCM

Trang giới thiệu & bảng giá một trang (single-page) cho **GS.studio – Golden Shot**, studio chụp kỷ yếu & tốt nghiệp. Giao diện sáng tone kem ngà – trắng – vàng golden, ưu tiên điện thoại. Gồm hero (ảnh khách thật), câu chuyện thương hiệu, khu "Ảnh khách thật" (kèm video tặng kèm) và 3 tab: Bảng giá, Chuẩn bị trước buổi chụp, Đặt lịch & Báo giá.

## Công nghệ
- HTML + CSS + JavaScript thuần trong **một file `index.html`** – không cần build.
- Google Fonts: Playfair Display (tiêu đề) & Be Vietnam Pro (nội dung).
- `localStorage` lưu gói đã chọn, loại khách, checklist, dữ liệu form.
- Netlify Image CDN tự nén ảnh sang WebP khi chạy trên Netlify (mở file trực tiếp trên máy vẫn hiển thị ảnh gốc).

## Hướng dẫn nhanh
1. **Sửa liên hệ & giá:** mở `index.html`, tìm `const CONFIG` ở đầu file → sửa `lienHe.sdt`, `sdtGoi`, `facebook`, `messenger`, `tiktok`, `instagram` (để trống = ẩn nút); giá trong `goi`, hạn ưu đãi trong `uuDai.denNgay`, % cọc trong `datCocPhanTram`.
2. **Thêm ảnh khách:** chép ảnh vào `images/gallery/`, rồi thêm dòng vào `CONFIG.gallery`, ví dụ `{ src: "images/gallery/pregrad-04.jpg", tag: "pregrad", caption: "Pre-Graduation – Sân trường" }` (tag: `pregrad` hoặc `le`). Ảnh hero sửa ở `CONFIG.heroAnh`.
   **Video tặng kèm:** đăng lên YouTube / Google Drive / TikTok rồi dán link vào `CONFIG.video.link`, hoặc chép file `.mp4` (< 20MB) vào `videos/` và ghi `CONFIG.video.file`. Xem `videos/HUONG-DAN.txt`.
3. **Đưa lên Netlify:** vào app.netlify.com → *Add new site → Deploy manually* → kéo-thả cả thư mục dự án (chứa `index.html` và `images/`). Nếu kết nối Git: build command để trống, publish directory là `.` (đã cấu hình sẵn trong `netlify.toml`).

## Chạy trên máy
Mở trực tiếp `index.html` bằng trình duyệt, hoặc chạy `netlify dev` để có cả Image CDN.

## Cấu trúc
```
index.html          # toàn bộ giao diện + CONFIG + logic
images/logo.png     # logo gốc (ảnh chia sẻ Open Graph)
images/favicon.svg  # favicon máy ảnh vàng
images/gallery/     # ảnh khách thật (hero + ảnh khách)
videos/             # (tùy chọn) file video tặng kèm .mp4
netlify.toml        # publish thư mục gốc, cache ảnh
```
