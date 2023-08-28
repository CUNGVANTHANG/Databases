# MySQL
## Mục lục
- [I. Tổng quan về cơ sở dữ liệu](#i-tổng-quan-về-cơ-sở-dữ-liệu)
- [II. Truy vấn dữ liệu trong một bảng](#ii-truy-vấn-dữ-liệu-trong-một-bảng)
- [III. Truy vấn dữ liệu từ nhiều bảng](#iii-truy-vấn-dữ-liệu-từ-nhiều-bảng)
- [IV. Kết hợp bảng và Nhóm kiểu dữ liệu](#iv-kết-hợp-bảng-và-nhóm-kiểu-dữ-liệu)

## I. Tổng quan về cơ sở dữ liệu
**Cơ sở dữ liệu là gì?**

Cơ sở dữ liệu là một tập hợp dữ liệu liên quan được chia sẻ chung. Dữ liệu có thể là các sự kiện đã biết có thể được ghi lại và có ý nghĩa nào đó. Ví dụ, tên, số điện thoại và địa chỉ của những người bạn biết.

**Hệ quản trị cơ sở dữ liệu là gì?**

Hệ quản trị cơ sở dữ liệu (Database Management System - DBMS) là một phần mềm được sử dụng để quản lý và tổ chức dữ liệu trong một hệ thống cơ sở dữ liệu. Nó cung cấp các công cụ và chức năng cho phép người dùng tạo, lưu trữ, truy xuất, cập nhật và xóa dữ liệu trong cơ sở dữ liệu.

**Cấu trúc cơ bản của một chương trình SQL**

```sql
SELECT .... FROM .... WHERE ...;
```

Ý nghĩa:

```sql
"Hiển thị dữ liệu ... từ ... thỏa mãn ..."
```

| Cú pháp | Ý nghĩa |
| :--- | :--- |
| `SELECT` | Xem dữ liệu từ một hoặc nhiều bảng |
| `INSERT` | Thêm mới dữ liệu |
| `UPDATE` | Chỉnh sửa thông tin dữ liệu |
| `DELETE` | Xóa dữ liệu |

