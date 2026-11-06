# baitap

Trò chơi học tập cho bé (Toán, Tiếng Việt lớp 1–2), chạy hoàn toàn trong `index.html`.

## Lưu trữ & đồng bộ

- Dữ liệu chính được lưu trên Supabase (gói Free). Gói này không có ngày hết hạn, nhưng project có thể bị tạm dừng sau 7 ngày không có hoạt động; dữ liệu vẫn còn và có thể khôi phục.
- App tự lưu bản sao câu hỏi, học sinh và cài đặt vào `localStorage` của từng thiết bị. Nếu Supabase tạm dừng hoặc mất mạng, app vẫn chạy bằng dữ liệu đã lưu và hiện băng thông báo.
- Kết quả làm bài khi mất mạng được xếp hàng trong `localStorage` và tự gửi lại khi có mạng.
- App tự đồng bộ lại dữ liệu mỗi 15 giây khi đang mở, và ngay khi quay lại tab.
- Mỗi lần mở app (tối đa 6 giờ một lần) sẽ gửi một truy vấn nhỏ để giữ project Supabase hoạt động.
- Workflow `.github/workflows/keep-supabase-awake.yml` gửi thêm một ping mỗi ngày. GitHub chỉ chạy workflow định kỳ trên nhánh mặc định (`main`), nên workflow có hiệu lực sau khi thay đổi này được gộp vào `main`; GitHub cũng tự tắt workflow định kỳ nếu repo không có hoạt động trong 60 ngày. Vì vậy cơ chế giữ project hoạt động chính vẫn là ping tự động mỗi khi có người mở app.
