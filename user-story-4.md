## 6. User Story: Post a Borrowing Request

**As a borrower,**  
Tôi muốn đăng bài yêu cầu mượn đồ,  
**So that** tôi có thể tìm được các món đồ phù hợp để mượn từ những người cho thuê.

### Acceptance Criteria

**AC1: User can view the borrowing request form**  
**Người dùng có thể xem biểu mẫu đăng bài mượn đồ**

- **Given**: Người dùng đã đăng nhập vào hệ thống với vai trò Người mượn đồ
- **When**: Người dùng truy cập trang [Đăng bài mượn đồ]
- **Then**:
  - Hệ thống hiển thị biểu mẫu với các trường thông tin cần thiết:
    - **Tên yêu cầu mượn đồ** (Bắt buộc \*): Tên mô tả ngắn gọn mục đồ cần mượn
    - **Danh mục** (Bắt buộc \*): Lựa chọn loại món đồ cần mượn từ danh sách (ví dụ: điện tử, nội thất, dụng cụ thể thao, …)
    - **Mô tả chi tiết** (Bắt buộc \*): Mô tả yêu cầu mượn, lý do và cách sử dụng (20–1000 ký tự)
    - **Thời gian bắt đầu mượn** (Bắt buộc \*): Thời gian dự kiến nhận đồ
    - **Thời gian trả dự kiến** (Bắt buộc \*): Thời gian hẹn trả đồ, phải sau thời gian bắt đầu
    - **Địa điểm nhận đồ** (Bắt buộc \*): Địa điểm cụ thể khi nhận đồ từ người cho thuê
    - **Địa điểm trả đồ** (Bắt buộc \*): Địa điểm dự kiến trả đồ (nếu khác với địa điểm nhận)
    - **Hình thức giao nhận** (Bắt buộc \*): Ví dụ: Giao hàng, Nhận trực tiếp (đảm bảo chọn ít nhất 1 tùy chọn)
    - **Yêu cầu đặt cọc (nếu có)**: Tùy chọn nhập số tiền đặt cọc dự kiến (số dương)
    - **Tải lên hình ảnh/Mô tả mẫu đồ** (Tùy chọn): Hình ảnh tham khảo về món đồ cần mượn, giúp người cho thuê đánh giá yêu cầu (1–3 ảnh, định dạng JPG/PNG)

#### Validation Rules for Borrow Request Form

| **Field**                     | **Validation Rule**                                                    | **Error Message Example**                                           |
| ----------------------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **Tên yêu cầu mượn đồ**       | Bắt buộc, không trống, giới hạn 20–100 ký tự                           | "Tên yêu cầu là bắt buộc" / "Tên yêu cầu phải từ 20 đến 100 ký tự." |
| **Danh mục**                  | Bắt buộc, phải chọn từ danh sách có sẵn                                | "Vui lòng chọn danh mục."                                           |
| **Mô tả chi tiết**            | Bắt buộc, từ 20 đến 1000 ký tự                                         | "Mô tả là bắt buộc và phải từ 20 ký tự trở lên."                    |
| **Thời gian bắt đầu mượn**    | Bắt buộc, phải là thời gian hợp lệ và không quá khứ                    | "Vui lòng chọn thời gian bắt đầu hợp lệ."                           |
| **Thời gian trả dự kiến**     | Bắt buộc, phải sau thời gian bắt đầu mượn                              | "Thời gian trả dự kiến phải sau thời gian bắt đầu mượn."            |
| **Địa điểm nhận đồ & trả đồ** | Bắt buộc, không để trống                                               | "Vui lòng nhập địa điểm."                                           |
| **Hình thức giao nhận**       | Bắt buộc, phải chọn ít nhất 1 tùy chọn                                 | "Vui lòng chọn hình thức giao nhận."                                |
| **Yêu cầu đặt cọc**           | Nếu có, phải là số dương                                               | "Đặt cọc phải là số dương."                                         |
| **Hình ảnh/Mô tả mẫu đồ**     | Nếu tải lên, số lượng tối đa 3 ảnh, định dạng JPG/PNG, kích thước <5MB | "Hãy tải lên ảnh hợp lệ (định dạng JPG/PNG, <5MB)."                 |

---

**AC2: User receives confirmation after submitting the borrow request**  
**Người dùng nhận được xác nhận sau khi gửi bài đăng yêu cầu mượn đồ**

- **Given**: Người dùng đã điền đầy đủ thông tin hợp lệ trong biểu mẫu
- **When**: Nhấn nút [Gửi yêu cầu mượn]
- **Then**:
  - Hệ thống lưu bài đăng yêu cầu mượn và hiển thị thông báo: “Yêu cầu mượn của bạn đã được gửi và đang chờ phê duyệt.”
  - Người dùng nhận được email/SMS thông báo xác nhận gửi bài thành công.

---

**AC3: Admin/Management Board reviews the borrow request**  
**Ban quản trị/Người cho thuê có thể xem và phê duyệt bài đăng yêu cầu mượn đồ**

- **Given**: Bài đăng yêu cầu mượn được gửi đi
- **When**:
  - Ban quản trị hoặc người cho thuê (tùy theo cơ chế duyệt của hệ thống) xem xét bài đăng
  - Nhấn nút [Phê duyệt] hoặc [Từ chối]
- **Then**:
  - Nếu được phê duyệt, bài đăng hiển thị trên mục "Yêu cầu mượn đồ" trên hệ thống.
  - Nếu bị từ chối, hệ thống gửi thông báo với lý do từ chối để người mượn có thể chỉnh sửa hoặc gửi lại.

---

**AC4: User can edit or cancel the borrow request before approval**  
**Người dùng có thể chỉnh sửa hoặc hủy bài đăng yêu cầu mượn trước khi được phê duyệt**

- **Given**: Bài đăng yêu cầu mượn chưa được phê duyệt
- **When**: Người dùng vào trang quản lý bài đăng của mình
- **Then**:
  - Có các lựa chọn: [Chỉnh sửa] hoặc [Hủy yêu cầu]
  - Sau khi chỉnh sửa, người dùng có thể gửi lại để phê duyệt

---

**AC5: Borrowing request is displayed with key information for potential lenders**  
**Bài đăng yêu cầu mượn hiển thị các thông tin chính để người cho thuê dễ dàng đánh giá**

- **Given**: Bài đăng yêu cầu mượn đã được phê duyệt
- **When**: Người cho thuê truy cập trang [Danh sách yêu cầu mượn đồ]
- **Then**:
  - Hiển thị các thông tin nổi bật bao gồm:
    - Tên yêu cầu mượn đồ
    - Danh mục
    - Mô tả ngắn gọn
    - Thời gian bắt đầu và trả dự kiến
    - Địa điểm nhận và trả đồ
    - Hình ảnh (nếu có)
  - Cho phép người cho thuê nhấn vào bài đăng để xem chi tiết và liên hệ trực tiếp với người mượn.
