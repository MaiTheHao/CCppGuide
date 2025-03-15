# MỤC LỤC

1. [LÝ DO CẦN CÓ STRUCT](#1-lý-do-cần-có-struct)
2. [STRUCT LÀ GÌ?](#2-struct-là-gì)
3. [KHAI BÁO STRUCT](#3-khai-báo-struct)
4. [TRUY CẬP THUỘC TÍNH CỦA STRUCT](#4-truy-cập-thuộc-tính-của-struct)
5. [TẠO NHIỀU BIẾN STRUCT KHÁC NHAU](#5-tạo-nhiều-biến-struct-khác-nhau)
6. [XỬ LÝ CHUỖI TRONG STRUCT](#6-xử-lý-chuỗi-trong-struct)
7. [CÚ PHÁP KHAI BÁO NGẮN GỌN HƠN](#7-cú-pháp-khai-báo-ngắn-gọn-hơn)
8. [SAO CHÉP STRUCT](#8-sao-chép-struct)
9. [CHỈNH SỬA GIÁ TRỊ TRONG STRUCT](#9-chỉnh-sửa-giá-trị-trong-struct)
10. [ỨNG DỤNG STRUCT TRONG THỰC TẾ](#10-ứng-dụng-struct-trong-thực-tế)
11. [TỔNG KẾT](#11-tổng-kết)

# 1. LÝ DO CẦN CÓ STRUCT

📝 **Giải thích**  
Trong lập trình C, nếu bạn cần lưu trữ nhiều thông tin có liên quan về một thực thể, bạn có thể sử dụng các biến riêng lẻ. Tuy nhiên, cách làm này sẽ gây khó khăn trong việc quản lý dữ liệu khi số lượng biến tăng lên.

Ví dụ, nếu bạn cần lưu thông tin về một sinh viên, bạn có thể có các biến như:

💻 **Ví dụ**

```c
int studentID;
char studentName[50];
float studentGPA;
```

Nếu cần lưu trữ thông tin của nhiều sinh viên, bạn sẽ phải tạo nhiều bộ biến riêng lẻ, điều này làm cho mã nguồn trở nên cồng kềnh và khó quản lý.

Struct giúp giải quyết vấn đề này bằng cách nhóm các biến liên quan vào một cấu trúc duy nhất, giúp mã nguồn dễ đọc, dễ bảo trì hơn.

📌 **Ghi nhớ**

- Struct giúp nhóm các biến liên quan lại với nhau.
- Giúp mã nguồn dễ đọc và bảo trì hơn.

---

# 2. STRUCT LÀ GÌ?

📝 **Giải thích**  
Struct (còn gọi là struct) là một cách để nhóm nhiều biến có liên quan lại với nhau trong một nơi duy nhất. Mỗi biến trong struct được gọi là một thuộc tính của struct.

Không giống như mảng, một struct có thể chứa nhiều kiểu dữ liệu khác nhau như `int`, `float`, `char`, v.v.

📌 **Ghi nhớ**

- Struct có thể chứa nhiều kiểu dữ liệu khác nhau.
- Mỗi biến trong struct được gọi là một thuộc tính.

---

# 3. KHAI BÁO STRUCT

📝 **Giải thích**  
Bạn có thể tạo một `struct` bằng cách sử dụng từ khóa `struct` và khai báo từng thuộc tính bên trong dấu ngoặc nhọn `{}`:

💻 **Ví dụ**

```c
struct MyStruct {   // Khai báo struct
  int myNum;           // thuộc tính (biến kiểu int)
  char myLetter;       // thuộc tính (biến kiểu char)
}; // Kết thúc struct bằng dấu chấm phẩy
```

Để sử dụng `struct`, bạn cần tạo một biến của nó bằng cách sử dụng từ khóa `struct` trong hàm `main()`:

💻 **Ví dụ**

```c
struct MyStruct {
  int myNum;
  char myLetter;
};

int main() {
  struct MyStruct s1;  // Khai báo biến kiểu struct
  return 0;
}
```

## **Sử dụng `typedef` để đơn giản hóa cú pháp**

📝 **Giải thích**  
Khi khai báo `struct`, bạn thường phải lặp lại từ khóa `struct` mỗi lần tạo biến. Điều này có thể gây bất tiện, đặc biệt khi tên struct dài. Để khắc phục, ta sử dụng `typedef` để tạo một bí danh cho kiểu `struct`, giúp đơn giản hóa cú pháp:

💻 **Ví dụ**

```c
#include <stdio.h>

// Sử dụng typedef để định danh struct mới
typedef struct {
  int myNum;
  char myLetter;
} MyStruct;

int main() {
  MyStruct s1;  // Không cần dùng 'struct' nữa
  s1.myNum = 10;
  s1.myLetter = 'A';

  printf("myNum: %d, myLetter: %c\n", s1.myNum, s1.myLetter);
  return 0;
}
```

📌 **Ghi nhớ**

- `typedef` giúp đơn giản hóa cú pháp khi sử dụng struct.
- Không cần lặp lại từ khóa `struct` mỗi lần tạo biến.

---

# 4. TRUY CẬP THUỘC TÍNH CỦA STRUCT

📝 **Giải thích**  
Để truy cập thuộc tính của một struct, sử dụng cú pháp dấu chấm (`.`):

💻 **Ví dụ**

```c
struct myStruct {
  int myNum;
  char myLetter;
};

int main() {
  struct myStruct s1;

  // Gán giá trị cho các thuộc tính của s1
  s1.myNum = 13;
  s1.myLetter = 'B';

  // In ra giá trị
  printf("My number: %d\n", s1.myNum);
  printf("My letter: %c\n", s1.myLetter);

  return 0;
}
```

📌 **Ghi nhớ**

- Sử dụng dấu chấm (`.`) để truy cập thuộc tính của struct.

---

# 5. TẠO NHIỀU BIẾN STRUCT KHÁC NHAU

📝 **Giải thích**  
Bạn có thể tạo nhiều biến struct khác nhau với các giá trị khác nhau từ một struct duy nhất:

💻 **Ví dụ**

```c
struct myStruct s1;
struct myStruct s2;

s1.myNum = 13;
s1.myLetter = 'B';

s2.myNum = 20;
s2.myLetter = 'C';
```

📌 **Ghi nhớ**

- Có thể tạo nhiều biến struct khác nhau từ một struct duy nhất.

---

# 6. XỬ LÝ CHUỖI TRONG STRUCT

📝 **Giải thích**  
Strings trong C thực chất là một mảng ký tự, và bạn không thể gán giá trị trực tiếp như sau:

💻 **Ví dụ**

```c
struct myStruct {
  int myNum;
  char myLetter;
  char myString[30];
};

int main() {
  struct myStruct s1;
  s1.myString = "Some text";  // Lỗi!
  return 0;
}
```

Để gán giá trị chuỗi, bạn cần sử dụng hàm `strcpy()`:

💻 **Ví dụ**

```c
#include <stdio.h>
#include <string.h>

struct myStruct {
  int myNum;
  char myLetter;
  char myString[30];
};

int main() {
  struct myStruct s1;
  strcpy(s1.myString, "Some text");
  printf("My string: %s", s1.myString);
  return 0;
}
```

📌 **Ghi nhớ**

- Sử dụng `strcpy()` để gán giá trị chuỗi cho thuộc tính của struct.

---

# 7. CÚ PHÁP KHAI BÁO NGẮN GỌN HƠN

📝 **Giải thích**  
Bạn có thể gán giá trị trực tiếp khi khai báo biến struct:

💻 **Ví dụ**

```c
struct myStruct {
  int myNum;
  char myLetter;
  char myString[30];
};

int main() {
  struct myStruct s1 = {13, 'B', "Some text"};
  printf("%d %c %s", s1.myNum, s1.myLetter, s1.myString);
  return 0;
}
```

Lưu ý: Thứ tự giá trị phải khớp với thứ tự khai báo biến trong struct.

📌 **Ghi nhớ**

- Có thể gán giá trị trực tiếp khi khai báo biến struct.
- Thứ tự giá trị phải khớp với thứ tự khai báo biến trong struct.

---

# 8. SAO CHÉP STRUCT

📝 **Giải thích**  
Bạn có thể sao chép một struct sang một struct khác:

💻 **Ví dụ**

```c
struct myStruct s1 = {13, 'B', "Some text"};
struct myStruct s2;
s2 = s1;
```

📌 **Ghi nhớ**

- Có thể sao chép một struct sang một struct khác.

---

# 9. CHỈNH SỬA GIÁ TRỊ TRONG STRUCT

📝 **Giải thích**  
Bạn có thể thay đổi giá trị của một thuộc tính struct bằng dấu `.` và sử dụng `strcpy()` cho chuỗi:

💻 **Ví dụ**

```c
struct myStruct {
  int myNum;
  char myLetter;
  char myString[30];
};

int main() {
  struct myStruct s1 = {13, 'B', "Some text"};

  s1.myNum = 30;
  s1.myLetter = 'C';
  strcpy(s1.myString, "Something else");

  printf("%d %c %s", s1.myNum, s1.myLetter, s1.myString);
  return 0;
}
```

📌 **Ghi nhớ**

- Sử dụng dấu chấm (`.`) để thay đổi giá trị của thuộc tính struct.
- Sử dụng `strcpy()` để thay đổi giá trị chuỗi.

---

# 10. ỨNG DỤNG STRUCT TRONG THỰC TẾ

📝 **Giải thích**  
Giả sử bạn muốn lưu trữ thông tin về xe hơi như thương hiệu, mẫu xe và năm sản xuất. Bạn có thể tạo một struct để làm "mẫu xe hơi" chung:

💻 **Ví dụ**

```c
struct Car {
  char brand[50];
  char model[50];
  int year;
};

int main() {
  struct Car car1 = {"BMW", "X5", 1999};
  struct Car car2 = {"Ford", "Mustang", 1969};
  struct Car car3 = {"Toyota", "Corolla", 2011};

  printf("%s %s %d\n", car1.brand, car1.model, car1.year);
  printf("%s %s %d\n", car2.brand, car2.model, car2.year);
  printf("%s %s %d\n", car3.brand, car3.model, car3.year);

  return 0;
}
```

📌 **Ghi nhớ**

- Struct có thể được sử dụng để lưu trữ thông tin phức tạp trong thực tế.

---

# 11. TỔNG KẾT

Struct trong C giúp nhóm nhiều biến liên quan vào một đơn vị duy nhất, giúp quản lý dữ liệu tốt hơn. Đây là công cụ mạnh mẽ để làm việc với dữ liệu phức tạp trong lập trình C.