# BÁO CÁO PHÂN TÍCH VÀ THIẾT KẾ CLASS DIAGRAM PHÂN HỆ ĐƠN HÀNG HỆ THỐNG RIKKEISHOP

> 👤 **Học viên:** Đỗ Hoàng Sơn | **Mã SV:** PTIT-HCM-066
> 🏫 **Môn học:** IT105-K25-Phan-tich-thi-t-k-h-th-ng

---

## 📊 Sơ đồ thiết kế hệ thống (Class Diagram)

> 💡 *Sơ đồ dưới đây được render tự động trực tiếp trên GitHub bằng Mermaid. Bạn cũng có thể tải file **`bt1.drawio`** trong repository này để mở và chỉnh sửa trực tiếp trên [Draw.io (diagrams.net)](https://app.diagrams.net).* 

```mermaid
classDiagram
    class Customer {
        -String customerId
        -String fullName
        -String phoneNumber
        +placeOrder(): Order
    }
    class Order {
        -String orderId
        -String createdDate
        -double totalAmount
        +calculateTotal(): double
    }
    Customer '1' -- '0..*' Order : places
```

---

## Bước 1: Trích xuất Lớp, Thuộc tính và Phương thức

Dựa trên yêu cầu nghiệp vụ của hệ thống thương mại điện tử RikkeiShop, chúng ta thực hiện bóc tách ngữ nghĩa các danh từ và động từ trong mô tả: 'Mỗi Khách hàng (Customer) có các thông tin như Mã khách hàng, Họ tên, Số điện thoại. Khách hàng có thể thực hiện đặt hàng (placeOrder). Mỗi Đơn hàng (Order) bao gồm Mã đơn hàng, Ngày tạo, và có thể tính tổng tiền (calculateTotal)'.

Danh từ đại diện cho các Lớp (Entities/Classes) và Thuộc tính (Attributes/Fields). Động từ đại diện cho các Phương thức (Methods/Operations) xử lý logic nghiệp vụ. Bảng trích xuất chi tiết như sau:

| Thành phần | Lớp Customer | Lớp Order |
| --- | --- | --- |
| Thuộc tính (Attributes) | customerId (Mã khách hàng), fullName (Họ tên), phoneNumber (Số điện thoại) | orderId (Mã đơn hàng), createdDate (Ngày tạo), totalAmount (Tổng tiền đơn hàng) |
| Phương thức (Methods) | placeOrder() (Đặt hàng mới) | calculateTotal() (Tính tổng tiền đơn hàng) |

## Bước 2: Thiết lập Access Modifiers và Multiplicity

Để đảm bảo tính đóng gói (Encapsulation) trong lập trình hướng đối tượng (OOP) cũng như xác định chính xác mối quan hệ dữ liệu giữa hai đối tượng, các bổ từ truy cập (Access Modifiers) và bội số (Multiplicity) được quy định chặt chẽ:

- Mức truy cập cho các thuộc tính (customerId, fullName, phoneNumber, orderId, createdDate, totalAmount): private (Ký hiệu: '-'). Quy định này ngăn chặn việc truy cập và sửa đổi trực tiếp dữ liệu từ bên ngoài lớp, đảm bảo tính toàn vẹn dữ liệu.
- Mức truy cập cho các phương thức (placeOrder, calculateTotal): public (Ký hiệu: '+'). Cho phép các thành phần khác trong hệ thống gọi thực thi các hành vi nghiệp vụ này.
- Quan hệ giữa Customer và Order là quan hệ Association (Kết hợp trực tiếp giữa hai lớp thực thể độc lập). Bội số (Multiplicity) từ Customer sang Order là: 1 - 0..* (Một khách hàng có thể có 0 hoặc nhiều đơn hàng, nhưng một đơn hàng bắt buộc chỉ thuộc về duy nhất 1 khách hàng).

## Bước 3: Xây dựng Class Diagram chuẩn UML cho Hệ thống RikkeiShop

Sơ đồ Class Diagram dưới đây chuẩn hóa mô hình lớp cho hai đối tượng Customer và Order, ghi rõ kiểu dữ liệu gợi ý (String, double, Date) và bổ từ truy cập chuẩn mực.

Tài liệu thiết kế này đóng vai trò là chuẩn giao tiếp giữa bộ phận System Analyst (SA) và Đội ngũ lập trình (Dev), giúp việc khai báo Entity Class và Mapper diễn ra chính xác, tránh nhầm lẫn biến trong quá trình xây dựng chức năng 'Tạo đơn hàng' và 'Tính tổng tiền đơn hàng'.

## Bước 4: Đánh giá mở rộng kiến trúc và Hướng dẫn sử dụng file .drawio

Trong các phiên bản phát triển tiếp theo của RikkeiShop, mô hình lớp này có thể mở rộng bằng cách bổ sung lớp OrderDetail (Chi tiết đơn hàng) đóng vai trò lớp trung gian giữa Order và Product (Sản phẩm) để quản lý số lượng, đơn giá từng mặt hàng.

Sơ đồ thiết kế Class Diagram đã được lưu trữ dưới định dạng `.drawio` tiêu chuẩn trong bài nộp. Giảng viên và Đội ngũ Dev có thể mở trực tiếp bằng ứng dụng Draw.io (Diagrams.net) để kiểm tra các thông số thuộc tính và mối quan hệ giữa các lớp.

---

## 📁 Danh sách tệp tin nộp bài trong Repository
- 📝 `bt1.docx`: Báo cáo tài liệu phân tích nghiệp vụ hoàn chỉnh.
- 🎨 `bt1.drawio`: File thiết kế sơ đồ chuẩn theo quy định đề bài (mở trực tiếp bằng [Draw.io](https://app.diagrams.net) hoặc Lucidchart).
