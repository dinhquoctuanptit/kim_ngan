# Pink Heart Vision
Trái tim 3D (Three.js) điều khiển bằng cử chỉ tay (MediaPipe Hand Landmarker).

## Cài đặt & chạy
    npm install
    npm run dev        # mở http://localhost:5173 (localhost được phép dùng camera), cho phép camera
Cần Internet lần đầu để tải mô hình MediaPipe (wasm từ jsdelivr, model từ storage.googleapis.com).

## Thêm ảnh
Bỏ PNG/JPG/JPEG/WEBP vào `src/assets/images/` (Vite tự nhận qua `import.meta.glob`; dev server tự reload).

## Ảnh đặc biệt (ngón giữa)
Bỏ ảnh vào `src/assets/special-images/` và sửa `SPECIAL_IMAGE` trong `src/gestures/gestureConfig.js` (mặc định `love.jpg`, không có thì lấy ảnh đầu tiên).

## Cử chỉ
| Cử chỉ | Hiệu ứng |
|---|---|
| Hai tay chụm thành hình tim (ngón cái chạm ngón cái, ngón trỏ chạm ngón trỏ) | LOVE: mưa "I LOVE U" + tim mini, giữ tay để duy trì |
| Xòe 1 bàn tay | Tim bung thành hạt, triệu hồi toàn bộ ảnh (5 ảnh lớn + ảnh nhỏ) |
| Ký hiệu OK (1 tay) | Chọn ảnh đang ở giữa màn hình |
| Hai tay tách ra / lại gần | Phóng to / thu nhỏ ảnh đã chọn |
| Xòe 1 tay khi đang có ảnh chọn | Bỏ ảnh đã chọn, chọn tiếp ảnh khác |
| Nắm tay | Thu hồi ảnh, hạt hút về thành trái tim |
| Chỉ ngón giữa | Ảnh đặc biệt, thả tay để quay lại |

Luân phiên ảnh: ảnh nào đã vào nhóm 5 ảnh lớn thì không quay lại cho tới hết chu kỳ (`src/systems/ImageQueue.js`).
