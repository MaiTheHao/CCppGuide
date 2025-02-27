# Mảng trong C

Mảng là một cấu trúc dữ liệu cho phép lưu trữ nhiều giá trị trong một biến duy nhất, tương tự như một danh sách mua sắm chứa nhiều món hàng.

## Khai báo mảng

Trong C, để khai báo một mảng, bạn cần chỉ rõ **kiểu dữ liệu** của các phần tử và **số lượng phần tử** mà mảng sẽ chứa. Tuy nhiên, cách khai báo mảng có thể thay đổi tùy thuộc vào phiên bản tiêu chuẩn C mà bạn sử dụng.

### Cú pháp cơ bản

```c
kiểu_dữ_liệu tên_mảng[kích_thước];
```

Ví dụ:
```c
int numbers[5]; // Mảng 5 phần tử kiểu int
```

### Khai báo và khởi tạo mảng

Bạn có thể khởi tạo mảng ngay khi khai báo:

```c
int numbers[5] = {1, 2, 3, 4, 5}; // Khai báo và khởi tạo mảng
```

Nếu không chỉ định kích thước nhưng có khởi tạo, compiler sẽ tự động xác định kích thước:

```c
int numbers[] = {1, 2, 3, 4, 5}; // Kích thước mảng là 5
```

### Sự khác biệt giữa các chuẩn C

#### Trong C89/C90 (chuẩn cũ)
- Kích thước mảng **phải là hằng số** tại thời điểm biên dịch (compile-time constant)
- Không thể sử dụng biến để khai báo kích thước mảng

```c
#define SIZE 5
int numbers[SIZE]; // Hợp lệ, SIZE là hằng số

int size = 5;
int array[size]; // Không hợp lệ trong C89/C90
```

#### Từ C99 trở lên
- Hỗ trợ **mảng có kích thước biến động** (Variable Length Array - VLA)
- Có thể sử dụng biến để xác định kích thước mảng

```c
int size = 5;
int array[size]; // Hợp lệ từ C99 trở lên
```

### Lưu ý quan trọng
- VLA không thể khởi tạo giá trị ngay khi khai báo
- VLA chỉ tồn tại trong phạm vi của khối mã khai báo nó
- Nhiều trình biên dịch hiện đại mặc định sử dụng chuẩn C99 hoặc mới hơn
- Nếu quan tâm đến tính tương thích, nên sử dụng cách khai báo theo C89/C90

## Truy cập phần tử của mảng

Để truy cập một phần tử trong mảng, bạn sử dụng chỉ số của phần tử đó. Chỉ số bắt đầu từ 0:

<p align="center">
    <img src="../../Imgs/array_index.jpg" alt="Ảnh lưu đồ của for loop" height="200"/>
</p>

```c
int numbers[5] = {1, 3, 5, 7, 9};
int firstElement = numbers[0]; // 1
int secondElement = numbers[1]; // 3
```

## Thay đổi giá trị của phần tử mảng

Bạn có thể thay đổi giá trị của một phần tử trong mảng bằng cách gán giá trị mới cho nó:

```c
int numbers[5] = {1, 3, 5, 7, 9};
numbers[0] = 10; 
// numbers = {10, 3, 5, 7, 9}
```

## Lặp qua các phần tử của mảng

Bạn có thể sử dụng vòng lặp `for` để duyệt qua các phần tử của mảng:

```c
for (int i = 0; i < 5; i++) {
  printf("%d\n", numbers[i]);
}
```

## Nhập dữ liệu cho mảng

Bạn có thể sử dụng vòng lặp `for` để nhập dữ liệu cho mảng từ bàn phím:

```c
for (int i = 0; i < 5; i++) {
  scanf("%d", &numbers[i]);
}
```

## Ví dụ về mảng

### Ví dụ 1: Khai báo và khởi tạo mảng

```c
#include <stdio.h>

int main() {
  int numbers[5] = {1, 2, 3, 4, 5}; // Khai báo và khởi tạo mảng

  // In các phần tử của mảng
  for (int i = 0; i < 5; i++) {
    printf("%d ", numbers[i]);
  }

  return 0;
}
```

### Ví dụ 2: Nhập và in các phần tử của mảng

```c
#include <stdio.h>

int main() {
  int numbers[5];

  // Nhập dữ liệu cho mảng
  for (int i = 0; i < 5; i++) {
    printf("Nhập phần tử thứ %d: ", i + 1);
    scanf("%d", &numbers[i]);
  }

  // In các phần tử của mảng
  printf("Các phần tử của mảng: ");
  for (int i = 0; i < 5; i++) {
    printf("%d ", numbers[i]);
  }

  return 0;
}
```

### Ví dụ 3: Tính tổng các phần tử của mảng

```c
#include <stdio.h>

int main() {
  int numbers[5] = {1, 2, 3, 4, 5};
  int sum = 0;

  // Tính tổng các phần tử của mảng
  for (int i = 0; i < 5; i++) {
    sum += numbers[i];
  }

  printf("Tổng các phần tử của mảng: %d\n", sum);

  return 0;
}
```

### Ví dụ 4: Tìm phần tử lớn nhất trong mảng

```c
#include <stdio.h>

int main() {
  int numbers[5] = {1, 2, 3, 4, 5};
  int max = numbers[0];

  // Tìm phần tử lớn nhất trong mảng
  for (int i = 1; i < 5; i++) {
    if (numbers[i] > max) {
      max = numbers[i];
    }
  }

  printf("Phần tử lớn nhất trong mảng: %d\n", max);

  return 0;
}
```

## Mảng đa chiều

Mảng đa chiều, còn được gọi là ma trận (matrix), là một mảng chứa các mảng khác bên trong nó. Mảng đa chiều phổ biến nhất là mảng hai chiều (2D), thường được sử dụng để lưu trữ dữ liệu dưới dạng bảng với các hàng và cột.

### Khai báo mảng đa chiều
Trong C, mảng n chiều là một cấu trúc dữ liệu mà mỗi chiều được biểu diễn bằng một cặp dấu ngoặc vuông `[]`. Cú pháp tổng quát để khai báo mảng n chiều như sau:

```c
// Đây là mảng 2 chiều có 3 hàng và 3 cột:
int matrix[3][3];

// Đây là mảng 3 chiều có 2 phần tử, mỗi phần tử là một ma trận 3x3:
int threeDArray[2][3][3];

// Đây là mảng 4 chiều có 2 phần tử, mỗi phần tử là một mảng 3 chiều:
int fourDArray[2][3][3][3];
```

### Khởi tạo mảng đa chiều

Bạn có thể khai báo và khởi tạo mảng đa chiều ngay khi khai báo:

```c
int matrix[3][3] = {
  {1, 2, 3},
  {4, 5, 6},
  {7, 8, 9}
};
```

### Truy cập phần tử của mảng đa chiều

Để truy cập một phần tử trong mảng đa chiều, bạn sử dụng chỉ số của hàng và cột:

```c
int firstElement = matrix[0][0]; // Phần tử ở hàng đầu tiên, cột đầu tiên
int secondElement = matrix[1][1]; // Phần tử ở hàng thứ hai, cột thứ hai
```

### Lặp qua các phần tử của mảng đa chiều

Bạn có thể sử dụng hai vòng lặp `for` lồng nhau để duyệt qua các phần tử của mảng đa chiều:

```c
for (int i = 0; i < 3; i++) {
  for (int j = 0; j < 3; j++) {
    printf("%d ", matrix[i][j]);
  }
  printf("\n");
}
```

### Ví dụ về mảng đa chiều

Dưới đây là ví dụ về mảng đa chiều:

```c
#include <stdio.h>

int main() {
  int matrix[3][3] = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
  };

  // In các phần tử của mảng
  for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 3; j++) {
      printf("%d ", matrix[i][j]);
    }
    printf("\n");
  }

  return 0;
}
```

Giải thích:
- Kích thước của ma trận là 3x3.
- Vòng lặp ngoài duyệt qua các hàng của ma trận.
- Vòng lặp bên trong duyệt qua các cột của ma trận.
- In ra các phần tử của ma trận theo hàng và cột.

Trong ví dụ trên, chúng ta khai báo một ma trận 3x3 và in các phần tử của nó ra.

## Mảng và con trỏ

Mảng trong C được lưu trữ dưới dạng một dãy các phần tử liên tiếp trong bộ nhớ. Mỗi phần tử của mảng có một địa chỉ riêng, và bạn có thể sử dụng con trỏ để truy cập các phần tử của mảng.

> **Lưu ý:** Để hiểu rõ hơn về mảng và con trỏ, bạn cần có kiến thức về con trỏ. Hãy đảm bảo bạn đã học về con trỏ trước khi tiếp tục phần này.

### Con trỏ và mảng

Khi bạn khai báo một mảng, tên của mảng là một con trỏ trỏ tới phần tử đầu tiên của mảng:

```c
int numbers[5] = {1, 2, 3, 4, 5};
int *ptr = numbers; // ptr trỏ tới phần tử đầu tiên của mảng
```

### Truy cập phần tử của mảng bằng con trỏ

Bạn có thể truy cập các phần tử của mảng bằng cách sử dụng con trỏ:

```c
int firstElement = *ptr; // Phần tử đầu tiên của mảng
int secondElement = *(ptr + 1); // Phần tử thứ hai của mảng
```

### Ví dụ về con trỏ và mảng

Dưới đây là ví dụ về việc sử dụng con trỏ để truy cập các phần tử của mảng:

```c
#include <stdio.h>

int main() {
  int numbers[5] = {1, 2, 3, 4, 5};
  int *ptr = numbers;

  // In các phần tử của mảng bằng con trỏ
  for (int i = 0; i < 5; i++) {
    printf("%d ", *(ptr + i));
  }

  return 0;
}
```

## Mảng động

Mảng động là mảng có thể thay đổi kích thước trong quá trình thực thi chương trình. Để sử dụng mảng động, bạn cần sử dụng con trỏ và các hàm cấp phát bộ nhớ động như `malloc`, `calloc`, và `realloc`.

> **Lưu ý:** Để hiểu rõ hơn về mảng động, bạn cần có kiến thức về con trỏ. Hãy đảm bảo bạn đã học về con trỏ trước khi tiếp tục phần này.

### Khai báo và cấp phát bộ nhớ cho mảng động

Để khai báo và cấp phát bộ nhớ cho mảng động, bạn sử dụng hàm `malloc` hoặc `calloc`:

```c
int *numbers;
numbers = (int *)malloc(5 * sizeof(int)); // Cấp phát bộ nhớ cho mảng 5 phần tử
```

### Truy cập và thay đổi giá trị của mảng động

Bạn truy cập và thay đổi giá trị của mảng động giống như mảng tĩnh:

```c
numbers[0] = 10; // Thay đổi giá trị phần tử đầu tiên
int firstElement = numbers[0]; // Truy cập phần tử đầu tiên
```

### Giải phóng bộ nhớ của mảng động

Sau khi sử dụng xong mảng động, bạn cần giải phóng bộ nhớ đã cấp phát để tránh rò rỉ bộ nhớ:

```c
free(numbers); // Giải phóng bộ nhớ
```

### Ví dụ minh họa

Dưới đây là ví dụ minh họa về việc sử dụng mảng động:

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
  int *numbers;
  numbers = (int *)malloc(5 * sizeof(int)); // Cấp phát bộ nhớ cho mảng 5 phần tử

  // Nhập dữ liệu cho mảng
  for (int i = 0; i < 5; i++) {
    numbers[i] = i + 1;
  }

  // In các phần tử của mảng
  for (int i = 0; i < 5; i++) {
    printf("%d ", numbers[i]);
  }

  // Giải phóng bộ nhớ
  free(numbers);

  return 0;
}
```

## Tổng kết

Trong chương này, bạn đã học cách khai báo, truy cập, thay đổi giá trị, và duyệt qua các phần tử của mảng. Bạn cũng đã học cách nhập dữ liệu cho mảng và thực hiện các thao tác cơ bản như tính tổng và tìm phần tử lớn nhất. Ngoài ra, bạn đã được giới thiệu sơ lược về mảng động và cách triển khai chúng.

## Bài tập thực hành

1. Khai báo một mảng gồm 10 số nguyên và nhập giá trị cho từng phần tử từ bàn phím. In ra các phần tử của mảng.
2. Viết chương trình tính trung bình cộng của các phần tử trong mảng.
3. Viết chương trình tìm phần tử nhỏ nhất trong mảng.
4. Viết chương trình đảo ngược các phần tử trong mảng.

## Mẹo và lưu ý

- Khi làm việc với mảng, hãy luôn kiểm tra chỉ số của mảng để tránh truy cập ngoài phạm vi mảng.
- Sử dụng vòng lặp `for` để duyệt qua các phần tử của mảng một cách hiệu quả.
- Đối với mảng động, đừng quên giải phóng bộ nhớ sau khi sử dụng để tránh rò rỉ bộ nhớ.
