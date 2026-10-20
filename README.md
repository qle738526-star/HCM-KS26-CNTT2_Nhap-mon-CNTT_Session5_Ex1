# HCM-KS26-CNTT2_Nhap-mon-CNTT_Session5_Ex1
# Báo Cáo: Phân Tích & Khắc Phục Lỗi PowerShell

## Phần 1: Phân Tích Lỗi

**1. Lỗi không bọc dấu ngoặc kép tên thư mục có khoảng trắng **
*   **Nguyên nhân:** Lệnh `mkdir Shopee Projects` không bọc chuỗi trong dấu ngoặc kép `""`. PowerShell phân tách các tham số bằng khoảng trắng nên sẽ hiểu `Shopee` và `Projects` là hai tham số riêng lẻ.
*   **Hậu quả:** Hệ thống tạo ra hai thư mục độc lập tên là `Shopee` và `Projects` thay vì một thư mục `Shopee Projects`.

**2. Lỗi dư tham số vị trí do chứa khoảng trắng **
*   **Nguyên nhân:** Lệnh `cd Shopee Projects` chỉ nhận một tham số đường dẫn đích, nhưng việc không bọc ngoặc kép làm cho từ `Projects` trở thành một tham số vị trí thứ hai dư thừa.
*   **Thông báo lỗi:** `A positional parameter cannot be found that accepts argument 'Projects'.` (PowerShell báo lỗi do nhận được một tham số vị trí nằm ngoài định dạng của lệnh `cd`).

**3. Lỗi thao tác trên đường dẫn không tồn tại **
*   **Nguyên nhân:** Do thư mục `Shopee Projects` không được tạo thành công ở Lệnh 1, các thao tác chuyển thư mục, tạo thư mục con hay sao chép đệ quy ở các lệnh sau đều trỏ vào một đường dẫn chưa từng xuất hiện trên hệ thống.
*   **Thông báo lỗi:** `Cannot find path '...' because it does not exist.`.


## Phần 2: Hoàn Thiện

Chuỗi 3 dòng lệnh PowerShell chuẩn xác để thực hiện cấu trúc thư mục:

mkdir "Shopee Projects"; cd "Shopee Projects"

mkdir "src\assets\images"

Copy-Item "src" -Destination "src-backup" -Recurse
