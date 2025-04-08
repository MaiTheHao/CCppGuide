# MỤC LỤC

1. [LÝ DO CẦN CÓ STRUCT](#1-lý-do-cần-có-struct)
2. [STRUCT LÀ CÁI QUÁI GÌ?](#2-struct-là-cái-quái-gì)
3. [KHAI BÁO STRUCT KIỂU GÌ ĐÂY?](#3-khai-báo-struct-kiểu-gì-đây)
4. [MÒ MẪM THUỘC TÍNH CỦA STRUCT](#4-mò-mẫm-thuộc-tính-của-struct)
5. [TẠO CẢ ĐỐNG BIẾN STRUCT](#5-tạo-cả-đống-biến-struct)
6. [XỬ LÝ CHUỖI TRONG STRUCT, ĐAU ĐẦU THẬT](#6-xử-lý-chuỗi-trong-struct-đau-đầu-thật)
7. [KHAI BÁO NGẮN GỌN CHO ĐỠ MỎI TAY](#7-khai-báo-ngắn-gọn-cho-đỡ-mỏi-tay)
8. [COPY STRUCT, DỄ NHƯ ĂN KẸO](#8-copy-struct-dễ-như-ăn-kẹo)
9. [SỬA GIÁ TRỊ STRUCT, THA HỒ NGHỊCH](#9-sửa-giá-trị-struct-tha-hồ-nghịch)
10. [STRUCT TRONG ĐỜI THỰC, KHÔNG PHẢI CHUYỆN ĐÙA](#10-struct-trong-đời-thực-không-phải-chuyện-đùa)
11. [TỔNG KẾT, NGẮN GỌN THÔI](#11-tổng-kết-ngắn-gọn-thôi)

# 1. LÝ DO CẦN CÓ STRUCT

📝 **Giải thích**  
Trong cái thế giới lập trình C này, nếu cứ cố nhét từng tí thông tin của một thứ gì đó vào mấy cái biến lẻ tẻ, thì thề luôn, bạn sẽ sớm phát điên. Ví dụ nhé, bạn muốn lưu info của một anh chàng sinh viên: ID, tên, điểm GPA. Nếu không có struct, phải khai báo từng biến kiểu:

💻 **Ví dụ**

```c
int studentID = 123;
char studentName[50] = "Cu Teo";
float studentGPA = 3.2;
```

Rồi giờ tưởng tượng có 10 sinh viên, bạn định khai báo 30 biến à? Đầu óc có chịu nổi không hay lại ngồi gõ code mà mắt cay xè? Struct ra đời để cứu vớt cuộc đời, gom hết mấy thứ lằng nhằng đó vào một cục cho gọn gàng, dễ quản lý, khỏi loạn cào cào.

📌 **Nhớ nha**

-   Struct là "cái túi thần kỳ" gom hết biến liên quan lại.
-   Code gọn hơn, đời bớt khổ.

---

# 2. STRUCT LÀ CÁI QUÁI GÌ?

📝 **Giải thích**  
Struct là cái thứ mà bạn có thể tưởng tượng như một cái hộp đựng đồ. Trong hộp đó, tha hồ nhét đủ thứ: số, chữ, ký tự, gì cũng được. Không giống cái mảng ngố ngơ chỉ chứa một loại, struct chơi đẹp, đa năng khủng khiếp!

📌 **Nhớ nha**

-   Struct đựng được đủ kiểu dữ liệu, không kén chọn.
-   Mấy cái biến trong đó gọi là "thuộc tính", nghe sang chưa?

---

# 3. KHAI BÁO STRUCT KIỂU GÌ ĐÂY?

📝 **Giải thích**  
Muốn tạo struct thì phải dùng từ khóa `struct`, rồi nhét mấy thuộc tính vào trong cặp ngoặc nhọn `{}`. Xong xuôi nhớ chốt bằng dấu chấm phẩy `;` nha, không là compiler sẽ báo lỗi cú pháp.

💻 **Ví dụ**

```c
struct MyStruct {
  int myNum;      // số nguyên nè
  char myLetter;  // ký tự nè
};
```

Rồi muốn xài thì khai báo biến trong `main()` kiểu này:

```c
struct MyStruct s1; // biến struct đây
```

## **Dùng `typedef` cho đỡ mệt**

📝 **Giải thích**  
Mỗi lần khai báo mà cứ phải gõ `struct` dài dòng thì mỏi tay lắm. Dùng `typedef` để đặt tên ngắn gọn hơn, đỡ phải lặp đi lặp lại từ khóa `struct`.

💻 **Ví dụ**

```c
#include <stdio.h>
typedef struct {
  int myNum;
  char myLetter;
} MyStruct;

int main() {
  MyStruct s1; // gọn lỏn, không cần gõ struct nữa
  s1.myNum = 69;
  s1.myLetter = 'Z';
  printf("Số: %d, Chữ: %c\n", s1.myNum, s1.myLetter);
  return 0;
}
```

📌 **Nhớ nha**

-   `typedef` giúp tạo tên kiểu dữ liệu mới, rút gọn cú pháp.
-   Biến struct giờ khai báo ngắn gọn và dễ đọc hơn.

---

# 4. MÒ MẪM THUỘC TÍNH CỦA STRUCT

📝 **Giải thích**  
Muốn truy cập vào các thuộc tính của struct thì dùng dấu chấm `.`. Đơn giản cực kỳ, giống như cách bạn chọn một thuộc tính cụ thể trong struct.

💻 **Ví dụ**

```c
struct MyStruct {
  int myNum;
  char myLetter;
};

int main() {
  struct MyStruct s1;
  s1.myNum = 420;
  s1.myLetter = 'X';
  printf("Số của tôi: %d\n", s1.myNum);
  printf("Chữ của tôi: %c\n", s1.myLetter);
  return 0;
}
```

📌 **Nhớ nha**

-   Dấu chấm `.` là cách để truy cập đến từng thuộc tính trong struct.

---

# 5. TẠO CẢ ĐỐNG BIẾN STRUCT

📝 **Giải thích**  
Một struct mà tạo được cả tá biến, mỗi biến là một thể hiện riêng. Mỗi biến là một bản sao độc lập, có thể gán giá trị khác nhau.

💻 **Ví dụ**

```c
struct MyStruct s1, s2;
s1.myNum = 69;
s1.myLetter = 'A';
s2.myNum = 420;
s2.myLetter = 'B';
```

📌 **Nhớ nha**

-   Một struct cho phép tạo nhiều biến, mỗi biến quản lý bộ dữ liệu riêng.

---

# 6. XỬ LÝ CHUỖI TRONG STRUCT, ĐAU ĐẦU THẬT

📝 **Giải thích**  
Chuỗi trong C là một mảng ký tự, và vì đặc tính của mảng trong C, bạn không thể gán trực tiếp kiểu "Hello" vào được. Điều này xảy ra vì mảng trong C hoạt động như con trỏ cố định, nên không thể thay đổi địa chỉ mà nó trỏ tới.

💻 **Ví dụ sai**

```c
#include <stdio.h>
struct MyStruct {
  char myString[30];
};
int main() {
  struct MyStruct s1;
  s1.myString = "Hello"; // Sai cú pháp, không thể gán trực tiếp
  return 0;
}
```

Muốn gán chuỗi đúng cách thì phải dùng `strcpy()` từ thư viện string.h:  
💻 **Ví dụ đúng**

```c
#include <stdio.h>
#include <string.h> // Nhớ include thư viện này!
struct MyStruct {
  char myString[30];
};
int main() {
  struct MyStruct s1;
  strcpy(s1.myString, "Hello bro");
  printf("Chuỗi của tôi: %s\n", s1.myString);
  return 0;
}
```

📌 **Nhớ nha**

-   Chuỗi trong struct phải dùng `strcpy()` để gán giá trị, không gán trực tiếp được.
-   Luôn nhớ include `<string.h>` khi làm việc với chuỗi.

---

# 7. KHAI BÁO NGẮN GỌN CHO ĐỠ MỎI TAY

📝 **Giải thích**  
Bạn có thể khởi tạo giá trị ngay lúc khai báo struct, giúp code ngắn gọn hơn. Tuy nhiên, cú pháp này chỉ hoạt động khi khai báo biến lần đầu, không thể dùng để gán lại giá trị sau khi đã khai báo.

💻 **Ví dụ**

```c
struct MyStruct {
  int myNum;
  char myLetter;
  char myString[30];
};
int main() {
  struct MyStruct s1 = {69, 'Z', "Yo yo"}; // Khởi tạo ngay lúc khai báo - OK
  printf("%d %c %s\n", s1.myNum, s1.myLetter, s1.myString);

  // Gán sau khai báo phải làm theo từng thuộc tính
  s1.myNum = 100; // OK
  // s1 = {100, 'A', "Hello"}; // Sai - không thể gán kiểu này sau khai báo
  return 0;
}
```

📌 **Nhớ nha**

-   Khởi tạo giá trị ngay lúc khai báo giúp code gọn gàng.
-   Thứ tự giá trị phải khớp với thứ tự các thuộc tính trong struct.
-   Không thể dùng cú pháp khởi tạo `{...}` để gán lại giá trị sau khi đã khai báo.

---

# 8. COPY STRUCT, DỄ NHƯ ĂN KẸO

📝 **Giải thích**  
Muốn nhân bản struct thì gán trực tiếp, C sẽ tự sao chép toàn bộ nội dung. Đây là sao chép giá trị (value copy), tức là sẽ sao chép toàn bộ dữ liệu từ struct này sang struct khác.

💻 **Ví dụ**

````c
struct MyStruct s1 = {69, 'Z', "Yo yo"};
struct MyStruct s2 =

📝 **Giải thích**
Muốn thay đổi gì trong struct thì cứ dùng dấu `.`, còn chuỗi thì lại lôi `strcpy()` ra xài.

💻 **Ví dụ**

```c
struct MyStruct {
  int myNum;
  char myLetter;
  char myString[30];
};
int main() {
  struct MyStruct s1 = {69, 'Z', "Yo yo"};
  s1.myNum = 420;
  s1.myLetter = 'X';
  strcpy(s1.myString, "Wassup bro");
  printf("%d %c %s\n", s1.myNum, s1.myLetter, s1.myString);
  return 0;
}
````

📌 **Nhớ nha**

-   Dấu `.` để sửa số với chữ, `strcpy()` cho chuỗi.

---

# 10. STRUCT TRONG ĐỜI THỰC, KHÔNG PHẢI CHUYỆN ĐÙA

📝 **Giải thích**  
Thử tưởng tượng bạn làm app quản lý xe hơi của mấy ông đại gia đi. Mỗi chiếc xe cần thương hiệu, mẫu, năm sản xuất. Struct là chân ái luôn!

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
  printf("Xe 1: %s %s %d\n", car1.brand, car1.model, car1.year);
  printf("Xe 2: %s %s %d\n", car2.brand, car2.model, car2.year);
  printf("Xe 3: %s %s %d\n", car3.brand, car3.model, car3.year);
  return 0;
}
```

📌 **Nhớ nha**

-   Struct là "trùm" quản lý dữ liệu thực tế.

---

# 11. TỔNG KẾT, NGẮN GỌN THÔI

Struct trong C là cái hộp thần kỳ, gom hết mớ bòng bong dữ liệu lại cho bạn dễ sống. Học xong cái này là lên level pro ngay, không đùa đâu!
