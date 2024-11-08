
# API Documentation

API này cung cấp các chức năng để tạo email ảo, đọc hộp thư đến, và lấy nội dung của một email cụ thể.

- **Base URL**: `https://liketudong.biz/apiv2`
- **Authentication**: API yêu cầu khóa truy cập (API key) để xác thực.

---

## 1. Tạo Email Ảo

- **Endpoint**: `/genmail.php`
- **Method**: `GET`
- **Mô tả**: Tạo một địa chỉ email ảo mới.

### Request
- **URL**: `https://liketudong.biz/apiv2/genmail.php`
- **Query Parameter**:
  - `key` (string) **Bắt buộc**: Khóa truy cập API của bạn.

**Ví dụ URL**:
```
https://liketudong.biz/apiv2/genmail.php?key={key}
```

### Response
- **200 OK**:
    ```json
    {
      "email": "m.i.c.ahlu.t.z87@gmail.com"
    }
    ```
- **Ý nghĩa**: Trả về địa chỉ email mới được tạo.

---

## 2. Đọc Hộp Thư Đến

- **Endpoint**: `/docmail.php`
- **Method**: `GET`
- **Mô tả**: Lấy danh sách các email trong hộp thư đến của một địa chỉ email ảo.

### Request
- **URL**: `https://liketudong.biz/apiv2/docmail.php`
- **Query Parameters**:
  - `key` (string) **Bắt buộc**: Khóa truy cập API của bạn.
  - `email` (string) **Bắt buộc**: Địa chỉ email mà bạn muốn kiểm tra hộp thư đến.

**Ví dụ URL**:
```
https://liketudong.biz/apiv2/docmail.php?key={key}&email={email}
```

### Response
- **200 OK**:
    ```json
    {
      "messageData": [
        {
          "messageID": "ADSVPN",
          "from": "AI TOOLS",
          "subject": "Unleash the power of AI with our ultimate directory of online tools!",
          "time": "Just Now"
        },
        {
          "messageID": "MTkzMDcxZjkxMTE3ZTIwNg==",
          "from": "Netflix <info@join.netflix.com>",
          "subject": "Hero, The Diplomat Season 2 is now on Netflix",
          "time": "16 hrs ago"
        }
      ]
    }
    ```
- **Ý nghĩa**: Trả về một mảng chứa danh sách email trong hộp thư đến của email ảo.

**Giải thích trường dữ liệu**:
  - `messageID` (string): ID của email, sử dụng để truy xuất nội dung chi tiết.
  - `from` (string): Người gửi email.
  - `subject` (string): Tiêu đề của email.
  - `time` (string): Thời gian email được gửi.

---

## 3. Đọc Nội Dung Email Cụ Thể

- **Endpoint**: `/getmail.php`
- **Method**: `GET`
- **Mô tả**: Lấy nội dung chi tiết của một email cụ thể.

### Request
- **URL**: `https://liketudong.biz/apiv2/getmail.php`
- **Query Parameters**:
  - `email` (string) **Bắt buộc**: Địa chỉ email mà bạn muốn đọc.
  - `messageID` (string) **Bắt buộc**: ID của email mà bạn muốn lấy nội dung.

**Ví dụ URL**:
```
https://liketudong.biz/apiv2/getmail.php?email={email}&messageID={messageID}
```

### Response
- **200 OK**: Nội dung của email được trả về dưới dạng HTML.
- **Ý nghĩa**: Trả về HTML của email được yêu cầu, bạn có thể hiển thị nội dung này trong trình duyệt hoặc ứng dụng đọc email.

---

### Mã Lỗi (Error Codes)

| Mã lỗi | Ý nghĩa                   |
|--------|----------------------------|
| 400    | Bad Request - Thông tin không hợp lệ |
| 401    | Unauthorized - Thiếu hoặc sai khóa API |
| 404    | Not Found - Email hoặc messageID không tồn tại |
| 500    | Internal Server Error - Lỗi hệ thống |

---
