## 7. User Story: Lender Responds to a Borrowing Request

**As a lender,**  
Tôi muốn xem các bài đăng yêu cầu mượn đồ và phản hồi lại nếu tôi có món đồ phù hợp,  
**So that** tôi có thể cho mượn món đồ của mình và giúp người khác.

---

### Acceptance Criteria

**AC1: Lender can view list of active borrowing requests**  
**Người cho thuê có thể xem danh sách các yêu cầu mượn đồ đang hoạt động**

- **Given**: Người cho thuê đã đăng nhập vào hệ thống
- **When**: Người cho thuê truy cập trang [Yêu cầu mượn đồ]
- **Then**:
  - Hệ thống hiển thị danh sách bài đăng yêu cầu mượn, bao gồm:
    - Tên yêu cầu
    - Danh mục
    - Thời gian mượn/trả dự kiến
    - Địa điểm
    - Mô tả ngắn gọn
  - Có nút [Xem chi tiết] cho từng bài đăng

---

**AC2: Lender can view full request details and propose an item**  
**Người cho thuê có thể xem chi tiết yêu cầu và đề xuất món đồ phù hợp**

- **Given**: Người cho thuê nhấn vào [Xem chi tiết] một bài đăng
- **When**: Trang chi tiết bài đăng được mở
- **Then**:
  - Hiển thị đầy đủ thông tin bài đăng: mô tả, thời gian, hình ảnh mẫu (nếu có), địa điểm nhận/trả
  - Có nút [Đề xuất món đồ]

---

**AC3: Lender can select one of their items to offer in response**  
**Người cho thuê có thể chọn một món đồ mình đã đăng để đề xuất**

- **Given**: Người cho thuê nhấn nút [Đề xuất món đồ]
- **When**: Hệ thống hiển thị popup hoặc trang chọn món đồ
- **Then**:
  - Hiển thị danh sách các món đồ đã được duyệt và sẵn sàng cho thuê của người cho thuê
  - Người cho thuê chọn một món phù hợp (hoặc thêm mô tả bổ sung)
  - Nhấn [Gửi đề xuất]

---

**AC4: System notifies the borrower of new offers**  
**Hệ thống thông báo cho người mượn khi có người đề xuất món đồ**

- **Given**: Người cho thuê đã gửi đề xuất
- **When**: Gửi thành công
- **Then**:
  - Người mượn nhận được thông báo trong hệ thống và qua email/SMS:  
    “Một người cho thuê đã đề xuất món đồ phù hợp với yêu cầu của bạn.”
  - Người mượn có thể nhấn [Xem đề xuất] để mở chi tiết

---

**AC5: Borrower can accept or reject the offer**  
**Người mượn có thể chấp nhận hoặc từ chối món đồ được đề xuất**

- **Given**: Người mượn đã nhận được đề xuất từ người cho thuê
- **When**: Người mượn mở chi tiết đề xuất
- **Then**:
  - Hiển thị thông tin món đồ được đề xuất:
    - Tên món đồ
    - Mô tả, hình ảnh
    - Giá thuê, yêu cầu đặt cọc
    - Hình thức giao nhận
  - Có nút [Chấp nhận đề xuất] hoặc [Từ chối]

---

**AC6: Transaction begins when borrower accepts the offer**  
**Quá trình mượn bắt đầu khi người mượn chấp nhận đề xuất**

- **Given**: Người mượn nhấn [Chấp nhận đề xuất]
- **When**: Xác nhận thành công
- **Then**:
  - Hệ thống tạo một đơn mượn mới liên kết với món đồ được đề xuất
  - Gửi thông báo đến cả hai bên:
    - “Yêu cầu mượn của bạn đã được xác nhận. Hãy chờ người cho thuê giao món đồ.”
  - Hiển thị lịch sử mượn và trạng thái đơn hàng trong [Lịch sử mượn/cho thuê]

---

**AC7: Other lenders are notified if their proposals are not selected**  
**Người cho thuê khác sẽ được thông báo nếu đề xuất của họ không được chọn**

- **Given**: Người mượn đã chọn một món để mượn
- **When**: Có nhiều người cho thuê đề xuất
- **Then**:
  - Các người cho thuê không được chọn sẽ nhận được thông báo:  
    “Rất tiếc, món đồ của bạn không được chọn cho yêu cầu mượn này.”

---

**AC8: Both parties can chat or contact after match is made**  
**Cả hai bên có thể trò chuyện sau khi kết nối thành công**

- **Given**: Đề xuất đã được chấp nhận
- **When**: Người mượn/cho thuê truy cập chi tiết giao dịch
- **Then**:
  - Có tùy chọn mở hộp thoại trò chuyện (chat real-time)
  - Cho phép người dùng trao đổi chi tiết về giao nhận đồ hoặc thời gian
