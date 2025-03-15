# CON TRỎ TRONG C

## MỤC LỤC

1. [TỔNG QUAN](#tổng-quan)

   - [KHÁI NIỆM VỀ CON TRỎ](#khái-niệm-về-con-trỏ)
   - [CÁCH HIỂU TRỰC QUAN VỀ CON TRỎ](#cách-hiểu-trực-quan-về-con-trỏ)

2. [CƠ BẢN VỀ CON TRỎ](#cơ-bản-về-con-trỏ)

   - [KHAI BÁO VÀ SỬ DỤNG CON TRỎ](#khai-báo-và-sử-dụng-con-trỏ)
   - [TOÁN TỬ & VÀ \* TRONG CON TRỎ](#toán-tử--và--trong-con-trỏ)
   - [VÍ DỤ MINH HỌA CON TRỎ](#ví-dụ-minh-họa-con-trỏ)
   - [PHÂN TÍCH ĐOẠN MÃ](#phân-tích-đoạn-mã)

3. [CON TRỎ VÀ MẢNG](#con-trỏ-và-mảng)

   - [TRUY XUẤT PHẦN TỬ MẢNG BẰNG CON TRỎ](#truy-xuất-phần-tử-mảng-bằng-con-trỏ)
   - [DUYỆT MẢNG BẰNG CON TRỎ](#duyệt-mảng-bằng-con-trỏ)
   - [SỬ DỤNG CON TRỎ ĐỂ CẬP NHẬT GIÁ TRỊ MẢNG](#sử-dụng-con-trỏ-để-cập-nhật-giá-trị-mảng)
   - [TRUYỀN MẢNG VÀO HÀM BẰNG CON TRỎ](#truyền-mảng-vào-hàm-bằng-con-trỏ)
   - [TÓM TẮT VỀ CON TRỎ VÀ MẢNG](#tóm-tắt-về-con-trỏ-và-mảng)

4. [LƯU Ý VÀ MẸO KHI SỬ DỤNG CON TRỎ](#lưu-ý-và-mẹo-khi-sử-dụng-con-trỏ)
   - [KHỞI TẠO CON TRỎ TRƯỚC KHI SỬ DỤNG](#khởi-tạo-con-trỏ-trước-khi-sử-dụng)
   - [TRÁNH TRUY CẬP VÙNG NHỚ NGOÀI PHẠM VI](#tránh-truy-cập-vùng-nhớ-ngoài-phạm-vi)
   - [SỬ DỤNG CON TRỎ NULL MỘT CÁCH CẨN THẬN](#sử-dụng-con-trỏ-null-một-cách-cẩn-thận)
   - [GIẢI PHÓNG BỘ NHỚ ĐỘNG SAU KHI SỬ DỤNG](#giải-phóng-bộ-nhớ-động-sau-khi-sử-dụng)
   - [THẬN TRỌNG VỚI CON TRỎ VOID](#thận-trọng-với-con-trỏ-void)
   - [SỬ DỤNG CON TRỎ HẰNG ĐỂ BẢO VỆ DỮ LIỆU](#sử-dụng-con-trỏ-hằng-để-bảo-vệ-dữ-liệu)
   - [TRÁNH SỬ DỤNG CON TRỎ SAU KHI GIẢI PHÓNG BỘ NHỚ](#tránh-sử-dụng-con-trỏ-sau-khi-giải-phóng-bộ-nhớ)
   - [SỬ DỤNG CON TRỎ ĐÔI MỘT CÁCH HỢP LÝ](#sử-dụng-con-trỏ-đôi-một-cách-hợp-lý)

---

# TỔNG QUAN

## KHÁI NIỆM VỀ CON TRỎ

Trong ngôn ngữ lập trình C, con trỏ (pointer) là một biến đặc biệt có khả năng lưu trữ địa chỉ của một biến khác thay vì lưu trữ trực tiếp giá trị. Mỗi biến trong C đều được cấp phát một vùng nhớ, và con trỏ giúp chúng ta thao tác trực tiếp với địa chỉ của vùng nhớ đó.

## CÁCH HIỂU TRỰC QUAN VỀ CON TRỎ

- Hãy hình dung mỗi biến trong C như một ngôi nhà, và mỗi ngôi nhà đều có số nhà (địa chỉ bộ nhớ).
  - Khi khai báo một biến thông thường, ta đang xây một ngôi nhà mới với số nhà riêng và chứa một giá trị bên trong.
  - Con trỏ giống như một người trung gian biết địa chỉ của một ngôi nhà nào đó.
  - Khi có số nhà (địa chỉ), ta có thể đến thẳng đó để xem hoặc thay đổi nội thất bên trong (giá trị của biến gốc).
  - Mọi thay đổi thông qua con trỏ sẽ ảnh hưởng trực tiếp đến ngôi nhà mà nó trỏ đến.

# CƠ BẢN VỀ CON TRỎ

## KHAI BÁO VÀ SỬ DỤNG CON TRỎ

Con trỏ thường được khai báo với một kiểu dữ liệu cụ thể, nghĩa là nó chỉ có thể trỏ đến các biến cùng kiểu, giúp đảm bảo tính nhất quán khi truy xuất dữ liệu.

```c
int a = 10;   // Biến thông thường
int *p = &a;  // Con trỏ lưu địa chỉ của biến a
*p = 20;      // Thay đổi giá trị của a thông qua con trỏ
```

## TOÁN TỬ `&` VÀ `*` TRONG CON TRỎ

- `&` (địa chỉ): Lấy địa chỉ của một biến.
- `*` (dereference): Truy cập giá trị tại địa chỉ mà con trỏ trỏ đến.
- `*` còn dùng để khai báo và khởi tạo con trỏ.

## VÍ DỤ MINH HỌA CON TRỎ

```c
#include <stdio.h>

int main() {
    int houseValue = 100; // Ngôi nhà có giá trị 100
    int* housePointer = &houseValue; // Người trung gian nhớ địa chỉ ngôi nhà

    printf("Địa chỉ của houseValue: %p\n", &houseValue);
    printf("Giá trị của housePointer (địa chỉ mà nó lưu trữ): %p\n", housePointer);

    // Xem giá trị của ngôi nhà thông qua con trỏ
    printf("Giá trị của ngôi nhà thông qua con trỏ: %d\n", *housePointer);

    // Thay đổi giá trị ngôi nhà thông qua con trỏ
    *housePointer = 200;
    printf("Giá trị mới của ngôi nhà: %d\n", houseValue);

    // Con trỏ NULL - Chưa trỏ đến đâu
    int* unknownHouse = NULL;
    printf("Giá trị của unknownHouse: %p\n", unknownHouse);

    // Con trỏ void - Có thể trỏ đến bất kỳ kiểu dữ liệu nào
    void* generalPointer = &houseValue;
    printf("Địa chỉ lưu trong generalPointer: %p\n", generalPointer);

    return 0;
}
```

## PHÂN TÍCH ĐOẠN MÃ

- `&houseValue` lấy địa chỉ của biến `houseValue`.
- `housePointer` lưu địa chỉ của `houseValue`.
- `*housePointer` lấy giá trị tại địa chỉ mà nó trỏ đến.
- Khi thay đổi `*housePointer`, giá trị của `houseValue` cũng thay đổi theo.
- `*` còn có tác dụng khai báo và khởi tạo con trỏ (`int* housePointer`).
- In ra địa chỉ bộ nhớ giúp hiểu rõ cách con trỏ hoạt động trong thực tế.

# CON TRỎ VÀ MẢNG

## TRUY XUẤT PHẦN TỬ MẢNG BẰNG CON TRỎ

```c
int arr[3] = {10, 20, 30};
int *p = arr; // Con trỏ trỏ đến mảng

// Truy cập phần tử mảng bằng con trỏ
printf("%d\n", *p);     // In ra 10
printf("%d\n", *(p+1)); // In ra 20
printf("%d\n", *(p+2)); // In ra 30
```

## DUYỆT MẢNG BẰNG CON TRỎ

```c
int arr[5] = {1, 2, 3, 4, 5};
int *p = arr;

for (int i = 0; i < 5; i++) {
    printf("%d ", *(p + i)); // Truy cập từng phần tử qua con trỏ
}
```

## SỬ DỤNG CON TRỎ ĐỂ CẬP NHẬT GIÁ TRỊ MẢNG

```c
int arr[3] = {1, 2, 3};
int *p = arr;
*p = 10;      // arr[0] = 10
*(p+1) = 20;  // arr[1] = 20
*(p+2) = 30;  // arr[2] = 30
```

## TRUYỀN MẢNG VÀO HÀM BẰNG CON TRỎ

```c
void printArray(int *p, int size) {
    for (int i = 0; i < size; i++) {
                printf("%d ", *(p + i));
    }
}

int main() {
    int arr[4] = {5, 10, 15, 20};
    printArray(arr, 4);
    return 0;
}
```

## TÓM TẮT VỀ CON TRỎ VÀ MẢNG

- Tên mảng là con trỏ hằng trỏ đến phần tử đầu tiên.
- `p + i` dịch chuyển con trỏ để truy cập phần tử tiếp theo.
- Có thể truyền mảng vào hàm dưới dạng con trỏ.
- Có thể cập nhật giá trị mảng thông qua con trỏ.

Con trỏ giúp truy xuất mảng linh hoạt và hiệu quả hơn so với cách dùng chỉ số thông thường!

# LƯU Ý VÀ MẸO KHI SỬ DỤNG CON TRỎ

Việc sử dụng con trỏ trong lập trình C mang lại nhiều lợi ích, nhưng cũng tiềm ẩn rủi ro nếu không cẩn thận. Dưới đây là một số lưu ý và mẹo quan trọng:

## KHỞI TẠO CON TRỎ TRƯỚC KHI SỬ DỤNG

- Khởi tạo con trỏ ngay khi khai báo: Tránh việc sử dụng con trỏ chưa được khởi tạo, vì chúng có thể trỏ đến vùng nhớ không xác định, gây ra lỗi không mong muốn.

```c
int *p = NULL; // Khởi tạo con trỏ với giá trị NULL
```

- Gán địa chỉ hợp lệ cho con trỏ trước khi sử dụng: Đảm bảo con trỏ trỏ đến một biến hoặc vùng nhớ hợp lệ trước khi thao tác.

## TRÁNH TRUY CẬP VÙNG NHỚ NGOÀI PHẠM VI

- Không truy cập ngoài phạm vi mảng: Khi sử dụng con trỏ để duyệt mảng, đảm bảo không vượt quá giới hạn của mảng để tránh lỗi truy cập bộ nhớ.

```c
int arr[5] = {1, 2, 3, 4, 5};
int *p = arr;
for (int i = 0; i < 5; i++) {
    printf("%d ", *(p + i)); // Truy cập hợp lệ trong phạm vi mảng
}
```

## SỬ DỤNG CON TRỎ NULL MỘT CÁCH CẨN THẬN

- Kiểm tra con trỏ NULL trước khi sử dụng: Trước khi truy cập giá trị thông qua con trỏ, luôn kiểm tra xem con trỏ có trỏ đến NULL hay không để tránh lỗi runtime.

```c
int *p = NULL;
if (p != NULL) {
          // Thao tác với con trỏ
} else {
          // Xử lý khi con trỏ là NULL
}
```

## GIẢI PHÓNG BỘ NHỚ ĐỘNG SAU KHI SỬ DỤNG

- Sử dụng free() để giải phóng bộ nhớ: Khi sử dụng hàm malloc() hoặc calloc() để cấp phát bộ nhớ động, hãy chắc chắn giải phóng bộ nhớ sau khi sử dụng để tránh rò rỉ bộ nhớ.

```c
int *p = (int *)malloc(sizeof(int) * 10);
// Sử dụng bộ nhớ
free(p); // Giải phóng bộ nhớ
```

## THẬN TRỌNG VỚI CON TRỎ VOID

- Con trỏ void có thể trỏ đến bất kỳ kiểu dữ liệu nào: Tuy nhiên, cần ép kiểu phù hợp trước khi dereference để đảm bảo an toàn và chính xác.

```c
void *p;
int a = 10;
p = &a;
printf("%d\n", *(int *)p); // Ép kiểu trước khi truy cập giá trị
```

## SỬ DỤNG CON TRỎ HẰNG ĐỂ BẢO VỆ DỮ LIỆU

- Con trỏ hằng (const pointer): Ngăn chặn việc thay đổi giá trị mà con trỏ trỏ đến, giúp bảo vệ dữ liệu không bị sửa đổi ngoài ý muốn.

```c
const int *p = &a;
// *p = 20; // Lỗi: không thể thay đổi giá trị thông qua con trỏ hằng
```

## TRÁNH SỬ DỤNG CON TRỎ SAU KHI GIẢI PHÓNG BỘ NHỚ

- Không sử dụng con trỏ sau khi đã giải phóng: Sau khi gọi free() trên một con trỏ, không nên tiếp tục sử dụng con trỏ đó để tránh lỗi truy cập bộ nhớ.

```c
int *p = (int *)malloc(sizeof(int));
free(p);
// *p = 10; // Lỗi: sử dụng con trỏ sau khi giải phóng
```

## SỬ DỤNG CON TRỎ ĐÔI MỘT CÁCH HỢP LÝ

- Con trỏ đôi cho phép quản lý con trỏ cấp thấp hơn: Tuy nhiên, cần hiểu rõ cách hoạt động để tránh nhầm lẫn và lỗi khó phát hiện.

```c
int a = 10;
int *p = &a;
int **pp = &p;
printf("%d\n", **pp); // In ra 10
```
