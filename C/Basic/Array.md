# 🔥 MẢNG TRONG C 🔥

**Mảng** là một cấu trúc dữ liệu quan trọng trong ngôn ngữ lập trình C, cho phép lưu trữ một tập hợp các phần tử có cùng kiểu dữ liệu một cách có tổ chức. Nhờ mảng, việc quản lý, truy cập và xử lý dữ liệu trở nên hiệu quả hơn, giúp tối ưu hóa hiệu suất chương trình. Hiểu rõ cách sử dụng mảng là điều cần thiết trong lập trình, vì chúng không chỉ giúp sắp xếp dữ liệu khoa học mà còn cải thiện tốc độ xử lý.

> **Lưu ý quan trọng**: Trong C, mảng có mối quan hệ chặt chẽ với con trỏ. Thực chất, tên mảng chính là địa chỉ của phần tử đầu tiên trong mảng và có thể được xem như một con trỏ hằng.

---

# 📌 1. KHAI BÁO VÀ KHỞI TẠO MẢNG

Mảng có thể được khai báo với số lượng phần tử cố định hoặc sử dụng cấp phát động để tạo mảng linh hoạt hơn.

## **Cú pháp khai báo mảng một chiều**

```c
kiểu_dữ_liệu tên_mảng[kích_thước];
```

**Ví dụ:**

```c
int numbers[5]; // Mảng gồm 5 phần tử kiểu int
```

> **Tip**: Bạn có thể khởi tạo mảng ngay lúc khai báo:

```c
int numbers[5] = {1, 2, 3, 4, 5};
```

> **Lưu ý**: Nếu không chỉ định kích thước nhưng có khởi tạo giá trị, trình biên dịch sẽ tự động xác định kích thước:

```c
int numbers[] = {1, 2, 3, 4, 5}; // Mảng có kích thước 5
```

Có thể khởi tạo tất cả phần tử về giá trị 0:

```c
int numbers[5] = {0}; // Tất cả phần tử là 0
```

---

# ⚠️ 2. SỰ KHÁC BIỆT GIỮA C89/C90 VÀ C99+ ⚠️

## **Trước C99 (C89/C90)**

> **Hạn chế**:
>
> - Kích thước mảng **phải là một hằng số** xác định tại thời điểm biên dịch
> - Không thể sử dụng biến để khai báo kích thước mảng

**Ví dụ (không hợp lệ trong C89/C90):**

```c
int size = 10;
int array[size]; // Lỗi: không thể sử dụng biến để khai báo kích thước mảng
```

## **Từ C99 trở lên**

> **Cải tiến**:
>
> - Hỗ trợ **mảng có kích thước biến động (VLA - Variable Length Array)**
> - Có thể sử dụng biến để xác định kích thước mảng

**Ví dụ (hợp lệ trong C99+):**

```c
int size = 10;
int array[size]; // Hợp lệ trong C99 trở lên
```

Lưu ý: Một số trình biên dịch có thể không hỗ trợ VLA, vì vậy nếu gặp lỗi, hãy sử dụng **mảng động thay thế**.

---

# 🔄 3. MẢNG ĐA CHIỀU

**Mảng đa chiều** là mảng chứa nhiều mảng con bên trong. Mỗi phần tử trong mảng đa chiều có thể được truy cập bằng nhiều chỉ số.

> **Ví dụ về mảng ba chiều:**

```c
int array3D[2][3][4]; // Mảng 3 chiều với kích thước 2x3x4
```

## **Mảng hai chiều (Matrix)**

**Mảng hai chiều** là trường hợp phổ biến nhất của mảng đa chiều và thường được sử dụng để lưu trữ dữ liệu dạng **ma trận (matrix)**.

## **Khai báo mảng hai chiều**

```c
int matrix[3][3];
```

## **Khởi tạo mảng hai chiều**

```c
int matrix[3][3] = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```

## **Duyệt qua mảng hai chiều**

```c
for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 3; j++) {
        printf("%d ", matrix[i][j]);
    }
    printf("\n");
}
```

---

# 🛠️ 4. MẢNG ĐỘNG

**Mảng động** sử dụng cấp phát bộ nhớ trong thời gian chạy, giúp quản lý kích thước linh hoạt hơn so với mảng tĩnh.

> **Quan trọng**: Luôn nhớ giải phóng bộ nhớ sau khi sử dụng mảng động để tránh rò rỉ bộ nhớ.

## **Cấp phát bộ nhớ động**

```c
int *numbers = (int *)malloc(5 * sizeof(int));
```

## **Giải phóng bộ nhớ**

```c
free(numbers);
```

## **Ví dụ về mảng động**

```c
#include <stdio.h>
#include <stdlib.h>
int main() {
    int n;
    printf("Nhập số phần tử: ");
    scanf("%d", &n);
    int *numbers = (int *)malloc(n * sizeof(int));
    for (int i = 0; i < n; i++) {
        numbers[i] = i + 1;
    }
    for (int i = 0; i < n; i++) {
        printf("%d ", numbers[i]);
    }
    free(numbers);
    return 0;
}
```

---

# 🚀 5. ỨNG DỤNG CỦA MẢNG

**Mảng được sử dụng trong nhiều ứng dụng thực tế như:**

- Xử lý chuỗi và ký tự
- Lưu trữ và xử lý dữ liệu số lớn
- Áp dụng trong thuật toán tìm kiếm và sắp xếp
- Biểu diễn và xử lý ma trận trong đồ họa máy tính
- Quản lý danh sách sinh viên, nhân viên, sản phẩm
- Ứng dụng trong lập trình hệ thống và mô phỏng dữ liệu

---

# 🎯 6. TỔNG KẾT

> **Kết luận**: Mảng là một công cụ mạnh mẽ giúp tổ chức dữ liệu hiệu quả trong lập trình C. Việc hiểu cách khai báo, truy cập, sử dụng vòng lặp để duyệt qua mảng, và quản lý bộ nhớ cho mảng động sẽ giúp bạn viết chương trình tối ưu hơn.

> **Lời khuyên**: Khi làm việc với mảng, hãy luôn chú ý đến:
>
> - Quản lý bộ nhớ cẩn thận
> - Kiểm tra giới hạn mảng
> - Chọn đúng kiểu mảng (tĩnh/động) cho từng bài toán
> - Tối ưu hóa việc truy cập mảng trong vòng lặp
