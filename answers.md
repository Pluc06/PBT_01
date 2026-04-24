PHẦN A — KIỂM TRA ĐỌC HIỂU (20 điểm)
Câu A1 (5đ) — HTTP & Browser
Nguồn tham chiếu: File 01_introduction_html_universe.md — Phần 0 (Opening Hook), Phần 2 (Big Picture) và Phần 3 (Core Technical Truth).
1. Khi bạn gõ https://shopee.vn vào trình duyệt và nhấn Enter, hãy liệt kê đúng thứ tự ít nhất 5 bước xảy ra (từ DNS lookup đến render).
    B1: Gửi Request: Khi bạn nhấn Enter, trình duyệt (Client) tạo một HTTP Request (thường là phương thức GET) để yêu cầu nội dung trang web.
    B2: Truyền tải qua mạng: Yêu cầu đi qua router, nhà mạng (ISP), cáp quang biển để đến máy chủ (Server) của Shopee.
    B3: Server phản hồi: Server tìm kiếm tài nguyên (file index.html), sau đó gửi ngược lại một HTTP Response kèm mã trạng thái (ví dụ: 200 OK) và nội dung file.
    B4: Trình duyệt tiếp nhận (Parse): Trình duyệt nhận file và bắt đầu đọc mã HTML từ trên xuống để xây dựng cây cấu trúc DOM (Document Object Model).
    B5: Render giao diện: Trình duyệt kết hợp HTML, CSS và thực thi JavaScript để tính toán vị trí (Layout), vẽ điểm ảnh (Paint) và hiển thị trang Shopee hoàn chỉnh.