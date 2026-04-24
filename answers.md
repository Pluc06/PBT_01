PHẦN A — KIỂM TRA ĐỌC HIỂU (20 điểm)
Câu A1 (5đ) — HTTP & Browser
1. Khi gõ https://shopee.vn vào trình duyệt và nhấn Enter, các bước xảy ra sau đó là:
    B1: Gửi Request: Trình duyệt (Client) tạo một HTTP Request (thường là phương thức GET) để yêu cầu nội dung trang web.
    B2: Truyền tải qua mạng: Yêu cầu đi qua router, nhà mạng (ISP), cáp quang biển để đến máy chủ (Server) của Shopee.
    B3: Server phản hồi: Server tìm kiếm tài nguyên (file index.html), sau đó gửi ngược lại một HTTP Response kèm mã trạng thái và nội dung file.
    B4: Trình duyệt tiếp nhận (Parse): Trình duyệt nhận file và bắt đầu đọc mã HTML từ trên xuống để xây dựng cây cấu trúc DOM.
    B5: Render giao diện: Trình duyệt kết hợp HTML, CSS và thực thi JavaScript để tính toán vị trí (Layout), vẽ điểm ảnh (Paint) và hiển thị trang Shopee hoàn chỉnh.
*(Nguồn tham chiếu: File 01_introduction_html_universe.md — Phần 0 (Opening Hook), Phần 2 (Big Picture) và Phần 3 (Core Technical Truth))

2. Tab Network trong Chrome DevTools là công cụ dùng để giám sát tất cả các hoạt động mạng của trang web. Nó hiển thị danh sách mọi tài nguyên (file HTML, CSS, JS, hình ảnh, video, dữ liệu API) mà trình duyệt đã yêu cầu từ server, kèm theo các thông tin chi tiết về: trạng thái phản hồi, kích thước file, loại file và thời gian tải.
(1) Status Code của request đầu tiên
(2) Tổng thời gian load trang
(3) Một request trả về file CSS
![alt text](<Screenshot 2026-04-24 222816.png>)
*(Nguồn tham chiếu: File 01_introduction_html_universe.md — Phần 3 (HTTP — Giao thức giao tiếp), Phần 6 (Hands-on Practice) và Phụ lục.)
Câu A2 (5đ) — Semantic HTML 
*(Nguồn tham chiếu:04_visible_part_html.md - Phần 1 và phần 3)
- Trang web bị đánh giá SEO thấp vì mắc lỗi "Div Soup" (lạm dụng thẻ <div>). Việc sử dụng các thẻ vô nghĩa khiến Google không thể phân biệt được đâu là nội dung chính, đâu là thanh điều hướng, và đâu là các thành phần độc lập của trang.
- Các lỗi semantic(dùng <div>):
    + Lỗi dùng <div class="header"> thay vì <header>
    Lý do chính: Làm mất đi định danh chức năng của phần đầu trang. Trình duyệt và Google không thể xác định đây là khu vực chứa Logo và công cụ tìm kiếm để ưu tiên xử lý.
    + Lỗi dùng <div class="menu"> thay vì <nav>
    Lý do chính: Khiến các công cụ hỗ trợ và Bot tìm kiếm không nhận diện được đây là khu vực điều hướng. Điều này ngăn cản việc thu thập dữ liệu về cấu trúc liên kết của website.
    + Lỗi dùng <div class="main"> thay vì <main>
    Lý do chính: Không xác định được vùng nội dung trọng tâm duy nhất của trang web. Điều này khiến Google khó phân biệt giữa nội dung chính và các thành phần phụ (sidebar, footer).
    + Lỗi dùng <div class="product"> thay vì <article>
    Lí do chính: Vi phạm tính độc lập của nội dung. Thẻ <article> giúp Google hiểu đây là một thực thể sản phẩm hoàn chỉnh, có thể đem đi chia sẻ hoặc nhúng vào trang khác mà vẫn giữ nguyên ý nghĩa.
    + Lỗi dùng <div class="title"> thay vì <h1>
    Lý do chính: Triệt tiêu từ khóa quan trọng nhất của trang web. Google coi thẻ <h1> là tiêu đề chính để xếp hạng nội dung; việc dùng <div> khiến tên sản phẩm "iPhone 16 Pro" bị đối xử như một đoạn văn bản bình thường.
    + Lỗi dùng <div class="footer"> thay vì <footer>
    Lí do chính: Làm mất đi ranh giới kết thúc trang. Việc dùng đúng thẻ <footer> giúp các công cụ tìm kiếm dễ dàng tìm thấy thông tin bản quyền, chính sách và liên hệ để xác minh độ uy tín của website.

- Sửa lại:
<header>
    <div class="logo">ShopTLU</div>
    <nav>
        <ul>
            <li><a href="/">Trang chủ</a></li>
            <li><a href="/products">Sản phẩm</a></li>
        </ul>
    </nav>
</header>

<main>
    <article class="product">
        <h1>iPhone 16 Pro</h1> <p class="price">25.990.000đ</p>
        
        <figure class="image">
            <img src="iphone.jpg" alt="iPhone 15 Pro Max màu Titan" loading="lazy">
        </figure>
    </article>
</main>

<footer>© 2026 ShopTLU</footer>

Câu A3 (5đ) — Block vs Inline
Trình duyệt sẽ render đoạn mã như sau:
Hộp 1
Text AText B
Hộp 2
Text CText D
Hộp 3

2. Giải thích:
    - <div>Hộp 1</div>: Thẻ <div> là phần tử Block. Trình duyệt đặt nó trên một dòng riêng biệt. Sau khi kết thúc thẻ, dòng tiếp theo sẽ bị cưỡng bức xuống dưới.
    - <span>Text A</span>: Thẻ <span> là phần tử Inline. Nó bắt đầu trên dòng mới (vì div trước đó đã chiếm hết dòng), nhưng nó chỉ chiếm không gian vừa đủ cho chữ "Text A".
    - <span>Text B</span>: Vì cũng là thẻ Inline, nó sẽ "nhảy" lên đứng cùng dòng với "Text A" ngay lập tức. Vì trong mã nguồn bạn viết không có khoảng trắng giữa hai thẻ </span><span>, chúng sẽ dính sát vào nhau: Text AText B.
    - <div>Hộp 2</div>: Đây là thẻ Block. Nó không chấp nhận đứng chung dòng với bất kỳ ai, nên nó tự nhảy xuống dòng tiếp theo và chiếm trọn một hàng cho chữ "Hộp 2".
    - <span>Text C</span>: Là thẻ Inline, nó bắt đầu ở dòng mới (ngay dưới Hộp 2).
    - <strong>Text D</strong>: Thẻ <strong> cũng là phần tử Inline. Nó tiếp tục nằm trên cùng một dòng với "Text C".
    - <div>Hộp 3</div>: Là thẻ Block, nó đẩy "Text C" và "Text D" lên trên và tự chiếm một dòng cuối cùng.

Câu A4 (5đ) — Table
- Đây là ba thẻ dùng để phân nhóm ngữ nghĩa cho các hàng trong một bảng, giúp trình duyệt và các công cụ hỗ trợ hiểu rõ vai trò của từng phần dữ liệu.
    + thead> (Table Header): Chứa các hàng tiêu đề của cột.
    + <tbody> (Table Body): Chứa nội dung dữ liệu chính của bảng.
    + <tfoot> (Table Footer): Chứa phần tổng kết hoặc ghi chú cuối bảng.
- Việc dùng <table> để chia bố cục trang web (ví dụ chia cột trái, cột phải) là một sai lầm nghiêm trọng (Anti-pattern). Thay vào đó, lập trình viên hiện đại phải dùng CSS Grid hoặc Flexbox.
- Lý do (Trích xuất ít nhất 3 lý do từ tài liệu):
    + Sai lệch về mặt Ngữ nghĩa (Semantics): <table> chỉ dành cho dữ liệu tabular (dữ liệu có hàng và cột có ý nghĩa). Dùng nó cho layout khiến Google Bot không hiểu được cấu trúc nội dung trang web.
    + Gây khó khăn cho khả năng tiếp cận (Accessibility): Các thiết bị đọc màn hình (Screen Reader) sẽ đọc bảng theo thứ tự ô, khiến người khiếm thị bị rối loạn khi nghe nội dung trang web được bố trí bằng bảng.
    + Hành vi hiển thị không mong muốn: Các thẻ trong bảng có những đặc tính hiển thị riêng (như tự động co giãn) khiến việc kiểm soát giao diện trên các thiết bị khác nhau (Responsive) trở nên cực kỳ khó khăn so với dùng CSS.

PHẦN C — SUY LUẬN (20 điểm)

Câu C1 (10đ) — Thiết kế cấu trúc
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <title>Chi tiết sản phẩm | ShopPL</title>
</head>
<body>

    <header>
        <div class="logo">ShopPL</div>
        <nav aria-label="Menu chính"> <ul> <li><a href="/">Trang chủ</a></li>
                <li><a href="/products">Sản phẩm</a></li>
            </ul>
        </nav>
    </header>

    <nav aria-label="breadcrumb"> <ol> <li><a href="/">Trang chủ</a></li>
            <li><a href="/mobile">Điện thoại</a></li>
            <li aria-current="page">iPhone 16</li> </ol>
    </nav>

    <main>
        <article class="product-details">
            
            <section class="product-gallery"> <figure> <img src="img1.jpg" alt="iPhone 16 mặt trước" loading="eager"> <figcaption>Ảnh mặt trước sản phẩm</figcaption>
                </figure>
                <img src="img2.jpg" alt="iPhone 16 mặt sau" loading="lazy">
                <img src="img3.jpg" alt="iPhone 16 cạnh bên" loading="lazy">
                <img src="img4.jpg" alt="iPhone 16 cụm camera" loading="lazy">
                <img src="img5.jpg" alt="iPhone 16 hộp đựng" loading="lazy">
            </section>

            <section class="product-info">
                <h1>Tên sản phẩm</h1> <p class="rating">⭐⭐⭐⭐⭐ (4.5/5)</p> <p class="price">
                    <del>30.000.000đ</del> <ins>25.000.000đ</ins> </p>
                <div class="description">
                    <h2>Mô tả sản phẩm</h2> <p>Nội dung mô tả chi tiết...</p>
                </div>
            </section>

            <section class="specs">
                <h2>Thông số kỹ thuật</h2>
                <table> <thead> <tr>
                            <th>Tính năng</th>
                            <th>Chi tiết</th>
                        </tr>
                    </thead>
                    <tbody> <tr>
                            <td>Màn hình</td>
                            <td>6.1 inch</td>
                        </tr>
                        <tr>
                            <td>Chipset</td>
                            <td>A18 Bionic</td>
                        </tr>
                    </tbody>
                </table>
            </section>

            <section class="reviews">
                <h2>Đánh giá từ khách hàng</h2>
                <article class="comment"> <header>
                        <strong>Nguyễn Văn A</strong> <time datetime="2026-04-24">24/04/2026</time> </header>
                    <blockquote>"Sản phẩm rất tốt!"</blockquote> </article>
            </section>
        </article>

        <aside class="related-products"> <h2>Sản phẩm tương tự</h2>
            <ul>
                <li><a href="/iphone-15">iPhone 15</a></li>
                <li><a href="/samsung-s24">Samsung S24</a></li>
            </ul>
        </aside>
    </main>

    <footer>
        <p>&copy; 2026 ShopTLU. All rights reserved.</p>
        <address> Địa chỉ: 175 Tây Sơn, Đống Đa, Hà Nội
        </address>
    </footer>

</body>
</html>

Câu C2 (10đ) — So sánh & Tranh luận
Quan điểm "dùng <div> cho mọi thứ" thực chất là một sai lầm kỹ thuật nghiêm trọng, thường được gọi là "Div-itis". Mặc dù thêm class giúp chúng ta định dạng giao diện, nhưng nó hoàn toàn thất bại trong việc giao tiếp với các hệ thống máy tính.Về mặt kỹ thuật, lý do đầu tiên là SEO (Tối ưu hóa tìm kiếm). Google Bot không ưu tiên đọc tên class (vốn mang tính cá nhân của lập trình viên), nó dựa vào các thẻ như <main>, <article>, <h1> để lập chỉ mục. Nếu chỉ dùng <div>, thuật toán sẽ coi trang web là một khối văn bản phẳng, khiến sản phẩm của bạn bị đẩy xuống dưới trên bảng xếp hạng tìm kiếm. Lý do thứ hai là Accessibility (Khả năng tiếp cận). Những người khiếm thị sử dụng Screen Reader dựa vào các thẻ như <nav> hoặc <button> để hiểu cấu trúc trang. Một trang web toàn <div> đối với họ giống như một cuốn sách không có mục lục và tiêu đề, khiến họ không thể điều hướng.Một ví dụ cụ thể: Trên trang sản phẩm, nếu dùng <div class="price-new">25tr</div>, Google chỉ thấy một con số. Nhưng nếu dùng thẻ <ins>25.000.000đ</ins>, trình duyệt và công cụ tìm kiếm hiểu ngay đây là "giá mới sau khi giảm". Điều này giúp hiển thị các thông tin khuyến mãi ngay trên kết quả tìm kiếm (Rich Snippets), giúp tăng tỷ lệ click của khách hàng.Tuy nhiên, <div> không hề bị "khai tử". Nó vẫn là lựa chọn phù hợp nhất trong trường hợp cần các container trung tính để phục vụ mục đích dàn trang (layout) hoặc bọc các phần tử để áp dụng CSS (như Flexbox/Grid) mà bản thân khối đó không mang ý nghĩa nội dung cụ thể nào.Việc học thêm hơn 20 thẻ Semantic không tốn thời gian bằng việc phải đi sửa lỗi SEO hay lỗi hiển thị trên các thiết bị hỗ trợ sau này. Đó là sự khác biệt giữa một thợ gõ code và một Web Developer chuyên nghiệp.