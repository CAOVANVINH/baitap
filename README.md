# baitap

Trò chơi học tập cho bé (Toán, Tiếng Việt lớp 1–2), chạy hoàn toàn trong `index.html`.

## Lưu trữ & đồng bộ

- Dữ liệu chính được lưu trên **Firebase Realtime Database** (gói Spark – miễn phí, không có ngày hết hạn và không bị tạm dừng vì không hoạt động như Supabase).
- Realtime Database của Firebase tự đẩy thay đổi về mọi thiết bị đang mở app, nên câu hỏi, học sinh, cài đặt, bảng xếp hạng và lịch sử làm bài được đồng bộ gần như tức thì, không cần chờ 15 giây.
- App tự lưu bản sao câu hỏi, học sinh và cài đặt vào `localStorage` của từng thiết bị. Nếu mất mạng, app vẫn chạy bằng dữ liệu đã lưu và hiện băng thông báo màu vàng.
- Kết quả làm bài khi mất mạng được xếp hàng trong `localStorage` và tự gửi lại ngay khi Firebase báo đã kết nối lại.
- Không cần cron job hay keep-alive: Firebase không tạm dừng project vì không có truy cập.

## Cấu hình Firebase

App dùng cấu hình web Firebase đã nhúng trong `index.html` (project `data-chung-a62ee`). Trong **Firebase Console → Realtime Database → Rules**, cần cho phép đọc/ghi ở mức phù hợp. Nếu để rules mặc định (chỉ cho phép người đã đăng nhập), app sẽ hiện băng "Đang dùng dữ liệu đã lưu trên máy" và không đồng bộ được.

Ví dụ rules mở hoàn toàn cho ứng dụng gia đình (không chứa dữ liệu nhạy cảm):

```json
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
```

Sau khi dán rules và bấm **Publish**, mở lại app: dữ liệu mẫu (câu hỏi, học sinh) sẽ tự được tạo ở lần chạy đầu tiên nếu database đang trống.
