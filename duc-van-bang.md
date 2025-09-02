# Hướng dẫn tạo và huỷ văn bằng NFT trên hệ thống

## 1. Tạo văn bằng mới (Degree)

### Bước 1: Truy cập hệ thống
- QL ĐHXDHN đăng nhập vào hệ thống bằng ví Solana.
- Sau khi đăng nhập thành công, chọn menu **Quản lý văn bằng**.  
  > 🖼️ *Ảnh minh hoạ: Giao diện trang quản lý văn bằng*

---

### Bước 2: Tạo văn bằng (off-chain)
1. Chọn **Thêm văn bằng mới**.  
2. Nhập đầy đủ thông tin:
   - MSSV, họ tên, ngày sinh.  
   - Ngành, loại văn bằng, xếp loại.  
   - Số hiệu văn bằng, số vào sổ, ngày cấp.  
   - Ảnh văn bằng (file .jpg/.png).  
3. Bấm **Lưu** → Hệ thống lưu dữ liệu vào CSDL.  
   > 🖼️ *Ảnh minh hoạ: Form nhập thông tin văn bằng*

---

### Bước 3: Upload metadata
1. Chọn văn bằng vừa tạo → **Upload metadata**.  
2. Hệ thống đóng gói metadata chuẩn JSON (bao gồm thông tin sinh viên, văn bằng, ảnh).  
3. Metadata được tải lên mạng ngang hàng (IPFS/Arweave/S3).  
4. Hệ thống lưu lại URI vào CSDL.  
   > 🖼️ *Ảnh minh hoạ: Thông báo upload metadata thành công*

---

### Bước 4: Đúc văn bằng NFT (Mint on-chain)
1. Chọn văn bằng đã có metadata URI → **Đúc văn bằng NFT**.  
2. Hệ thống chuẩn bị dữ liệu on-chain:
   - Metadata URI.  
   - Chủ sở hữu (địa chỉ ví sinh viên).  
   - Ví mint (của nhà trường).  
   - Các plugin cần thiết (transfer, revoke…).  
3. Ký và gửi giao dịch lên blockchain Solana.  
4. Chờ xác nhận khối:  
   - ✅ Thành công → Lưu `transaction signature`, cập nhật trạng thái **Đã đúc (VERIFIED)**.  
   - ❌ Thất bại → Hiển thị lỗi (ví dụ: thiếu SOL, URI không hợp lệ).  
   > 🖼️ *Ảnh minh hoạ: Giao diện thông báo đúc văn bằng thành công*

---

## 2. Huỷ văn bằng NFT (Revoke / Burn)

Trong trường hợp văn bằng phát hành bị sai thông tin hoặc không hợp lệ, QL ĐHXDHN có thể tiến hành huỷ NFT.

### Bước 1: Chọn văn bằng cần huỷ
- Vào menu **Quản lý văn bằng**.  
- Lọc theo MSSV hoặc số hiệu văn bằng.  
- Chọn **Huỷ văn bằng**.  
  > 🖼️ *Ảnh minh hoạ: Danh sách văn bằng với nút Huỷ*

---

### Bước 2: Xác nhận huỷ
1. Hệ thống kiểm tra trạng thái văn bằng:
   - Chỉ cho phép huỷ khi trạng thái là **Đã đúc (VERIFIED)**.  
2. Xác nhận yêu cầu huỷ → QL ĐHXDHN ký giao dịch trên ví.  

---

### Bước 3: Gửi giao dịch lên blockchain
- Hệ thống ký và gửi giao dịch huỷ NFT lên Solana.  
- Chờ xác nhận khối:  
  - ✅ Thành công → Trạng thái cập nhật thành **Đã huỷ (REVOKED)**, lưu `transaction signature`.  
  - ❌ Thất bại → Hiển thị lý do lỗi.  
  > 🖼️ *Ảnh minh hoạ: Thông báo huỷ văn bằng thành công*

---

## 3. Lưu ý
- Cần đảm bảo ví mint có đủ **SOL** để trả phí gas.  
- Sau khi huỷ, văn bằng không thể phục hồi → chỉ thực hiện khi chắc chắn.  
- Tất cả hành động đều được ghi lại trong lịch sử giao dịch để minh bạch và kiểm tra sau này.  

