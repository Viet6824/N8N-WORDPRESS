# <p align="center">PHÁT TRIỂN ỨNG DỤNG VỚI MÃ NGUỒN MỞ (N8N + BOT TELEGRAM TỰ ĐỘNG)</p>

**Môn học:** Phát triển ứng dụng với mã nguồn mở - TEE0421  

**Họ và tên:** Nguyễn Đức Việt

**MSSV:** K225480106075

**Lớp:** K58KTP

**Deadline:** 23h59 ngày 25/05/2026

---
## 1. GIỚI THIỆU

Bài tập này mở rộng từ hệ thống WordPress đã được triển khai từ bài tập trước bằng Docker Compose. Bổ sung thêm service n8n để xây dựng hệ thống tự động đăng bài lên WordPress thông qua Telegram Bot và Google Gemini AI.

Người dùng chỉ cần gửi nội dung qua Telegram Bot, hệ thống sẽ tự động:

- Nhận yêu cầu từ Telegram
- Gửi prompt tới Google Gemini AI
- Sinh nội dung bài viết dạng HTML
- Tự động đăng bài lên WordPress
# 2. CÁC BƯỚC THỰC HIỆN

### Bước 1: Cập nhật docker-compose.yml
#### Sửa file docker-compose thêm service n8n
- Vào thư mục dự án của bài tập 3 `wordpress-project`
- Sửa file `nano docker-compose.yml`
- Thêm service n8n .

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/29936315-3b57-42f4-b68a-c39b69a07673" />

#### Khởi động lại hệ thống
```
docker compose up -d
```
#### Kiểm tra các service
```
docker compose ps
```

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/24ae2364-09d7-4c5f-bb90-ed56985a69be" />


### Bước 2: Cấu hình thêm route trên cloudflare tunnel
- Cấu hình Tunel cloudflare để truy cập vào các dịch vụ bằng các subdomain

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/96a5a688-6824-4184-8a5c-1002dd2ce9b7" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a27029ba-9380-48ce-9780-0dec1f9028bc" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f3d1ae74-af98-418d-b561-9f091088f833" />

### Bước 3: Truy cập subdomain xem kết quả

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/3fb55546-2216-4323-853f-9061515a8996" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/41556ac4-b9d8-4f31-bdc1-05695eaee011" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4584e221-3ec2-4779-9a80-3d639ad761c5" />

### Bước 4: Tạo bài viết trên Wordpress

#### Bước 4.1. Bài viết giới thiệu bản thân

##### Bài viết 1: đã thực hiện ở bài tập 3

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/22e90a3b-e9cf-4f63-88c6-4d8e2b14d537" />

##### Bài viết 2: sử dụng html

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7837e7ba-b04e-4753-89fd-0654e813ca4c" />

#### Bước 4.2. Bài viết giới thiệu những kiến thức đã học được ở môn học Phát triển ứng dụng với mã nguồn mở

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7113df2b-4d46-4d26-b4d3-6bc99f4e0e72" />

### Bước 5: Cấu hình n8n
#### Bước 5.1. Truy cập subdomain `https://n8n.nguyentrunghiieu.id.vn/` để tạo tài khoản và kích hoạt license
##### Điền các thông tin , đặc biệt email cần chính xác -> Next

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/764f61a2-f155-4a0b-85e5-ef91e6490ed2" />

##### Chọn `Send me a free license key`

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/8177bb92-4a36-4991-ba48-eff66c062318" />

##### Trong Usage and plan -> Enter Activation Key -> Nhập Key lấy từ email -> Activate

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/dde2deed-2ca1-475e-b378-b60f86cb9ce8" />

#### Bước 5.2. Tạo workflow
##### Chọn Home page -> Overview -> New workflow

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/652b775c-b576-4956-abed-ba4690eb18a2" />

#### Bước 5.3. Tạo Telegram Bot

Mở Telegram và tìm kiếm `BotFather` có tích xanh chính chủ

#####  Bấm `/start`

##### Nhập lệnh `/newbot`

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5680248b-09e7-4d44-ad5b-57fd70c2d86a" />

##### Đặt tên cho bot `Bot_n8n_wordpress`
##### Đặt usename cho bot, bắt buộc kết thúc bằng `bot` (`viet6824_n8n_bot`)
##### Copy token HTTP API

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6a0794a8-86c8-4d04-ad16-d3689b388770" />

##### Chat với bot mới lần đầu:

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/302bc63f-26cc-4869-870d-51224d42143d" />

#### Bước 5.4. Cấu hình node Telegram trong workflow

##### Add trigger node: tìm node: Telegram -> OnMessage ; cấu hình Credential: Set up Credential -> cần Nhập Access Token

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4c8a96cb-e11a-4689-905d-e23a51485174" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7d7f4577-1721-4108-ac59-a54483f25efc" />

##### Nhấn Test this trigger để kiểm tra, vào Telegram Bot vừa tạo rồi gửi bất kỳ

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c097ec8a-8c6a-4849-9901-8564170f30bb" />

#### Bước 5.5. Cấu hình node AI Google Gemini

##### Add (nối tiếp vào sau node Telegram Trigger) node: Google Gemini => Message a model

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/fa84faf6-be78-40e5-901e-98c70029b32b" />


##### Thực hiện Set up Credential -> Cần nhập Token API Key
- Lấy API KEY tại trang: https://aistudio.google.com => https://aistudio.google.com/api-keys
- Tạo project mới, rồi tạo API KEY

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2dd32216-9560-44e1-9620-cccd01e74137" />

- Nhập API key lên giao diện setup trong n8n rồi nhấn save.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/3e96593e-6c28-4c6f-baeb-ee2c9de31461" />


#### Bước 5.6. Cấu hình node Code in JavaSript

- Add (nối tiếp vào sau node Message a model) node: Code in JavaScript
- Dán code

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b54dfd2d-af4d-4453-8202-e489f9ff5c3b" />

#### Bước 5.7. Cấu hình node WordPress

##### - Add (nối tiếp vào sau node Code in JavaScript) node: WordPress => Create a Post
##### - Lấy "Mật khẩu ứng dụng" (Application Password) từ WordPress
- Truy cập trang quản trị
- Vào `Tài khoản` -> chọn user lúc thiết lập -> Mật khẩu ứng dụng -> Nhập tên `n8n` -> Thêm mật khẩu ứng dụng

#####  Copy mật khẩu rồi dán vào password của n8n credential, điền các thông tin -> save
- Ignore SSL Issues (Insecure): TURN ON

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/98af73cd-7060-4f8f-8ee7-a61050415726" />

##### Mapping dữ liệu
- Kéo thả tiêu đề (Title): Nhìn sang cột dữ liệu bên trái của node JavaScript trước đó, bạn sẽ thấy cột title. Nhấp giữ chuột vào trường title này và kéo thả trực tiếp vào ô nhập liệu Title của node WordPress. (Nó sẽ tự động điền mã biểu thức dạng {{ $json.title }}).
- Kéo thả nội dung (Content): Tương tự, nhấp giữ chuột vào trường content ở cột bên trái và kéo thả vào ô nhập liệu Content của node WordPress. (Nó sẽ tự động điền {{ $json.content }}).
- Cấu hình Trạng thái xuất bản (Status):

Nhấp vào nút Add Field (Thêm thuộc tính) ở cuối cấu hình.
  - Chọn thuộc tính Status.
  - Ở ô giá trị của Status, chọn là Publish

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e216db36-855f-4a7e-839e-f3cc0d9c0f7c" />

## 3. KẾT QUẢ ĐẠT ĐƯỢC
### 3.1. Kết quả demo
#### Chat với tele bot với yêu cầu : `Viết cho tôi một bài viết giới thiệu Hà Nội

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/42abf57c-ad10-4ba2-8d11-f3d33dc7c70d" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9917aa4b-a21c-4aa1-bb13-a043fe7e1cc5" />

### 3.2. Thực hiện yêu cầu mới
#### Chat với bot: `Viết cho tôi một bài viết về các điểm du lịch ở Việt Nam.`

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0d6d9a1f-9b83-4f5c-a80c-337801379a2b" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d942bcd6-ea36-4ea8-9dc4-10859b6d68f6" />

## 4. NHẬN XÉT

### 4.1. Quy trình vận hành hệ thống

Hệ thống hoạt động theo mô hình khép kín tự động hóa hoàn toàn 24/7:

- **Yêu cầu đầu vào:** Người dùng gửi yêu cầu viết bài bằng ngôn ngữ tự nhiên (tiếng Việt) qua Telegram Bot cá nhân.
- **Kích hoạt & Xử lý:** Node Telegram Trigger trên n8n bắt webhook tin nhắn và lập tức chuyển tiếp tới Google Gemini AI.
- **Sinh nội dung:** Gemini AI phân tích ngữ cảnh, tự động viết bài chuẩn định dạng HTML/CSS và đóng gói gọn gàng dưới dạng cấu trúc JSON.
- **Lọc dữ liệu:** Node Code JavaScript chạy script bóc tách, lọc sạch các ký tự markdown thừa và chuẩn hóa hai trường dữ liệu `title` và `content`.
- **Xuất bản:** Node WordPress kết nối qua Application Password bảo mật, tự động tạo và xuất bản bài viết công khai trực tiếp lên website.

### 4.2. Những điều đã đạt được & Kiến thức tích lũy

- **Triển khai hạ tầng Container:** Làm chủ kỹ thuật cấu trúc file `docker-compose.yml` để khởi chạy, phân quyền và liên kết chặt chẽ cụm dịch vụ bao gồm MariaDB, WordPress, phpMyAdmin, n8n và Cloudflared Tunnel trên Ubuntu Server.
- **Tự động hóa & Tích hợp API:** Làm quen và làm chủ trục tự động hóa n8n; biết cách cấu hình Webhook, kết nối và phân quyền giữa các API hiện đại gồm Telegram Bot API, Google Gemini API và WordPress REST API.
- **Xử lý dữ liệu thực chiến:** Ứng dụng thành công JavaScript cơ bản để xử lý chuỗi động, phân tích cú pháp (`JSON.parse`) và lồng mã bắt lỗi ngoại lệ (`try-catch`) giúp dòng chảy dữ liệu không bị nghẽn mạch.

### 4.3. Những vấn đề tồn tại & Hướng phát triển

- **Tính ổn định của AI:** Đôi khi Gemini AI phản hồi kèm văn bản rườm rà ngoài cấu trúc JSON mong muốn (hiện đã được khắc phục bằng thuật toán lọc chuỗi nâng cao và thiết lập tự động thử lại `Retry On Fail` trong n8n).
- **Quản lý tài nguyên phần cứng:** Việc vận hành đồng thời nhiều service tương đối nặng trên môi trường ảo hóa Ubuntu có dung lượng RAM hạn chế cần được tối ưu cấu hình Docker để tránh tràn bộ nhớ đệm (OOM).
- **Hướng phát triển nâng cấp:** Tích hợp thêm các node AI sinh ảnh (như Imagen hoặc DALL-E) vào workflow để tự động tạo ảnh minh họa độc bản dựa theo nội dung bài viết và tự động gán làm ảnh đại diện (`Featured Image`) trên WordPress.

---
