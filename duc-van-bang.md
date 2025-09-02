# Hướng dẫn tạo và huỷ văn bằng NFT trên hệ thống

## 1. Tạo văn bằng mới (Mint)

### Bước 1: Truy cập hệ thống
- QL ĐHXDHN đăng nhập vào hệ thống bằng ví Solana của QL ĐHXDHN.
- Sau khi đăng nhập thành công, chọn **Dashboard** ở nút kết nối ví.
<img width="1710" height="1112" alt="image" src="https://github.com/user-attachments/assets/d41737d9-a1fc-4239-8336-836eb55d203c" />

- Chọn **Quản lý văn bằng** ở navbar.
<img width="1710" height="1112" alt="image" src="https://github.com/user-attachments/assets/0dd90335-e2d3-4782-947c-864a474bf2ea" />

---

### Bước 2: Tạo văn bằng
- Chọn **Thêm văn bằng**.
- Nhập Mã sinh viên vào và nhấn biểu tượng tìm kiếm, các thông tin khác sẽ tự động được điền đầy đủ.
- Điền & Chọn đầy đủ các thông tin chưa có cho khớp với văn bằng.
- Tải lên ảnh văn bằng.
- Bấm **Tạo văn bằng** → Hệ thống lưu dữ liệu vào CSDL.  
<img width="3420" height="5000" alt="image" src="https://github.com/user-attachments/assets/3cd71ae5-7c13-4279-ad3b-57e33de838b4" />

---

### Bước 3: Upload metadata
- Chọn văn bằng vừa tạo → **Tải lên metadata**.  
- Hệ thống đóng gói metadata chuẩn JSON
```
{
  "name": "Engineer-ArtificialIntelligence-HOANG LAI",
  "image": "https://s3.ap-southeast-1.amazonaws.com/lainhathoang.bucket/degree/degree-1756484959.jpg",
  "full_name": "HOANG LAI",
  "major": "Artificial Intelligence",
  "degree_type": "Engineer",
  "classification": "Good",
  "university_name": "National University of Civil Engineering",
  "degree_number": "XD001",
  "issued_date": "2025-08-28"
}
```
- Metadata được tải lên mạng ngang hàng (IPFS/Arweave/S3).  
- Hệ thống lưu lại URI của metadata vào CSDL.
- Văn bằng được chuyển sang trạng thái **Chờ đúc**  
<img width="1710" height="1112" alt="image" src="https://github.com/user-attachments/assets/fad9ea2d-fe32-4cd4-871c-0c45d00c3027" />
<img width="1710" height="1112" alt="image" src="https://github.com/user-attachments/assets/b1717a1b-39ce-46f8-a501-b266f2ffa854" />


---

### Bước 4: Đúc văn bằng NFT (Mint NFT on-chain)
1. Chọn phần **Thao tác** của một văn bằng đang ở trạng thái **Chờ đúc** → **Đúc văn bằng**.  
2. Hệ thống chuẩn bị dữ liệu on-chain:
   - Metadata URI.  
   - Chủ sở hữu (địa chỉ ví sinh viên).  
   - Ví mint (của nhà trường).  
   - Các plugin cần thiết cho NFT văn bằng (transfer, revoke…).  
3. Ký và gửi giao dịch lên blockchain Solana.  
4. Chờ xác nhận khối:  
   - ✅ Thành công → Lưu `transaction signature`, cập nhật trạng thái **Đã đúc**, và gán cho văn bằng NFT 1 địa chỉ riêng trên toàn mạng lưới.  
   - ❌ Thất bại → Hiển thị lỗi (ví dụ: thiếu SOL, URI không hợp lệ).
<img width="1710" height="1112" alt="image" src="https://github.com/user-attachments/assets/5b0bfe41-03f9-4fbd-9854-511da020142c" />
<img width="1710" height="1112" alt="image" src="https://github.com/user-attachments/assets/372b57f5-dfce-4250-a6b6-1f846426c611" />


---

## 2. Huỷ văn bằng NFT (Revoke / Burn)

Trong trường hợp văn bằng phát hành bị sai thông tin, không hợp lệ. QL ĐHXDHN có thể tiến hành huỷ NFT.

### Bước 1: Chọn văn bằng cần huỷ
- Vào mục **Quản lý văn bằng**.  
- Lọc theo MSSV hoặc số hiệu văn bằng để tìm văn bằng cần huỷ.  
- Chọn **Huỷ bỏ văn bằng**.  
<img width="1710" height="1112" alt="image" src="https://github.com/user-attachments/assets/2e26aaf3-31ae-448c-a067-f33184023996" />


---

### Bước 2: Hệ thống xác nhận huỷ
- Hệ thống kiểm tra trạng thái văn bằng:
   - Kiểm tra xem đúng người thực thi là QL ĐHXDHN (hoặc Admin) không.    
   - Chỉ cho phép huỷ khi trạng thái là **Đã đúc**.  
- Xác nhận yêu cầu huỷ → QL ĐHXDHN ký giao dịch trên ví.
<img width="1710" height="1112" alt="image" src="https://github.com/user-attachments/assets/fc513d44-0219-456a-bece-b2ba24d1d680" />


---

### Bước 3: Gửi giao dịch lên blockchain
- Hệ thống ký và gửi giao dịch huỷ NFT lên Solana.  
- Chờ xác nhận khối:  
  - ✅ Thành công → Trạng thái cập nhật thành **Đã huỷ**, lưu `transaction signature`.  
  - ❌ Thất bại → Hiển thị lý do lỗi.  
<img width="1710" height="1112" alt="image" src="https://github.com/user-attachments/assets/a69d6b68-cf91-44fb-8aa1-8a005988be96" />


---

## 3. Lưu ý
- Cần đảm bảo ví mint có đủ **SOL** để trả phí gas.  
- Sau khi huỷ, văn bằng không thể phục hồi → chỉ thực hiện khi chắc chắn.  
- Tất cả hành động đều được ghi lại trong lịch sử giao dịch và trên blockchain để minh bạch và kiểm tra sau này (çó thể xem trực tiếp trên trang scan của blockchain Solana).  

