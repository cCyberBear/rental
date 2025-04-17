## 4. User Story: Returning Items

### 4.1. Trả hàng đúng hạn

**As a borrower,**  
Tôi muốn trả lại món đồ đã mượn vào đúng thời gian và địa điểm đã được xác định,  
**So that** tôi không bị phạt và duy trì uy tín trong hệ thống.

#### Acceptance Criteria

**AC1: User receives return reminder before due time**  
**Người dùng nhận được thông báo nhắc nhở trước hạn trả**

- **Given**: Người dùng đang mượn món đồ
- **When**: Còn 24 giờ trước thời gian trả hàng
- **Then**:
  - Gửi thông báo qua app hoặc email: “Bạn còn 1 ngày để trả món [Tên món đồ] tại [Địa điểm].”
  - Thêm tùy chọn: [Xem chỉ đường] / [Liên hệ người cho mượn]

**AC2: User can confirm return when handing over the item**  
**Người dùng có thể xác nhận trả đồ khi giao lại món đồ**

- **Given**: Người mượn đến địa điểm trả hàng
- **When**: Giao lại món đồ
- **Then**:
  - Người mượn nhấn nút [Đã trả đồ]
  - Người cho mượn xác nhận lại bằng nút [Đã nhận lại]
  - Trạng thái món đồ chuyển thành “Đã trả” trong lịch sử

**AC3: Deposit is automatically returned (if applicable)**  
**Tiền đặt cọc được hoàn trả sau khi món đồ được xác nhận trả**

- **Given**: Giao dịch có yêu cầu đặt cọc
- **When**: Người cho mượn xác nhận đã nhận lại đồ và đồ còn nguyên trạng
- **Then**:
  - Hệ thống hoàn trả đặt cọc cho người mượn qua hình thức ban đầu (ví dụ: ví điện tử, chuyển khoản)

---

### 4.2. Trả hàng quá hạn

**As a lender,**  
Tôi muốn nhận được cảnh báo nếu người mượn không trả đúng hạn,  
**So that** tôi có thể xử lý tình huống và đảm bảo quyền lợi của mình.

#### Acceptance Criteria

**AC1: System flags overdue items and sends alerts**  
**Hệ thống gắn cờ quá hạn và gửi cảnh báo**

- **Given**: Món đồ đã quá thời gian trả hàng
- **When**: Quá hạn trả ít nhất 1 giờ
- **Then**:
  - Gửi thông báo đến cả người mượn và người cho mượn: “Món đồ [Tên món đồ] đã quá hạn trả.”
  - Gắn nhãn “Quá hạn” trong lịch sử mượn đồ

**AC2: System applies penalty (if defined)**  
**Hệ thống áp dụng phí phạt nếu có quy định**

- **Given**: Món đồ được cho thuê với điều khoản phạt trễ
- **When**: Người mượn không trả đúng giờ
- **Then**:
  - Tự động tính toán và hiển thị phí phạt (ví dụ: 10% giá thuê mỗi ngày trễ)
  - Cập nhật tổng số tiền phải thanh toán thêm trước khi người mượn được mượn món tiếp theo

**AC3: Lender can report serious late returns**  
**Người cho mượn có thể báo cáo trễ hạn nghiêm trọng**

- **Given**: Người mượn trễ hạn hơn 3 ngày
- **When**: Người cho mượn nhấn [Báo cáo vi phạm]
- **Then**:
  - Hệ thống gửi báo cáo đến quản trị viên để xử lý
  - Có thể hạn chế quyền mượn đồ trong tương lai

---

### 4.3. Phản hồi sau khi trả

**As a borrower and lender,**  
Tôi muốn đánh giá trải nghiệm sau khi hoàn thành giao dịch,  
**So that** hệ thống có thể duy trì chất lượng và độ tin cậy.

#### Acceptance Criteria

**AC1: System prompts feedback after item return**  
**Hệ thống yêu cầu phản hồi sau khi trả đồ**

- **Given**: Giao dịch đã hoàn tất (xác nhận trả)
- **When**: 1 giờ sau khi kết thúc giao dịch
- **Then**:
  - Gửi thông báo đến cả 2 bên: “Hãy đánh giá trải nghiệm của bạn với [Người mượn/người cho thuê]”
  - Giao diện đánh giá 1–5 sao và nhận xét ngắn (tối đa 200 ký tự)

**AC2: Users can view rating history**  
**Người dùng có thể xem lịch sử đánh giá**

- **Given**: Người dùng có ít nhất một giao dịch đã hoàn thành
- **When**: Truy cập trang [Lịch sử giao dịch]
- **Then**:
  - Hiển thị điểm đánh giá của đối tác và nhận xét
  - Có thể báo cáo phản hồi không phù hợp

---
