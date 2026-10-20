# NHẬT KÝ PROMPT ENGINEERING (VIBE CODING LOG)
- **Họ và tên:** Đỗ Minh Quân
- **MSSV:** 125002532
- **Tên đề tài Website:** QUANDO Nihongo - Website Học Tiếng Nhật Căn Bản Nhập Môn
- **Công cụ AI đã sử dụng:** ChatGPT / Antigravity AI Assistant


## 1. Yêu cầu ban đầu (System/Initial Prompt)
> Tôi đang làm bài kiểm tra giữa kỳ môn Thiết kế Web theo phong cách Vibe Coding. Hãy đóng vai một Chuyên gia Front-End Developer chuyên nghiệp để giúp tôi viết toàn bộ mã nguồn cho website.
Chủ đề Website: Website học tiếng Nhật cơ bản cho người mới bắt đầu (Nhật ngữ Nhập môn).
Yêu cầu KỸ THUẬT BẮT BUỘC (Tuân thủ đề bài):
1. Chuẩn Semantic HTML5: Bắt buộc sử dụng đúng các thẻ ngữ nghĩa: <header>, <nav>, <main>, <section> (hoặc <article>), và <footer>. Tuyệt đối không lạm dụng thẻ <div> vô nghĩa.
2. CSS & CSS Variables (:root):
   - Quản lý bảng màu thống nhất:
     + Primary: Hồng hoa anh đào nhẹ nhàng (#FFB7C5 hoặc tương tự)
     + Accent/Secondary: Đỏ Nhật Bản (#E60012) làm điểm nhấn nút bấm/logo
     + Background/Text: Trắng chủ đạo (#FFFFFF), xám nhẹ làm nền, chữ tối màu dễ đọc.
   - Bố cục: Sử dụng CSS Flexbox và CSS Grid hiện đại, có tính Responsive cơ bản.
3. Hiệu ứng & Thư viện (KHÔNG DÙNG JAVASCRIPT):
   - Nhúng CDN Animate.css cho Hero Section & Title.
   - Nhúng CDN AOS (Animate On Scroll) cho các khối nội dung khi cuộn trang.
   - Viết hiệu ứng CSS thuần cho nút bấm, liên kết (:hover, :focus, transition).

NỘI DUNG VÀ TƯƠNG TÁC CỤ THỂ TRÊN TRANG (Tự động hóa bằng CSS thuần):
1. Section 1: Hero Section & Lời chào + Ảnh minh họa (Hero banner).
2. Section 2: Bảng chữ cái Hiragana & Katakana
   - Dùng kỹ thuật Tab chuyển đổi bằng CSS thuần (Input Radio + Label) để người dùng chọn xem "Bảng Hiragana" hoặc "Bảng Katakana" mà không cần JS.
   - Bảng chữ cái thiết kế dạng Grid xinh xắn, hiển thị rõ Chữ Hán/Kana + Romaji bên dưới.
3. Section 3: 30 Từ vựng Flashcard cơ bản (Flip Card CSS 3D Effect)
   - Thiết kế dạng lưới (Grid) hiển thị danh sách Flashcard từ vựng.
   - Chia thành các nhóm chủ đề cơ bản (Chào hỏi, Số đếm, Đồ ăn, Con người...).
   - Hiệu ứng Lật Thẻ (CSS Flip Card): Mặt trước hiển thị Chữ Nhật (Kana/Kanji), khi rê chuột (:hover) hoặc chạm vào thì thẻ tự lật 180 độ sang mặt sau hiện phiên âm Romaji + Nghĩa tiếng Việt.
4. Quản lý tài nguyên hình ảnh:
   - Mọi hình ảnh trỏ đường dẫn về thư mục local: "assets/images/tên_ảnh.png" (Ví dụ: assets/images/logo.png, assets/images/hero-bg.jpg,...).
   - Thêm comment gợi ý vị trí chèn ảnh để tôi dễ tự bổ sung sau.

Hãy viết cho tôi 2 file mã nguồn hoàn chỉnh, sạch đẹp và đúng chuẩn UI/UX:
1. index.html
2. style.css  

---

## 2. Quá trình tinh chỉnh & Giải quyết sự cố (Iteration Iterations)

### Lần 1: Dựng khung Semantic HTML5 & Quản lý Màu sắc với CSS Variables
- **Prompt đã dùng:** 
  "Hãy phân tích đề bài và viết cấu trúc Semantic HTML5 chuẩn xác nhất. Phân định rõ ràng các khu vực: <header> chứa logo QUANDO và navigation; <main> chứa các <section>; từng thẻ flashcard và mẹo học bọc trong thẻ <article>. Khai báo bảng màu hoa anh đào và đỏ Hinomaru trong :root."
- **Kết quả AI tạo ra:** 
  AI đã sinh ra khung HTML5 sạch sẽ, chuẩn ngữ nghĩa, hệ thống biến CSS `:root` đầy đủ, bố cục Grid 5 cột cho bảng chữ cái và Flexbox cho thanh điều hướng.
- **Nhận xét & Tinh chỉnh của SV (Đỗ Minh Quân):** 
  Ban đầu AI dùng nhiều thẻ `<div>` để bọc các khối card. Tôi đã yêu cầu AI thay thế toàn bộ bằng thẻ ngữ nghĩa `<article class="flip-card">` và `<article class="culture-card">` để tối ưu điểm tiêu chí Semantic HTML5 (2.0/2.0 điểm).

### Lần 2: Tích hợp Thư viện Animate.css & AOS (Animate On Scroll)
- **Prompt đã dùng:** 
  "Nhúng thư viện Animate.css và AOS qua CDN. Gắn class animation cho tiêu đề Hero, nút CTA và thêm thuộc tính `data-aos='fade-up'` cho các section khi cuộn trang. Chú ý hiệu ứng phải mượt mà, không lạm dụng gây rối mắt."
- **Thách thức gặp phải:** 
  Sau khi nhúng AOS CSS, khi cuộn trang các khối nội dung chưa kích hoạt chuyển động vì thư viện AOS đòi hỏi phải gọi hàm khởi tạo `AOS.init()`.
- **Cách sửa prompt (Debug prompt):** 
  "Thư viện AOS cần một dòng script kích hoạt `AOS.init()` từ CDN của thư viện. Hãy bổ sung dòng nạp script AOS cuối thẻ <body> để kích hoạt hiệu ứng cuộn mượt mà mà vẫn đảm bảo toàn bộ logic tương tác của trang web (tab, lật thẻ) là CSS thuần."

### Lần 3: Tối ưu 3D Flip Card & Tab Chuyển Đổi Bằng CSS Thuần
- **Prompt đã dùng:** 
  "Làm thế nào để chuyển đổi qua lại giữa bảng Hiragana và Katakana, đồng thời lật 30 Flashcard xem phiên âm Romaji và nghĩa tiếng Việt mà không cần viết bất kỳ dòng mã JavaScript nào?"
- **Kết quả AI tạo ra:** 
  - Kỹ thuật Tab: Ẩn các `<input type="radio">`, dùng `<label for="...">` làm nút bấm. Khi radio `:checked`, dùng bộ chọn CSS Sibling `~` để hiển thị đúng khối `.tab-content` tương ứng.
  - Kỹ thuật 3D Flip: Sử dụng `perspective: 1000px`, `transform-style: preserve-3d` và `transform: rotateY(180deg)` khi `:hover` hoặc `:focus-within`.
- **Nhận xét & Tinh chỉnh của SV (Đỗ Minh Quân):** 
  Trên thiết bị cảm ứng (Mobile), hiệu ứng `:hover` không tự kích hoạt được. Tôi đã yêu cầu AI thêm thuộc tính `tabindex="0"` vào thẻ `<article>` cùng bộ chọn `:focus-within` để người dùng chạm (tap) trên điện thoại là thẻ lật 3D ngay lập tức.

### Lần 4: Đồng bộ Thương hiệu QUANDO & Tăng cường Hệ thống Hình ảnh Trực quan
- **Prompt đã dùng:** 
  "Đổi toàn bộ nhận diện thương hiệu trên website thành QUANDO (QUANDO Nihongo). Đồng thời trang đang thiếu hình ảnh, hãy bổ sung thêm các vị trí ảnh minh họa: Banner bảng chữ cái, thumbnail cho từng nhóm chủ đề Flashcard, Gallery văn hóa Nhật Bản và thumbnail các bước lộ trình học tập; tất cả trỏ về 'assets/images/' kèm fallback."
- **Kết quả AI tạo ra:** 
  AI đã hoàn thiện nhận diện thương hiệu QUANDO trên toàn trang, bổ sung khối Gallery văn hóa Nhật Bản (Núi Phú Sĩ, Cố đô Kyoto, Tokyo) và 14 vị trí hình ảnh minh họa sống động, có cơ chế CSS fallback tự động để không bao giờ bị lỗi ảnh.

---

## 3. Đánh giá cá nhân về quá trình Vibe Coding
- **AI đã giúp bạn tiết kiệm thời gian ở phần nào nhất?**
  AI giúp tôi tiết kiệm hơn 80% thời gian khi soạn thảo dữ liệu 30 thẻ từ vựng tiếng Nhật với đầy đủ chữ Hán, Kana, Romaji và giải nghĩa tiếng Việt; đồng thời xuất trọn vẹn 46 ký tự Hiragana và Katakana theo đúng bảng ngũ âm Gojūon vào hệ thống CSS Grid mà không cần nhập liệu thủ công từng chữ.
- **Bài học rút ra khi đặt câu hỏi (Prompt) cho AI trong thiết kế web?**
  1. Cần đưa ra yêu cầu kỹ thuật chi tiết, có cấu trúc rõ ràng ngay từ đầu (các thẻ Semantic cần có, mã màu cụ thể, thư viện yêu cầu) để AI lập trình bám sát đề thi.
  2. Vibe Coding đòi hỏi người học phải nắm chắc kiến thức nền tảng để làm chủ và định hướng cho AI: Nhận diện kịp thời những chỗ AI dùng sai thẻ (như lạm dụng `<div>`), biết cách debug khi thư viện bên ngoài không hoạt động (như bổ sung `AOS.init()`), từ đó đưa ra các prompt lặp (Iteration) chuẩn xác để tạo ra sản phẩm chất lượng cao nhất.