## 5. User Story: Rating and Feedback System

### 5.1. Đánh giá và phản hồi sau giao dịch

**As a user (borrower/lender),**  
Tôi muốn có thể đánh giá và gửi phản hồi sau mỗi giao dịch,  
**So that** tôi có thể chia sẻ trải nghiệm và giúp cộng đồng đưa ra lựa chọn tốt hơn.

#### Acceptance Criteria

**AC1: Prompt users to rate after transaction completion**  
**Người dùng được yêu cầu đánh giá sau khi hoàn tất giao dịch**

- **Given**: Giao dịch (mượn/trả) đã hoàn tất
- **When**: Trong vòng 1 giờ sau khi cả hai bên xác nhận “Đã nhận/trả đồ”
- **Then**:
  - Hệ thống hiển thị popup hoặc gửi email yêu cầu đánh giá:
    - Thang điểm 1–5 sao
    - Nhận xét tùy chọn (tối đa 200 ký tự)
    - Câu hỏi nhanh: "Bạn có mượn/cho mượn lại với người này không?"

**AC2: Users can view and manage their feedbacks**  
**Người dùng có thể xem và quản lý phản hồi đã gửi và nhận**

- **Given**: Người dùng có các giao dịch đã hoàn tất
- **When**: Truy cập trang [Lịch sử đánh giá] hoặc [Hồ sơ của tôi]
- **Then**:
  - Hệ thống hiển thị:
    - Danh sách các đánh giá đã nhận và gửi
    - Tổng số điểm trung bình
    - Các đánh giá tích cực và tiêu cực

**AC3: One-time editable review**  
**Người dùng có thể chỉnh sửa phản hồi 1 lần duy nhất trong vòng 24h**

- **Given**: Người dùng đã gửi đánh giá
- **When**: Trong vòng 24 giờ
- **Then**:
  - Cho phép sửa nội dung đánh giá đúng 1 lần
  - Ghi chú hiển thị: "Đã chỉnh sửa lần cuối vào [thời gian]"

---

### 5.2. Điểm Uy Tín (Reputation Score)

**As a system,**  
Tôi muốn tính điểm uy tín dựa trên lịch sử mượn/trả, đánh giá và hành vi người dùng,  
**So that** tôi có thể phân loại mức độ đáng tin cậy của người mượn và người cho mượn.

#### Acceptance Criteria

**AC1: Reputation score is automatically calculated**  
**Điểm uy tín được tính toán tự động**

- **Given**: Người dùng có các hoạt động giao dịch trên hệ thống
- **When**: Có các hành vi sau:
  - Hoàn tất giao dịch đúng hạn: +2 điểm
  - Nhận đánh giá 4–5 sao: +1 điểm
  - Trả hàng trễ: –3 điểm
  - Bị báo cáo vi phạm: –5 điểm
  - Không phản hồi giao dịch quá 3 ngày: –2 điểm
- **Then**:
  - Hệ thống cập nhật điểm trên hồ sơ người dùng
  - Thang điểm từ 0 đến 100 (mặc định người mới: 50 điểm)

**AC2: Users can view their reputation badge**  
**Người dùng có thể xem huy hiệu uy tín của mình**

- **Given**: Điểm uy tín được hệ thống ghi nhận
- **When**: Người dùng truy cập hồ sơ
- **Then**:
  - Hiển thị badge tương ứng:
    - ⭐ Mới (0–30)
    - ⭐⭐ Đang cải thiện (31–50)
    - ⭐⭐⭐ Tin cậy (51–70)
    - ⭐⭐⭐⭐ Rất tin cậy (71–90)
    - ⭐⭐⭐⭐⭐ Đáng tin cậy tuyệt đối (91–100)

**AC3: Lenders can set reputation filter for borrowers**  
**Người cho mượn có thể giới hạn người mượn dựa trên điểm uy tín**

- **Given**: Người cho mượn đăng món đồ
- **When**: Thiết lập điều kiện "Chỉ cho mượn với người có điểm uy tín từ X trở lên"
- **Then**:
  - Hệ thống chỉ hiển thị món đồ với người mượn đủ điều kiện
  - Hiển thị thông báo cho người không đủ điểm: "Bạn cần nâng điểm uy tín để mượn món này."

**AC4: System sends warning for low reputation**  
**Hệ thống cảnh báo khi người dùng có điểm uy tín thấp**

- **Given**: Điểm uy tín dưới 30
- **When**: Sau mỗi hành vi tiêu cực
- **Then**:
  - Hệ thống gửi email hoặc thông báo: “Tài khoản của bạn có điểm uy tín thấp, vui lòng cải thiện bằng cách hoàn tất giao dịch đúng hạn và giữ thái độ tích cực.”
  - Nếu điểm tiếp tục giảm, hệ thống có thể giới hạn quyền truy cập.

---

### 5.3. Báo cáo và khiếu nại đánh giá

**As a user,**  
Tôi muốn có thể báo cáo các đánh giá không đúng sự thật hoặc xúc phạm,  
**So that** hệ thống có thể xem xét và xử lý công bằng.

#### Acceptance Criteria

**AC1: Users can report reviews**  
**Người dùng có thể báo cáo đánh giá**

- **Given**: Người dùng nhận một đánh giá
- **When**: Nhấn nút [Báo cáo đánh giá này]
- **Then**:
  - Hiển thị popup chọn lý do (giả mạo, xúc phạm, không đúng sự thật, v.v.)
  - Gửi báo cáo đến quản trị viên để xem xét

**AC2: Admin can moderate reviews**  
**Quản trị viên có thể xử lý các phản hồi bị báo cáo**

- **Given**: Có phản hồi bị báo cáo
- **When**: Truy cập giao diện quản lý đánh giá
- **Then**:
  - Cho phép xóa đánh giá, cảnh cáo người gửi hoặc khôi phục nếu không vi phạm
