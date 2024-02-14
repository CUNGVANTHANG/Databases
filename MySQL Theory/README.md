# Database
## Mục lục
- [Database](#database)
  - [Mục lục](#mục-lục)
  - [I. Tổng quan về cơ sở dữ liệu](#i-tổng-quan-về-cơ-sở-dữ-liệu)
  - [II. Truy vấn dữ liệu trong một bảng `SELECT ...,...,... FROM ... WHERE...`](#ii-truy-vấn-dữ-liệu-trong-một-bảng-select--from--where)
    - [1. Toán tử `OR, AND, BETWEEN, NOT`](#1-toán-tử-or-and-between-not)
    - [2. Kết hợp nhiều điều kiện bằng cách sử dụng dấu ngoặc `()`](#2-kết-hợp-nhiều-điều-kiện-bằng-cách-sử-dụng-dấu-ngoặc-)
    - [3. Dữ liệu văn bản sử dụng dấu nháy đơn `''`](#3-dữ-liệu-văn-bản-sử-dụng-dấu-nháy-đơn-)
    - [4. Ký hiệu phần trăm `%, LIKE`](#4-ký-hiệu-phần-trăm--like)
    - [5. Ký hiệu gạch dưới `_, LIKE`](#5-ký-hiệu-gạch-dưới-_-like)
    - [6. Tìm các giá trị `IS NOT NULL, IS NULL`](#6-tìm-các-giá-trị-is-not-null-is-null)
  - [III. Truy vấn dữ liệu từ nhiều bảng `SELECT ...,...,... FROM ...,...,... WHERE ...`](#iii-truy-vấn-dữ-liệu-từ-nhiều-bảng-select--from--where-)
    - [1. Tham chiếu đến các cột cụ thể `.`](#1-tham-chiếu-đến-các-cột-cụ-thể-)
    - [2. Cấu trúc kết hợp bảng `JOIN ... ON`](#2-cấu-trúc-kết-hợp-bảng-join--on)
    - [3. Trích xuất cột cụ thể `.`](#3-trích-xuất-cột-cụ-thể-)
    - [4. Đổi tên cột, tên bảng `AS`](#4-đổi-tên-cột-tên-bảng-as)
  - [IV. Kết hợp bảng và Nhóm kiểu dữ liệu](#iv-kết-hợp-bảng-và-nhóm-kiểu-dữ-liệu)
    - [1. Sắp xếp các hàng `ORDER BY, ASC, DESC`](#1-sắp-xếp-các-hàng-order-by-asc-desc)
    - [2. Lọc trùng dữ liệu `DISTINCT`](#2-lọc-trùng-dữ-liệu-distinct)
    - [3. Đếm số hàng `COUNT()`](#3-đếm-số-hàng-count)
    - [4. Giá trị lớn nhất, nhỏ nhất `MAX(), MIN()`](#4-giá-trị-lớn-nhất-nhỏ-nhất-max-min)
    - [5. Tính giá trị trung bình `AVG`](#5-tính-giá-trị-trung-bình-avg)
    - [6. Tính tổng giá trị `SUM`](#6-tính-tổng-giá-trị-sum)
    - [7. Nhóm hàng cùng giá trị `GROUP BY`](#7-nhóm-hàng-cùng-giá-trị-group-by)
    - [8. Lọc nhóm dữ liệu `GROUP BY, HAVING`](#8-lọc-nhóm-dữ-liệu-group-by-having)
  - [V. Join nâng cao](#v-join-nâng-cao)
    - [1. Chỉ trả về giá trị hai bảng khớp với nhau `INNER JOIN`](#1-chỉ-trả-về-giá-trị-hai-bảng-khớp-với-nhau-inner-join)
    - [2. Trả về tất cả giá trị bảng bên trái khớp với bảng bên phải `LEFT JOIN`](#2-trả-về-tất-cả-giá-trị-bảng-bên-trái-khớp-với-bảng-bên-phải-left-join)
    - [3. Trả về tất cả giá trị bảng bên phải khớp với bảng bên trái `RIGHT JOIN`](#3-trả-về-tất-cả-giá-trị-bảng-bên-phải-khớp-với-bảng-bên-trái-right-join)
    - [4. Trả về tất cả giá trị hai bảng khớp nhau `FULL JOIN`](#4-trả-về-tất-cả-giá-trị-hai-bảng-khớp-nhau-full-join)
    - [5. Kết hợp bảng không sử dụng điều kiện `NATURAL JOIN`](#5-kết-hợp-bảng-không-sử-dụng-điều-kiện-natural-join)
    - [6. Nối bảng với chính nó bằng bí danh](#6-nối-bảng-với-chính-nó-bằng-bí-danh)
  - [VI. Truy vấn con](#vi-truy-vấn-con)
    - [1. Truy vấn con `()`](#1-truy-vấn-con-)
    - [2. So sánh giá trị với giá trị trong tập hợp `IN`](#2-so-sánh-giá-trị-với-giá-trị-trong-tập-hợp-in)
    - [3. So sánh giá trị với tất cả giá trị trong tập hợp `ALL`](#3-so-sánh-giá-trị-với-tất-cả-giá-trị-trong-tập-hợp-all)
    - [4. So sánh giá trị với ít nhất một giá trị trong tập hợp `ANY`](#4-so-sánh-giá-trị-với-ít-nhất-một-giá-trị-trong-tập-hợp-any)
    - [5. Truy vấn con tương quan](#5-truy-vấn-con-tương-quan)
    - [6. Đặt bí danh cho bảng với truy vấn con](#6-đặt-bí-danh-cho-bảng-với-truy-vấn-con)
    - [7. Kiểm tra tập hợp con có chứa bất kỳ dòng dữ liệu `EXISTS`](#7-kiểm-tra-tập-hợp-con-có-chứa-bất-kỳ-dòng-dữ-liệu-exists)
    - [8. Truy vấn con trong mệnh đề `FROM`](#8-truy-vấn-con-trong-mệnh-đề-from)
    - [9. Truy vấn con trong mệnh đề `SELECT`](#9-truy-vấn-con-trong-mệnh-đề-select)

## I. Tổng quan về cơ sở dữ liệu
[:arrow_up: Mục lục](#mục-lục)

| Cú pháp | Ý nghĩa |
| :---: | :---: | 
| `SELECT` | Xem dữ liệu từ một hoặc nhiều bảng |
| `INSERT` | Thêm mới dữ liệu |
| `UPDATE` | Chỉnh sửa thông tin dữ liệu |
| `DELETE` | Xóa dữ liệu |

> `SELECT .... FROM .... WHERE ...;`

`SELECT` có ý nghĩa là hiển thị thông tin dữ liệu. Ở đây câu này có nghĩa là "Hiển thị dữ liệu" lên màn hình. Còn nếu áp dụng cả FROM và WHERE thì câu lệnh sẽ là :"Hiển thị dữ liệu ... từ ... thỏa mãn điều kiện ..."

## II. Truy vấn dữ liệu trong một bảng `SELECT ...,...,... FROM ... WHERE...`
[:arrow_up: Mục lục](#mục-lục)

> `SELECT * FROM ...;`

`*` có nghĩa là tất cả. Ở đây câu này có nghĩa là "Hiển thị **tất cả các cột** từ bảng ..."

> `SELECT ... FROM ...;`

Ở đây câu này có nghĩa là "Hiển thị cột ... từ bảng ..."

> `SELECT ..., ... FROM ...;`

Ở đây câu này có nghĩa là "Hiển thị cột ..., ... từ bảng ..."

> `SELECT ... FROM ... WHERE ...;`

Ở đây câu này có nghĩa là "Hiển thị cột ... từ bảng ... thỏa mãn điều kiện ..."

*Ví dụ:*

```sql
SELECT * FROM xe WHERE nam_san_xuat = 2022;

-- Nghĩa là 'hiển thị tẩt cả cột' trong bảng 'xe' thỏa mãn điều kiện các hàng trong cột `nam_san_xuat = 2022`
```

### 1. Toán tử `OR, AND, BETWEEN, NOT`
[:arrow_up: Mục lục](#mục-lục)

| Toán tử | Ý nghĩa |
| `OR` | hoặc |
| `AND` | và (đến) |
| `BETWEEN` | từ |
| `NOT` | phủ định |

*Ví dụ:*

```sql
-- Toán tử OR
SELECT id, name FROM user WHERE age > 50 OR height < 185;

-- Toán tử AND
SELECT id, name FROM user WHERE age <= 70 AND age >= 13;

-- Toán tử BETWEEN
-- Bản chất:
SELECT id, name FROM user WHERE age <= 70 AND age >= 13;

-- Sử dụng toán tử:
SELECT id, name FROM user WHERE age BETWEEN 13 AND 70;

-- Toán tử NOT
SELECT * FROM user WHERE age NOT BETWEEN 20 AND 30;
```

### 2. Kết hợp nhiều điều kiện bằng cách sử dụng dấu ngoặc `()`
[:arrow_up: Mục lục](#mục-lục)

```sql
SELECT
  id,
  name
FROM user
WHERE (age > 70 OR age < 13)
  AND (height >= 180);
```

### 3. Dữ liệu văn bản sử dụng dấu nháy đơn `''`
[:arrow_up: Mục lục](#mục-lục)

```sql
SELECT age
FROM user
WHERE name = 'Smith';
```

### 4. Ký hiệu phần trăm `%, LIKE`
[:arrow_up: Mục lục](#mục-lục)

`LIKE` cho phép sử dụng ký hiệu phần trăm `%`. Dấu `%` được áp dụng trong ví dụ **so khớp với bất kỳ số lượng ký tự** không xác định nào (từ 0 đến nhiều ký tự).

*Ví dụ:*

```sql
-- Hiển thị tất cả cột trong bảng user thỏa mãn name bắt đầu bằng chữ A
SELECT *
FROM user
WHERE name LIKE 'A%';

-- Hiển thị tất cả cột trong bảng user thỏa mãn name kết thúc bằng chữ A
SELECT *
FROM user
WHERE name LIKE '%A';

-- Hiển thị tất cả cột trong bảng user thỏa mãn name bắt đầu hoặc kết thúc bằng chữ A
SELECT *
FROM user
WHERE name LIKE '%A%';
```

### 5. Ký hiệu gạch dưới `_, LIKE`
[:arrow_up: Mục lục](#mục-lục)

Ký hiệu gạch dưới `_` dùng để **khớp chính xác một ký tự**. 

*Ví dụ:*

```sql
-- Tìm một cô gái có tên là Catherine? hay là Katherine? khi chưa biết chính xác
SELECT *
FROM user
WHERE name LIKE '_atherine';
```

### 6. Tìm các giá trị `IS NOT NULL, IS NULL`
[:arrow_up: Mục lục](#mục-lục)

*Ví dụ 1: Tìm giá trị không NULL*

```sql
SELECT id
FROM user
WHERE middle_name IS NOT NULL;
```

Chương trình này chỉ chọn những người dùng có tên đệm, tức là cột `middle_name` đã được điền giá trị (nghĩa là giá trị không NULL).

*Ví dụ 2: Tìm giá trị NULL*

```sql
SELECT id
FROM user
WHERE middle_name IS NULL;
```

Truy vấn này sẽ trả về chỉ những người dùng không có tên đệm, tức là `middle_name` không được cung cấp trong cơ sở dữ liệu (nghĩa là giá trị NULL)

*Ví dụ 3: So sánh với NULL*

Nếu bạn đặt điều kiện trên một cột cụ thể, ví dụ như `AGE < 70`, các hàng mà `age` là `NULL` sẽ luôn bị loại khỏi kết quả.

`NULL` không bao giờ bằng `0`. Nên vì thế biểu thức `NULL = NULL` sẽ không bao giờ đúng trong SQL


## III. Truy vấn dữ liệu từ nhiều bảng `SELECT ...,...,... FROM ...,...,... WHERE ...`
[:arrow_up: Mục lục](#mục-lục)

### 1. Tham chiếu đến các cột cụ thể `.`
[:arrow_up: Mục lục](#mục-lục)

Bằng cách cung cấp tên của bảng và cột, được phân tách bằng dấu chấm `.`

_Ví dụ:_

```sql
-- Dùng để xem xét các tổ hợp mà id trong person giống owner_id trong car
SELECT *
FROM person, car
WHERE person.id = car.owner_id;
```

### 2. Cấu trúc kết hợp bảng `JOIN ... ON`
[:arrow_up: Mục lục](#mục-lục)

Sử dụng `JOIN` để kết hợp các bảng, `ON` là điều kiện kết hợp bảng

_Ví dụ 1:_

```sql
-- Kết hợp bảng person và car, ta sử dụng JOIN giữa tên hai bảng. Ngoài ra, ta cũng có thể đặt điều kiện kết hợp các bảng bằng ON. Sau từ khóa ON chúng ta có thể đặt điều kiện để chỉ kết hợp những hàng có id trong person giống owner_id trong car.
SELECT *
FROM person
JOIN car
  ON person.id = car.owner_id;
```

_Ví dụ 2:_

| | |
|:--: | :---: |
| `SELECT * FROM phim JOIN dao_dien ON phim.ma_dao_dien = dao_dien.id;` | `SELECT * FROM dao_dien JOIN phim ON phim.ma_dao_dien = dao_dien.id;` |
| ![image](https://github.com/CUNGVANTHANG/Java_Back-end/assets/96326479/768622a6-3b99-4cab-8bab-4ee01bd55fbf) | ![image](https://github.com/CUNGVANTHANG/Java_Back-end/assets/96326479/35d21419-d6c1-4ee3-a10d-a2db12d1bf67) |

_Chú ý:_ 

- Bảng 1: Bảng đầu tiên trong truy vấn

- Bảng 2: Bảng thứ hai trong truy vấn

Bảng 1 `JOIN` Bảng 2 thì kết quả sẽ là `Bảng 1 | Bảng 2`

Bảng 2 `JOIN` Bảng 1 thì kết quả sẽ là `Bảng 2 | Bảng 1`

Kết hợp bảng sử dụng `JOIN`, bảng ban đầu sẽ nối với bảng tiếp theo ở **phía bên phải** bảng

### 3. Trích xuất cột cụ thể `.`
[:arrow_up: Mục lục](#mục-lục)

_Ví dụ:_

```sql
-- Hiển thị một vài cột trong kết quả đầu ra. Chúng ta chỉ muốn biết mẫu xe và tên chủ sở hữu. Vì có nhiều hơn một bảng, chúng ta đặt tên bảng trước tên cột và phân tách chúng bằng dấu chấm .
SELECT
  person.name,
  car.model
FROM person
JOIN car
  ON person.id = car.owner_id;
```

### 4. Đổi tên cột, tên bảng `AS`
[:arrow_up: Mục lục](#mục-lục)

_Ví dụ 1:_ Đổi tên cột

```sql
-- Đổi tên cột person.id và car.id thành person_id và car_id tương ứng.
SELECT
  person.id AS person_id,
  car.id AS car_id
FROM person
JOIN car
  ON person.id = car.owner_id;
```

_Chú ý:_ Tên mới chỉ là **bí danh**, nghĩa là nó là tên tạm thời và **không thay đổi tên thực tế trong cơ sở dữ liệu**. Nó chỉ ảnh hưởng đến cách cột được **hiển thị trong kết quả của truy vấn**. Kỹ thuật này thường được sử dụng khi có một vài cột có cùng tên từ các bảng khác nhau.

_Ví dụ 2:_ Đổi tên bảng

```sql
-- Đổi tên bảng person thành p, tên car thành c
SELECT
  p.id,
  p.name,
  p.year,
  c.id,
  c.name,
  c.year
FROM person AS p
JOIN car AS c
  ON p.id = c.owner_id;
```

## IV. Kết hợp bảng và Nhóm kiểu dữ liệu
[:arrow_up: Mục lục](#mục-lục)

### 1. Sắp xếp các hàng `ORDER BY, ASC, DESC`
[:arrow_up: Mục lục](#mục-lục)

_Ví dụ 1:_

```sql
-- Sắp xếp các hàng theo customer_id
SELECT *
FROM orders
ORDER BY customer_id;
```

_Ví dụ 2:_ Sắp xếp tăng dần

```sql
-- Sắp xếp các hàng tăng dần theo customer_id
SELECT *
FROM orders
ORDER BY customer_id ASC;
```

_Ví dụ 3:_ Sắp xếp giảm dần

```sql
-- Sắp xếp các hàng giảm dần theo customer_id
SELECT *
FROM orders
ORDER BY customer_id DESC;
```

_Ví dụ 4:_ Sắp xếp theo một vài cột

```sql
-- Sắp xếp theo customer_id theo thứ tự tăng dần (giá trị thấp nhất trước) và sau đó, với mỗi customer_id, các đơn hàng sẽ được sắp xếp theo total_sum theo thứ tự giảm dần (giá trị lớn nhất trước).
SELECT *
FROM order
ORDER BY customer_id ASC, total_sum DESC;
```

_Ví dụ 5:_ Sắp xếp có điều kiện

```sql
-- Các đơn hàng được đặt bởi khách hàng có id là 100. Các đơn hàng sẽ được sắp xếp theo tổng số tiền - đơn hàng rẻ nhất sẽ xuất hiện đầu tiên và đắt nhất xuất hiện cuối cùng.
SELECT *
FROM orders
WHERE customer_id = 100
ORDER BY total_sum;
```

### 2. Lọc trùng dữ liệu `DISTINCT`
[:arrow_up: Mục lục](#mục-lục)

_Ví dụ 1:_ Nguyên nhân

```sql
-- Có nhiều dữ liệu trùng lặp
SELECT nam_lam
FROM nhan_vien;
```

<img src="https://github.com/CUNGVANTHANG/Java_Back-end/assets/96326479/d4262e57-379f-4106-8218-345fd7a47aad">


_Ví dụ 2:_ Khắc phục sử dụng `DISTINCT` để lọc dữ liệu **loại bỏ các bản ghi trùng lặp** và **hiện thị 1 lần**

```sql
SELECT DISTINCT nam_lam
FROM nhan_vien;
```

<img src="https://github.com/CUNGVANTHANG/Java_Back-end/assets/96326479/6931b737-b5a5-4236-9fb6-1990ee3a51a9">

### 3. Đếm số hàng `COUNT()`
[:arrow_up: Mục lục](#mục-lục)

_Ví dụ 1:_ Đếm tất cả các hàng

```sql
-- Đếm tất cả các hàng
SELECT COUNT(*)
FROM orders;
```

_Ví dụ 2:_ Đếm số hàng không NULL

```sql
-- Nếu có một giá trị NULL trong cột customer_id, hàng đó sẽ không được tính vào kết quả.
SELECT COUNT(customer_id)
FROM orders;
```

_Ví dụ 3:_ Đếm giá trị duy nhất trong một cột sử dụng `DISTINCT`

```sql
-- Đếm các hàng chứa giá trị duy nhất trong cột customer_id. Nói cách khác, câu lệnh này cho chúng ta biết có bao nhiêu khách hàng khác nhau đã đặt hàng cho đến nay. Nếu một khách hàng đặt 5 đơn hàng, khách hàng đó sẽ chỉ được đếm một lần.
SELECT COUNT(DISTINCT customer_id) AS distinct_customers
FROM orders;
```

### 4. Giá trị lớn nhất, nhỏ nhất `MAX(), MIN()`
[:arrow_up: Mục lục](#mục-lục)

_Ví dụ:_

```sql
-- Hàm MIN(total_sum) trả về giá trị nhỏ nhất trong cột total_sum. Như vậy, chúng ta có thể tìm ra đơn hàng rẻ nhất trong bảng. 
SELECT MIN(total_sum)
FROM orders;
```

### 5. Tính giá trị trung bình `AVG`
[:arrow_up: Mục lục](#mục-lục)

_Ví dụ:_

```sql
-- Chúng ta sẽ nhận được giá trị trung bình của đơn hàng cho khách hàng có id 100.
SELECT AVG(total_sum)
FROM orders
WHERE customer_id = 100;
```

### 6. Tính tổng giá trị `SUM`
[:arrow_up: Mục lục](#mục-lục)

_Ví dụ:_

```sql
-- Tính tổng giá trị của tất cả các đơn hàng được đặt bởi khách hàng có id 100
SELECT SUM(total_sum)
FROM orders
WHERE customer_id = 100;
```

### 7. Nhóm hàng cùng giá trị `GROUP BY`
[:arrow_up: Mục lục](#mục-lục)

_Ví dụ 1:_ Kết hợp `GROUP BY` với `COUNT()`

```sql
-- Chúng ta nhập GROUP BY theo sau là tên cột (customer_id). GROUP BY sẽ nhóm tất cả các hàng có cùng giá trị trong cột được chỉ định lại với nhau.

-- Trong ví dụ của chúng ta, tất cả các đơn được đặt bởi cùng một khách hàng sẽ được nhóm lại thành một hàng.
-- Hàm COUNT(*) sau đó sẽ đếm số hàng cho khách hàng cụ thể đó.
-- Kết quả, chúng ta sẽ có một bảng trong đó mỗi customer_id sẽ được hiển thị cùng với số lượng đơn hàng được đặt bởi khách hàng đó.
SELECT
  customer_id,
  COUNT(*)
FROM orders
GROUP BY customer_id;
```

![image](https://github.com/CUNGVANTHANG/Java_Back-end/assets/96326479/934e3abe-7973-419f-98a3-0cd607104fdf)

_Ví dụ 2:_ Kết hợp `GROUP BY` với `MAX(), MIN()`

```sql
-- Tìm đơn hàng có giá trị cao nhất cho mỗi khách hàng.
SELECT
  customer_id,
  MAX(total_sum)
FROM orders
GROUP BY customer_id;
```

_Ví dụ 3:_ Kết hợp `GROUP BY` với `AVG`

```sql
-- Tính giá trị đơn hàng trung bình cho mỗi khách hàng, nhưng chỉ với các đơn hàng trong năm 2019.
SELECT
  customer_id,
  AVG(total_sum)
FROM orders
WHERE order_date >= '2019-01-01'
  AND order_date < '2020-01-01'
GROUP BY custome
```

_Ví dụ 4:_ Nhóm các hàng dựa trên nhiều cột

```sql
SELECT
  customer_id,
  order_date,
  SUM(total_sum)
FROM orders
GROUP BY customer_id, order_date;
```

![image](https://github.com/CUNGVANTHANG/Java_Back-end/assets/96326479/d9f6071e-e190-40f4-af34-60a5ab73dc87)

### 8. Lọc nhóm dữ liệu `GROUP BY, HAVING`
[:arrow_up: Mục lục](#mục-lục)

_Ví dụ:_

```sql
-- Sử dụng từ khóa HAVING và sau đó cung cấp điều kiện lọc kết quả.
-- Trong trường hợp này, ta chỉ muốn hiển thị những khách hàng có tổng giá trị đơn hàng theo ngày lớn hơn $2.000.
SELECT
  customer_id,
  order_date,
  SUM(total_sum)
FROM orders
GROUP BY customer_id, order_date
HAVING SUM(total_sum) > 2000;
```

_Chú ý:_ 

- Không thể đặt `WHERE` trước `FROM`. Tương tự, `HAVING` luôn phải đứng sau `GROUP BY`
- `WHERE` được sử dụng để lọc dữ liệu trước khi nhóm và tổng hợp thông tin, trong khi `HAVING` được sử dụng để lọc dữ liệu sau khi đã được nhóm và tổng hợp thông tin.

## V. Join nâng cao
[:arrow_up: Mục lục](#mục-lục)

### 1. Chỉ trả về giá trị hai bảng khớp với nhau `INNER JOIN`
[:arrow_up: Mục lục](#mục-lục)

<img src="https://github.com/CUNGVANTHANG/Java_Back-end/assets/96326479/04c19cb2-765d-471b-a928-de1430c92aa5" width=300px>

Tên đầy đủ của `JOIN` là `INNER JOIN`

_Ví dụ:_

```sql
SELECT 
  phong.id AS ma_phong,
  so_phong,
  giuong,
  tang,
  thiet_bi.id AS ma_thiet_bi,
  ten 
FROM phong
INNER JOIN thiet_bi
  ON ma_phong = phong.id;
```

`INNER JOIN` (hoặc `JOIN`) **chỉ hiển thị các hàng từ hai bảng có các giá trị trong cột khớp với nhau**. Nói cách khác, bạn chỉ có thể thấy những thiết bị có trong phòng được chỉ định và ngược lại. **Thiết bị không có trong phòng không được hiển thị trong kết quả. Hãy xem bảng sau**:

![image](https://github.com/CUNGVANTHANG/Java_Back-end/assets/96326479/ca418bfc-ac2d-4ec5-878c-ed37368c930e)

Các hàng <span style="color: green;">**màu xanh**</span> là kết quả của `INNER JOIN`. Thiết bị có giá trị `NULL` trong cột `room_id`(các hàng <span style="color: yellow;">**màu vàng**</span>) không được hiển thị trong kết quả của `INNER JOIN`.

### 2. Trả về tất cả giá trị bảng bên trái khớp với bảng bên phải `LEFT JOIN`
[:arrow_up: Mục lục](#mục-lục)

<img src="https://github.com/CUNGVANTHANG/Java_Back-end/assets/96326479/8f07b255-8feb-4904-b389-c4b96033772d" width=300px>

`LEFT JOIN` tên đầy đủ là `LEFT OUTER JOIN`

`LEFT JOIN` hoạt động theo cách sau: nó **trả về tất cả** các hàng từ **bảng bên trái** (bảng đầu tiên trong truy vấn) cộng với tất cả các hàng khớp từ **bảng bên phải** (bảng thứ hai trong truy vấn).

Nếu không có giá trị chung trong cột kết hợp, các cột từ bảng bên phải sẽ chứa giá trị `NULL`.

_Ví dụ:_

```sql
SELECT *
FROM car
LEFT JOIN person
  ON car.owner_id = person.id;
```

![image](https://github.com/CUNGVANTHANG/Java_Back-end/assets/96326479/9c138f33-88ac-4d66-ab6b-cb609f3c4331)

`LEFT JOIN` trả về tất cả các hàng trong bảng trên. Các hàng <span style="color: green;">**màu xanh**</span> được trả về bởi `INNER JOIN`. Các hàng <span style="color: yellow;">**màu vàng**</span> được thêm vào bởi `LEFT JOIN`: tuy không có người sở hữu khớp với các xe <span style="color: yellow;">**màu vàng**</span>  nhưng `LEFT JOIN` vẫn trả về chúng.

### 3. Trả về tất cả giá trị bảng bên phải khớp với bảng bên trái `RIGHT JOIN`
[:arrow_up: Mục lục](#mục-lục)

<img src="https://github.com/CUNGVANTHANG/Java_Back-end/assets/96326479/9d24b264-1f1e-4ccf-b5c7-c81a14dcaa1e" width=300px>

`RIGHT JOIN` tên đầy đủ là `RIGHT OUTER JOIN`

`RIGHT JOIN` hoạt động như sau: nó **trả về tất cả** các hàng từ **bảng bên phải** (bảng thứ hai trong câu truy vấn) cộng với tất cả các hàng khớp từ **bảng bên trái** (bảng đầu tiên trong câu truy vấn).

_Ví dụ:_

```sql
SELECT *
FROM car
RIGHT JOIN person
  ON car.owner_id = person.id;
```

![image](https://github.com/CUNGVANTHANG/Java_Back-end/assets/96326479/3473149a-cd26-47b9-9522-5aebfe348c5c)

`RIGHT JOIN` trả về tất cả các hàng trong bảng trên. Các hàng <span style="color: green;">**màu xanh**</span> được trả về `INNER JOIN`. Các hàng <span style="color: yellow;">**màu vàng**</span> được thêm vào bởi `RIGHT JOIN`.

_Chú ý:_ Thứ tự các bảng trong `LEFT JOIN` và `RIGHT JOIN` rất quan trọng. Nói cách khác, `car RIGHT JOIN person` giống như `person LEFT JOIN car`

### 4. Trả về tất cả giá trị hai bảng khớp nhau `FULL JOIN`
[:arrow_up: Mục lục](#mục-lục)

Tên đầy đủ `FULL JOIN` là `FULL OUTER JOIN`

`FULL JOIN` trả về tất cả các hàng từ cả hai bảng và kết hợp các hàng có giá trị khớp nhau. Nói cách khác, `FULL JOIN` là kết hợp của `LEFT JOIN` và `RIGHT JOIN`.

_Ví dụ:_

```sql
SELECT *
FROM car
FULL JOIN person
  ON car.owner_id = person.id;
```

![image](https://github.com/CUNGVANTHANG/Java_Back-end/assets/96326479/88442ce7-6f78-4f16-b331-8b4e98af7b48)

Các hàng <span style="color: yellow;">**màu vàng**</span> được trả về bởi `INNER JOIN`.

Các hàng <span style="color: green;">**màu xanh**</span> sẽ được thêm vào bởi `LEFT JOIN`

Các hàng <span style="color: pink;">**màu hồng**</span> sẽ được thêm vào bởi `RIGHT JOIN`.

`FULL JOIN` trả về tất cả các hàng từ bảng trên.

### 5. Kết hợp bảng không sử dụng điều kiện `NATURAL JOIN`
[:arrow_up: Mục lục](#mục-lục)

`NATURAL JOIN` không yêu cầu nhập tên cột vì nó luôn kết hợp hai bảng dựa trên các cột có cùng tên.

_Ví dụ:_

```sql
SELECT *
FROM sinh_vien
NATURAL JOIN phong;
```

cho kết quả giống

```sql
SELECT *
FROM sinh_vien
JOIN phong
  ON sinh_vien.id = phong.id;
```

_Chú ý:_ Tuy nhiên, `NATURAL JOIN` không được sử dụng rộng rãi trong thực tế, do nó có thể dẫn đến những vấn đề khi tên cột không đồng nhất hoặc khi có nhiều hơn một cột có cùng tên trong các bảng. Thay vào đó, người ta thường sử dụng các phép toán join khác, chẳng hạn như `INNER JOIN` hoặc `LEFT JOIN`, và xác định rõ các điều kiện kết nối (`ON`) để tránh những vấn đề này.

### 6. Nối bảng với chính nó bằng bí danh
[:arrow_up: Mục lục](#mục-lục)

_Ví dụ 1:_

```sql
-- Chúng ta muốn đưa thông tin về mẹ và trẻ vào một cơ sở dữ liệu.
-- Tại một thời điểm cụ thể, chúng ta cũng muốn hiển thị thông tin về trẻ cùng với mẹ bằng cách sử dụng JOIN.
-- Giả sử Lưu trữ thông tin về trẻ và mẹ trong cùng bảng person.
-- Mỗi hàng đều có cột mother_id. Cột này chứa ID của một hàng khác - hàng của mẹ.
SELECT *
FROM person AS child
JOIN person AS mother
  ON child.mother_id = mother.id;
```

Nhờ có bí danh, máy chủ cơ sở dữ liệu sẽ có thể sử dụng cùng một bảng `person` hai lần - lần đầu tiên để tìm kiếm trẻ và lần thứ hai để tìm kiếm mẹ của trẻ.

*Ví dụ 2:*

_Bảng `sinh_vien`:_

<img src="https://github.com/CUNGVANTHANG/Java_Back-end/assets/96326479/bfdb1a5c-207c-4fac-82bf-e1ebf2154f36">

<img src="https://github.com/CUNGVANTHANG/Java_Back-end/assets/96326479/f4a3638c-5c73-4403-b7d0-834e3cab43f5">

_Bảng `phong`:_

![image](https://github.com/CUNGVANTHANG/Java_Back-end/assets/96326479/262e0a16-2b24-4e10-9bb2-0115bcea540e)

```sql
-- Phòng có 2 giường dành cho 2 sinh viên, hiển thị cột sinh_vien_1, sinh_vien_2, số phòng 
SELECT 
  s1.ten AS sinh_vien_1,
  s2.ten AS sinh_vien_2,
  so_phong
FROM sinh_vien AS s1
INNER JOIN sinh_vien s2
  ON s1.ma_phong = s2.ma_phong
INNER JOIN phong
  ON s1.ma_phong = phong.id
WHERE giuong = 2
  AND s1.ten < s2.ten;
```

<img src="https://github.com/CUNGVANTHANG/Java_Back-end/assets/96326479/450009ea-fc9e-4572-8f22-dae38b5119f6">

## VI. Truy vấn con
[:arrow_up: Mục lục](#mục-lục)
### 1. Truy vấn con `()`
[:arrow_up: Mục lục](#mục-lục)

_Ví dụ:_ Muốn tìm các thành phố có điểm xếp hạng bằng thành phố Paris.

```sql
SELECT danh_gia
FROM thanh_pho
WHERE ten = 'Paris';
```

kết quả của truy vấn trên trong ghi chú (điểm xếp hạng là 5) và sau đó tạo một truy vấn mới:

```sql
SELECT ten
FROM thanh_pho
WHERE danh_gia = 5;
```

**Truy vấn con** được sử dụng để hỗ trợ các trường hợp trên. Chúng là **truy vấn trong truy vấn** và luôn được đặt trong dấu ngoặc đơn `()`.

```sql
SELECT ten
FROM thanh_pho
WHERE danh_gia = (
  SELECT
    danh_gia
  FROM thanh_pho
  WHERE ten = 'Paris'
);
```

_Chú ý:_ Các ví dụ trên truy vấn con trả về một giá trị. Nếu trả về **hai hay nhiều giá trị (tập hợp)** thì ta phải sử dụng toán tử ở dưới đây

### 2. So sánh giá trị với giá trị trong tập hợp `IN`
[:arrow_up: Mục lục](#mục-lục)

Ở phần 1, truy vấn con chỉ trả về một giá trị duy nhất (như 5 hoặc 15.28). Nếu chúng ta muốn trả về nhiều giá trị hơn thì cần làm thế nào?

```sql
SELECT *
FROM thanh_pho
WHERE danh_gia IN (3, 4, 5);
```

Sử dụng toán tử `IN`. Nó cho phép ta chỉ định một vài giá trị trong mệnh đề `WHERE` thay vì chỉ một giá trị.

Trong ví dụ này, ta chỉ muốn hiển thị các thành phố có điểm xếp hạng cao, tuy nhiên, điểm xếp hạng không cần phải là cao nhất - bất kỳ thành phố nào có điểm xếp hạng là 3 `OR` 4 `OR` 5 đều phù hợp. Đó chính là ý nghĩa của `IN (3,4,5)`

_Ví dụ:_ 

```sql
SELECT gia
FROM chuyen_di
WHERE ma_thanh_pho IN (
  SELECT id
  FROM thanh_pho
  WHERE dan_so < 2000000
);
```

Trong truy vấn con, ta tìm ID của tất cả các thành phố có dân số dưới 2 triệu người. Tiếp theo, ta sử dụng những ID này dưới dạng các giá trị cho toán tử `IN`.

Bằng cách này, chúng ta có thể tìm chi phí của những chuyến tham quan đến các thành phố có dân số dưới 2 triệu người.

### 3. So sánh giá trị với tất cả giá trị trong tập hợp `ALL`
[:arrow_up: Mục lục](#mục-lục)

_Ví dụ:_

```sql
SELECT *
FROM quoc_gia
WHERE dien_tich > ALL (
  SELECT dien_tich
  FROM thanh_pho
);
```

`> ALL` có nghĩa là "lớn hơn tất cả các giá trị trong dấu ngoặc đơn".

Kết quả trả về tất cả các quốc gia có **diện tích lớn hơn các thành phố trong dấu ngoặc đơn**. Ví dụ, Liechtenstein là một quốc gia rất nhỏ. Quốc gia này có diện tích lớn hơn một số thành phố (ví dụ như Lyon), nhưng diện tích nhỏ hơn các thành phố còn lại (ví dụ như Berlin), vì vậy Liechtenstein sẽ không được hiển thị trong kết quả.

_Chú ý:_ Các toán tử logic khác: `= ALL`, `!= ALL`, `< ALL`, `<= ALL`, `>= ALL`.

### 4. So sánh giá trị với ít nhất một giá trị trong tập hợp `ANY`
[:arrow_up: Mục lục](#mục-lục)

_Ví dụ:_

```sql
SELECT *
FROM chuyen_di
WHERE gia < ANY (
  SELECT gia
  FROM goi_leo_nui
  WHERE ma_ngon_nui = 1
);
```

`< ANY` có nghĩa là "nhỏ hơn ít nhất một giá trị trong dấu ngoặc đơn"

Tìm các chuyến tham quan đến các thành phố có chi phí rẻ hơn chi phí của bất kỳ chuyến leo núi nào đến ngọn núi có id 1 (Mont Blanc).

Có hai chuyến leo núi đến Mont Blanc: một chuyến có giá 1000 và một chuyến có giá 300. Nếu chúng ta tìm thấy một chuyến tham quan đến thành phố có chi phí rẻ hơn bất kỳ một trong những giá trị này, chúng ta hiển thị nó trong kết quả.

_Chú ý:_ Toán tử logic khác: `= ANY`, `!= ANY`, `< ANY`, `<= ANY`, `>= ANY`.

### 5. Truy vấn con tương quan 
[:arrow_up: Mục lục](#mục-lục)

Bình thường chúng ta chỉ sử dụng các **truy vấn con độc lập với truy vấn chính** - bạn có thể chạy truy vấn con trước và sau đó đưa kết quả vào truy vấn chính.

Bây giờ chúng ta sẽ tìm hiểu về các truy vấn con. Các **truy vấn này sẽ phụ thuộc vào truy vấn chính** và chúng được gọi là **truy vấn con tương quan**.

_Ví dụ:_

```sql
SELECT *
FROM quoc_gia
WHERE dien_tich <= (
  SELECT MIN(dien_tich)
  FROM thanh_pho
  WHERE thanh_pho.ma_quoc_gia = quoc_gia.id
);
```

Chúng ta muốn tìm kiếm tất cả các quốc gia có diện tích nhỏ hơn hoặc bằng diện tích của thành phố nhỏ nhất trong chính quốc gia đó. Nói cách khác, nếu một quốc gia có diện tích nhỏ hơn thành phố nhỏ nhất của nó, nó sẽ được hiển thị. Tại sao chúng ta lại sử dụng một truy vấn như vậy? Vì nó rất hữu ích khi chúng ta cần kiểm tra xem cơ sở dữ liệu có bất kỳ lỗi nào hay không. **Nếu truy vấn này trả về bất kỳ kết quả nào khác, chúng ta biết rằng có điều gì đó không ổn với các bản ghi dữ liệu.**

Nội dung mới ở đây là gì? Hãy quan sát mệnh đề `WHERE` trong truy vấn con. Nó sử dụng `quoc_gia.id`. Quốc gia mà nó tham chiếu đến là quốc gia từ **truy vấn chính**. Đây là cơ chế đằng sau truy vấn con tương quan - nếu bạn chạy truy vấn con một mình, cơ sở dữ liệu sẽ thông báo:

"Bạn muốn tôi so sánh `thanh_pho.ma_quoc_gia` với `quoc_gia.id`, nhưng bảng `quoc_gia` có rất nhiều `id`, vì vậy tôi không biết chọn `id` nào".

Nhưng nếu bạn chạy câu lệnh như truy vấn con và mệnh đề chính duyệt qua bảng `quoc_gia`, cơ sở dữ liệu sẽ so sánh `quoc_gia.id` từ truy vấn con với `quoc_gia.id` hiện tại từ mệnh đề chính.

_Chú ý:_ **Truy vấn con có thể sử dụng các bảng từ truy vấn chính, nhưng truy vấn chính không thể sử dụng các bảng từ truy vấn con!**

### 6. Đặt bí danh cho bảng với truy vấn con
[:arrow_up: Mục lục](#mục-lục)

_Ví dụ:_

```sql
SELECT *
FROM thanh_pho main_city
WHERE dan_so > (
  SELECT AVG(dan_so)
  FROM thanh_pho average_city
  WHERE average_city.ma_quoc_gia = main_city.ma_quoc_gia
);
```

Trong một quốc gia, chúng ta muốn tìm các thành phố có dân số lớn hơn dân số trung bình của quốc gia đó. Nếu theo cách cũ, chúng ta tìm kiếm thành phố trong truy vấn chính và kiểm tra dân số trung bình cho thành phố trong truy vấn con tương quan. Cùng một **bảng xuất hiện hai lần**, tuy nhiên cách này **không thực sự tối ưu hóa chương trình**.

Đây là lý do tại sao chúng ta **nên sử dụng bí danh cho bảng**. 

**Cách làm như sau:** trong truy vấn con, ta đặt `... FROM thanh_pho average_city ...` và trong truy vấn chính `... FROM thanh_pho main_city`. Ta đặt tên tạm thời mới cho bảng `thanh_pho`, hai tên khác nhau cho truy vấn chính và truy vấn con. Tên tạm thời (còn được gọi là **bí danh**) được đặt sau tên bảng, cách nhau bởi một khoảng trắng. 

_Chú ý:_ Không có dấu phẩy ở đây, hãy ghi nhớ điều này!

### 7. Kiểm tra tập hợp con có chứa bất kỳ dòng dữ liệu `EXISTS`
[:arrow_up: Mục lục](#mục-lục)

_Ví dụ:_

```sql
SELECT *
FROM thanh_pho
WHERE EXISTS (
  SELECT *
  FROM trip
  WHERE ma_thanh_pho = thanh_pho.id
);
```

`EXISTS` kiểm tra xem có bất kỳ hàng nào thỏa mãn điều kiện hay không.

Trong ví dụ, truy vấn này sẽ chỉ hiển thị thông tin của những thành phố có ít nhất một chuyến tham quan (**tồn tại một chuyến tham quan**) được tổ chức bởi công ty du lịch. Các thành phố không tổ chức chuyến tham quan nào sẽ không được hiển thị.

### 8. Truy vấn con trong mệnh đề `FROM`
[:arrow_up: Mục lục](#mục-lục)

_Ví dụ:_

```sql
SELECT *
FROM thanh_pho, (
    SELECT
      *
    FROM quoc_gia
    WHERE dien_tich < 1000) AS quoc_gia_nho
WHERE quoc_gia_nho.id = thanh_pho.ma_quoc_gia;
```

Truy vấn trên tìm các thành phố từ các **quốc gia nhỏ**. Bảng `quoc_gia_nho` không có trong cơ sở dữ liệu, vì vậy... chúng ta tạo nó "tạm thời" bằng một truy vấn con trong mệnh đề `FROM`. Tất nhiên, ta cần đặt tên cho nó, vì vậy ta tạo một bí danh với từ khóa `AS`. 

Cuối cùng, truy vấn hiển thị các thành phố cùng với quốc gia tương ứng, miễn là quốc gia có diện tích dưới 1.000 (km2). Bạn có nhớ cách chọn dữ liệu từ hai bảng không? Chúng ta cần viết điều kiện trong mệnh đề `WHERE`, nếu không mỗi thành phố sẽ được hiển thị cùng với tất cả các quốc gia phù hợp.

### 9. Truy vấn con trong mệnh đề `SELECT`
[:arrow_up: Mục lục](#mục-lục)

Truy vấn con cũng có thể được sử dụng trong danh sách cột trong mệnh đề `SELECT`. Quan trọng là **truy vấn con trả về chính xác một hàng và một cột**.

_Ví dụ:_

```sql
SELECT
  name,
  (
    SELECT COUNT(*)
    FROM trip
    WHERE city_id = city.id) AS trip_count
FROM city;
```

Trong truy vấn trên, chúng ta cung cấp tên của mỗi thành phố cùng với số lượng chuyến tham quan cho thành phố đó. Lưu ý rằng chúng ta sử dụng hàm `COUNT()` để đếm số chuyến tham quan đến mỗi thành phố.