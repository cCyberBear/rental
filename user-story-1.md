# User Stories and Acceptance Criteria

---

## 1. User Story: User Registration/Login

**As a user,**  
Tôi muốn đăng ký/đăng nhập bằng cách điền thông tin cá nhân hoặc sử dụng tài khoản Google/Facebook,  
**So that** tôi có thể đăng ký/đăng nhập và sử dụng ứng dụng.

### Acceptance Criteria

**AC1: Users can register/login by filling personal information**  
**Người dùng có thể đăng ký/đăng nhập bằng cách điền thông tin cá nhân**

- **Given**: Người dùng truy cập trang Đăng nhập/Đăng ký
- **When**: Người dùng nhập tên, mật khẩu hợp lệ và xác nhận mật khẩu, sau đó nhấn nút “Đăng ký/Đăng nhập”
- **Then**:
  - Hệ thống sẽ tạo tài khoản mới
  - Hiển thị thông báo thành công
  - Chuyển hướng người dùng đến trang chào mừng

**AC2: Users can register/login by using Google/Facebook account**  
**Người dùng có thể đăng ký/đăng nhập bằng tài khoản Google/Facebook**

- **Given**: Người dùng truy cập trang Đăng nhập/Đăng ký
- **When**: Người dùng nhấn vào biểu tượng Google/Facebook và xác thực thành công với Google/Facebook
- **Then**:
  - Hệ thống tạo tài khoản mới bằng thông tin từ Google/Facebook
  - Chuyển hướng người dùng đến trang chủ

**AC3: Users must fill in detailed information after accessing the system successfully**  
**Người dùng phải điền thông tin chi tiết sau khi truy cập hệ thống thành công**

- **Given**: Người dùng đã đăng nhập và ở trang chủ lần đầu tiên
- **When**:
  - Một popup yêu cầu người dùng điền thông tin cá nhân (ví dụ: số điện thoại, địa chỉ)
  - Người dùng không thể đóng popup cho đến khi cung cấp và gửi thông tin yêu cầu
- **Then**:
  - Popup sẽ đóng sau khi người dùng gửi thông tin thành công
  - Hệ thống cho phép người dùng sử dụng các chức năng của ứng dụng

**AC4: Users must select a role and provide apartment details during registration**  
**Người dùng phải chọn vai trò và cung cấp thông tin căn hộ khi đăng ký**

- **Given**: Người dùng truy cập trang Đăng ký
- **When**: Người dùng nhập thông tin cá nhân và chọn vai trò (Người cho thuê hoặc Người mượn đồ)
- **Then**:
  - Hệ thống yêu cầu người dùng nhập thông tin căn hộ, bao gồm:
    - Số phòng
    - Tòa nhà
  - Người dùng không thể hoàn tất đăng ký nếu không cung cấp thông tin này
  - Hệ thống lưu vai trò và thông tin căn hộ của người dùng

---

## 2. User Story: Tenant Posting Items for Rent

**As a tenant,**  
Tôi muốn đăng các món đồ không còn sử dụng để cho thuê,  
**So that** tôi có thể kiếm thêm thu nhập từ các món đồ không sử dụng thay vì để chúng không dùng đến.

### Acceptance Criteria

**AC1: Tenant can view the posting form with detailed return info**  
**Người thuê có thể xem biểu mẫu đăng bài với thời gian và địa điểm trả hàng**

- **Given**: Người dùng truy cập trang [Đăng món đồ]
- **When**: Trang tải xong
- **Then**: Hệ thống hiển thị biểu mẫu với các trường sau:
  - **Tên món đồ** (Bắt buộc \*)
  - **Danh mục** (Bắt buộc \*)
  - **Mô tả** (Bắt buộc \*)
  - **Giá thuê** (Bắt buộc \*)
  - **Hình thức giao hàng** (Bắt buộc \*)
  - **Tải lên hình ảnh** (Bắt buộc \*)
  - **Thời gian sẵn sàng cho thuê**
  - **Yêu cầu đặt cọc**
  - **Ghi chú khác**
  - **Thời gian trả hàng** (Bắt buộc \*)
  - **Địa điểm trả hàng** (Bắt buộc \*)

#### Validation Rules

| **Field**               | **Validation Rule**                                                                | **Error Message Example**                       |
| ----------------------- | ---------------------------------------------------------------------------------- | ----------------------------------------------- |
| **Tên món đồ**          | Bắt buộc, không để trống, từ 20 đến 50 ký tự                                       | "Tên món đồ là bắt buộc" / "Tối đa 50 ký tự"    |
| **Danh mục**            | Bắt buộc, phải chọn từ danh sách                                                   | "Vui lòng chọn danh mục"                        |
| **Mô tả**               | Bắt buộc, 20–1000 ký tự                                                            | "Mô tả là bắt buộc." / "Quá ngắn" / "Quá dài"   |
| **Giá thuê**            | Bắt buộc, chỉ nhập số, không âm                                                    | "Vui lòng nhập giá thuê hợp lệ"                 |
| **Hình thức giao hàng** | Bắt buộc, chọn ít nhất 1 hình thức                                                 | "Vui lòng chọn hình thức giao hàng"             |
| **Tải lên hình ảnh**    | Bắt buộc: 1–5 ảnh (JPG/PNG/JPEG, <5MB hoặc 10MB), tối đa 2 video (mp4/webm, <50MB) | "Vui lòng tải lên ít nhất một hình ảnh hợp lệ." |
| **Thời gian sẵn sàng**  | Không bắt buộc, nếu có phải hợp lệ và sau ngày hôm nay                             | "Vui lòng chọn ngày/giờ hợp lệ."                |
| **Yêu cầu đặt cọc**     | Không bắt buộc, nếu có phải là số dương                                            | "Đặt cọc phải là số dương."                     |
| **Ghi chú khác**        | Không bắt buộc, tối đa 500 ký tự                                                   | "Ghi chú phải dưới 500 ký tự."                  |
| **Thời gian trả hàng**  | Bắt buộc, phải là ngày hợp lệ sau thời gian thuê                                   | "Vui lòng chọn thời gian trả hàng hợp lệ."      |
| **Địa điểm trả hàng**   | Bắt buộc, không được để trống                                                      | "Vui lòng nhập địa điểm trả hàng."              |

**AC2: Users receive confirmation after submitting item post for review**  
**Người dùng nhận xác nhận sau khi gửi bài đăng để xem xét**

- **Given**: Người dùng đã mở popup [Đăng món đồ]
- **When**: Người dùng nhập thông tin hợp lệ và nhấn nút [Gửi]
- **Then**:
  - Hiển thị thông báo: “Yêu cầu của bạn đang chờ phê duyệt.”

**AC3: Users post item successfully after being approved by the management board**  
**Người dùng đăng món đồ thành công sau khi được ban quản lý phê duyệt**

- **Given**: Người dùng đã gửi biểu mẫu
- **When**:
  - Quản lý phê duyệt bài đăng
- **Then**:
  - Gửi thông báo: “Yêu cầu của bạn đã được chấp nhận” (qua SMS/Gmail)
  - Bài đăng hiển thị trên hệ thống

**AC4: Users can view the post item in the [List Item]/[Home] page**  
**Người dùng có thể xem bài đăng trong trang [Danh sách món đồ]/[Trang chủ]**

---

## 3. User Story: Borrowing Items

**As a user,**  
Tôi muốn tìm kiếm và mượn các món đồ từ những người cho thuê,  
**So that** tôi có thể sử dụng các món đồ mà không cần phải mua chúng.

### Acceptance Criteria

**AC1: Users must register an account before borrowing items**  
**Người dùng phải đăng ký tài khoản trước khi mượn đồ**

- **Given**: Người dùng chưa có tài khoản
- **When**: Truy cập trang [Đăng ký] và hoàn tất thông tin
- **Then**:
  - Hệ thống tạo tài khoản mới
  - Người dùng không thể mượn đồ nếu chưa hoàn tất đăng ký

**AC2: Users can search for items to borrow**  
**Người dùng có thể tìm kiếm các món đồ để mượn**

- **Given**: Đã đăng nhập
- **When**: Nhập từ khóa hoặc chọn bộ lọc
- **Then**:
  - Hiển thị danh sách món đồ phù hợp
  - Người dùng có thể nhấn để xem chi tiết

**AC3: Users can request to borrow an item and confirm the pre-defined return info**  
**Người dùng có thể yêu cầu mượn một món đồ và xác nhận thông tin trả hàng có sẵn**

- **Given**: Đang xem chi tiết món đồ
- **When**:
  - Nhấn [Yêu cầu mượn]
  - Hệ thống hiển thị thời gian và địa điểm trả hàng được xác định bởi người cho thuê
  - Người dùng điền các thông tin còn lại
- **Then**:
  - Gửi yêu cầu mượn thành công
  - Hiển thị thông báo: “Yêu cầu của bạn đã được gửi thành công.”

**AC4: Users receive confirmation after the request is approved**  
**Người dùng nhận xác nhận sau khi yêu cầu được phê duyệt**

- **Given**: Đã gửi yêu cầu
- **When**:
  - Người cho thuê nhấn [Phê duyệt]
- **Then**:
  - Gửi thông báo xác nhận qua SMS/Gmail
  - Hiển thị thông tin chi tiết giao dịch

**AC5: Users can view their borrowing history**  
**Người dùng có thể xem lịch sử mượn đồ**

- **Given**: Đã từng mượn ít nhất 1 món
- **When**: Truy cập trang [Lịch sử mượn đồ]
- **Then**:
  - Hiển thị danh sách món đã mượn với thông tin:
    - Tên món đồ
    - Thời gian mượn
    - Trạng thái (Đang mượn, Đã trả, v.v.)

---
