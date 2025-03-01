# HÀM TRONG C

## 1. GIỚI THIỆU VỀ HÀM

### 1.1. HÀM LÀ GÌ?
Một **function** hay **hàm** là một khối mã thực hiện một nhiệm vụ cụ thể và có thể được gọi từ nhiều nơi trong chương trình. Function giúp chia nhỏ chương trình thành các phần có thể quản lý và tái sử dụng.

### 1.2. TẠI SAO SỬ DỤNG HÀM?
Sử dụng hàm giúp:
- **Tái sử dụng mã**.
- **Dễ dàng quản lý và bảo trì mã nguồn**.
- **Tăng độ rõ ràng và dễ đọc của chương trình**.

### 1.3. VAI TRÒ CỦA HÀM TRONG LẬP TRÌNH C
Function giúp tổ chức mã thành các khối hàm, làm cho chương trình dễ đọc, bảo trì và giảm lỗi.

## 2. CÚ PHÁP CƠ BẢN CỦA HÀM TRONG C

### 2.1. CẤU TRÚC CHUNG CỦA MỘT HÀM
```c
return_type function_name(parameter_list) {
  // Function body
}
```

### 2.2. CÁC THÀNH PHẦN CỦA MỘT HÀM

| Thành Phần      | Mô Tả                                                                 |
|-----------------|----------------------------------------------------------------------|
| **return_type** | Kiểu dữ liệu của giá trị mà hàm trả về. Sử dụng `void` nếu hàm không trả về giá trị. |
| **function_name**| Tên định danh của hàm, tuân theo các quy tắc đặt tên biến.      |
| **parameter_list**     | Danh sách các biến đầu vào cho hàm, có thể rỗng.                |
| **function_body**| Khối mã thực hiện nhiệm vụ của hàm.                            |

### 2.3. VÍ DỤ CƠ BẢN
```c
#include <stdio.h>

void sayHello() {
  printf("Hello, World!\n");
}

int main() {
  sayHello();
  return 0;
}
```

#### Phân Tích Cấu Trúc Hàm
- **Function `sayHello`**:
  - **Return type**: `void` (không trả về giá trị).
  - **Function name**: `sayHello`.
  - **Parameters**: Không có.
  - **Function body**: Gồm một lệnh `printf` để in ra chuỗi "Hello, World!".

- **Function `main`**:
  - **Return type**: `int` (trả về giá trị nguyên).
  - **Function name**: `main`.
  - **Parameters**: Không có.
  - **Function body**: 
    - Gọi hàm `sayHello` để in ra chuỗi "Hello, World!".
    - Trả về giá trị `0` để kết thúc chương trình.

## 3. KHAI BÁO VÀ ĐỊNH NGHĨA HÀM

### 3.1. KHAI BÁO HÀM (FUNCTION DECLARATION)  
Khai báo hàm giống như việc "giới thiệu" hàm với trình biên dịch trước khi sử dụng nó. Khi khai báo, ta chỉ cần nêu:  
- Tên hàm  
- Kiểu dữ liệu mà hàm trả về  
- Danh sách tham số (nếu có)  

Ví dụ:  
```c
void sayHello();    // Hàm không có tham số, không trả về giá trị
int add(int a, int b); // Hàm có hai tham số kiểu int, trả về kiểu int
```
>⏳ **Lưu ý:** Ở bước này, ta chưa viết nội dung bên trong hàm, chỉ đơn giản là khai báo cho trình biên dịch biết hàm đó tồn tại.  

---

### 3.2. ĐỊNH NGHĨA HÀM (FUNCTION DEFINITION)  
Định nghĩa hàm là lúc ta viết nội dung cụ thể để hàm thực hiện một nhiệm vụ nào đó. Đây chính là phần chứa các lệnh thực thi bên trong thân hàm.  

Ví dụ:  
```c
void sayHello() {   // Hàm này khi được gọi sẽ in ra dòng chữ "Hello, World!"
  printf("Hello, World!\n");
}

int add(int a, int b) {  // Hàm này nhận vào hai số nguyên và trả về tổng của chúng
  return a + b;
}
```
>📝 **Lưu ý:** Nếu bạn chỉ khai báo mà không định nghĩa, khi gọi hàm, chương trình sẽ không biết phải thực thi điều gì.

---

### 3.3. SỰ KHÁC BIỆT GIỮA KHAI BÁO VÀ ĐỊNH NGHĨA  

| Đặc điểm            | Khai báo hàm                | Định nghĩa hàm               |
|---------------------|---------------------------|------------------------------|
| **Mục đích**       | Giới thiệu hàm với trình biên dịch | Viết nội dung thực thi của hàm |
| **Có thân hàm không?** | ❌ Không có thân hàm (chỉ có dấu `;`) | ✅ Có thân hàm (chứa mã lệnh) |
| **Ví dụ**          | `int add(int a, int b);`  | `int add(int a, int b) { return a + b; }` |

📌 **Tóm lại:**  
- Nếu chỉ khai báo mà không định nghĩa -> Trình biên dịch biết hàm tồn tại nhưng không biết nó làm gì.  
- Nếu chỉ định nghĩa mà không khai báo -> Nếu định nghĩa ở sau khi gọi, trình biên dịch sẽ không biết đến nó.  
- Thông thường, ta khai báo hàm ở đầu file hoặc trong file header (`.h`), còn phần định nghĩa đặt trong file `.c`.  

---

```c
#include <stdio.h>

// Khai báo hàm
void sayHello();
int add(int a, int b);

int main() {
  sayHello();  // Gọi hàm sayHello
  int result = add(3, 5);  // Gọi hàm add với hai tham số 3 và 5
  printf("Tổng: %d\n", result);
  return 0;
}

// Định nghĩa hàm
void sayHello() {
  printf("Hello, World!\n");
}

int add(int a, int b) {
  return a + b;
}
```
💡 **Giải thích:**  
- Phần khai báo ở đầu giúp trình biên dịch nhận diện được các hàm.  
- Trong `main()`, ta có thể gọi hàm trước cả khi nó được định nghĩa nhờ khai báo từ trước.  
- Sau `main()`, phần định nghĩa hàm giúp hoàn thiện chức năng của chúng.  

---

## 4. CÁC LOẠI HÀM TRONG C 🚀
Trong lập trình C, hàm giúp chia nhỏ chương trình thành từng phần dễ quản lý. Có 4 loại hàm cơ bản:

### 4.1. HÀM KHÔNG CÓ THAM SỐ VÀ KHÔNG TRẢ VỀ GIÁ TRỊ
```c
void sayHello() {
  printf("Hello, world!\n");
}
```
📌 Giải thích:
- `void` nghĩa là không trả về gì cả.
- `sayHello` là tên hàm.
- Không có tham số nào trong `()` -> Không cần nhập dữ liệu.
- Khi gọi `sayHello();`, nó chỉ in ra "Hello, world!".

### 4.2. HÀM CÓ THAM SỐ NHƯNG KHÔNG TRẢ VỀ GIÁ TRỊ
```c
void greet(char *name) {
  printf("Hello, %s!\n", name);
}
```
📌 Giải thích:
- `char *name` là tham số truyền vào (một chuỗi ký tự).
- Khi gọi `greet("Alice");`, nó in "Hello, Alice!".

### 4.3. HÀM KHÔNG CÓ THAM SỐ NHƯNG TRẢ VỀ GIÁ TRỊ
```c
int getLuckyNumber() {
  return 7;
}
```
📌 Giải thích:
- `int` nghĩa là hàm trả về một số nguyên.
- Khi gọi `getLuckyNumber();`, nó trả về số 7, nhưng nếu không `printf()` hay gán vào biến thì không thấy được.

### 4.4. HÀM CÓ CẢ THAM SỐ VÀ TRẢ VỀ GIÁ TRỊ
```c
int add(int a, int b) {
  return a + b;
}
```
📌 Giải thích:
- `int a, int b` là hai tham số truyền vào.
- `return a + b;` trả về kết quả của phép cộng.
- Gọi `add(3, 4);` thì nó trả về 7.

### 4.5. CÁCH SỬ DỤNG HÀM TRONG `main()`
```c
#include <stdio.h>

void sayHello() {
  printf("Hello, world!\n");
}

void greet(char *name) {
  printf("Hello, %s!\n", name);
}

int getLuckyNumber() {
  return 7;
}

int add(int a, int b) {
  return a + b;
}

int main() {
  sayHello();  
  greet("Alice");  
  printf("Lucky number: %d\n", getLuckyNumber());  
  printf("3 + 4 = %d\n", add(3, 4));  
  return 0;
}
```
🎯 Tóm tắt:
- ✅ Hàm giúp chương trình dễ hiểu, dễ bảo trì.
- ✅ Có thể truyền tham số hoặc trả về kết quả tùy nhu cầu.
- ✅ Dùng `void` khi không cần trả về, dùng kiểu dữ liệu (`int`, `float`,...) khi có kết quả trả về.

## 5. TRUYỀN THAM SỐ CHO HÀM

### 5.1. TRUYỀN THEO GIÁ TRỊ
Truyền giá trị của biến cho hàm, và hàm không thể thay đổi giá trị gốc.
```c
void increment(int x) {
  x++;
}
```

### 5.2. TRUYỀN THEO THAM CHIẾU SỬ DỤNG CON TRỎ
Truyền địa chỉ của biến cho hàm, cho phép hàm thay đổi giá trị gốc.
```c
void increment(int *x) {
  (*x)++;
}
```

### 5.3. SO SÁNH TRUYỀN THEO GIÁ TRỊ VÀ TRUYỀN THEO THAM CHIẾU

Truyền theo giá trị và truyền theo tham chiếu là hai cách để truyền tham số vào hàm trong C. Dưới đây là bảng so sánh chi tiết giữa hai phương pháp này:

| Đặc điểm                  | Truyền theo giá trị                              | Truyền theo tham chiếu                              |
|---------------------------|--------------------------------------------------|----------------------------------------------------|
| **Cách thức**             | Truyền bản sao của biến                          | Truyền địa chỉ của biến                             |
| **Thay đổi giá trị gốc**  | Không thể thay đổi giá trị gốc                   | Có thể thay đổi giá trị gốc                         |
| **An toàn**               | An toàn hơn vì không thay đổi giá trị gốc        | Ít an toàn hơn vì có thể thay đổi giá trị gốc       |
| **Hiệu suất**             | Có thể chậm hơn với các biến lớn                 | Nhanh hơn với các biến lớn do chỉ truyền địa chỉ    |
| **Sử dụng con trỏ**       | Không cần sử dụng con trỏ                        | Cần sử dụng con trỏ                                 |
| **Ví dụ**                 | `void func(int x) { x++; }`                      | `void func(int *x) { (*x)++; }`                     |

>💡 **Lưu ý:** Nên tìm hiểu về con trỏ trước khi tìm hiểu về truyền tham chiếu.

### 5.4. VÍ DỤ
```c
#include <stdio.h>

// Hàm add sử dụng tham chiếu để thay đổi giá trị của biến x
void add(int *x) {
  *x += 1;
}

// Hàm sub sử dụng tham chiếu để thay đổi giá trị của biến x
void sub(int x) {
  x -= 1;
}

int main() {
  int a = 5;

  // Gọi hàm add với tham chiếu đến biến a
  add(&a);
  printf("Sau khi add: %d\n", a); // 6

  // Gọi hàm sub với tham trị đến biến a
  sub(a);
  printf("Sau khi sub: %d\n", a); // 6

  return 0;
}
```

Trong ví dụ trên:
- Hàm `add` sử dụng tham chiếu để thay đổi giá trị của biến `a`.
- Hàm `sub` cũng sử dụng tham chiếu để thay đổi giá trị của biến `a`.
- Khi gọi các hàm này, giá trị của `a` thay đổi theo các phép toán cộng và trừ.

## 6. GIÁ TRỊ TRẢ VỀ CỦA HÀM

### 6.1. SỬ DỤNG TỪ KHÓA `return`
Từ khóa `return` được sử dụng để trả về một giá trị từ hàm.
```c
int sum(int a, int b) {
  return a + b;
}
```

### 6.2. CÁC KIỂU DỮ LIỆU TRẢ VỀ KHÁC NHAU (int, float, char, v.v.)
Hàm có thể trả về các kiểu dữ liệu khác nhau như `int`, `float`, `char`, v.v.
```c
float getPI() {
  return 3.14;
}
```

### 6.3. VOID HÀM
Hàm `void` không trả về giá trị.
```c
void printMessage() {
  printf("This is a message.\n");
}
```

### 6.4. VÍ DỤ VỀ CÁC HÀM TRẢ VỀ GIÁ TRỊ
```c
#include <stdio.h>

int add(int a, int b) {
  return a + b;
}

float getPI() {
  return 3.14;
}

void printMessage() {
  printf("This is a message.\n");
}

int main() {
  printf("Sum: %d\n", add(3, 4));
  printf("PI: %.2f\n", getPI());
  printMessage();
  return 0;
}
```

## 7. THƯ VIỆN HÀM TIÊU CHUẨN

### 7.1. GIỚI THIỆU VỀ THƯ VIỆN HÀM TIÊU CHUẨN
C cung cấp nhiều thư viện hàm tiêu chuẩn cho các tác vụ thông thường.

### 7.2. VÍ DỤ VỀ CÁC HÀM TỪ `<stdio.h>` (printf, scanf)
```c
#include <stdio.h>

int main() {
  printf("Enter a number: ");
  int num;
  scanf("%d", &num);
  printf("You entered: %d\n", num);
  return 0;
}
```

### 7.3. VÍ DỤ VỀ CÁC HÀM TỪ `<math.h>` (sqrt, pow)
```c
#include <stdio.h>
#include <math.h>

int main() {
  double num = 16.0;
  printf("Square root of %.2f is %.2f\n", num, sqrt(num));
  printf("2 raised to the power 3 is %.2f\n", pow(2, 3));
  return 0;
}
```

### 7.4. CÁCH SỬ DỤNG THƯ VIỆN HÀM
Để sử dụng các thư viện hàm tiêu chuẩn, bao gồm tệp tiêu đề tương ứng bằng cách sử dụng chỉ thị `#include`.

## 10. THỰC HÀNH VÀ BÀI TẬP

### 10.1. VIẾT HÀM KIỂM TRA SỐ NGUYÊN TỐ
```c
#include <stdio.h>
#include <stdbool.h>

bool isPrime(int n) {
  if (n <= 1) return false;
  for (int i = 2; i <= n / 2; i++) {
    if (n % i == 0) return false;
  }
  return true;
}

int main() {
  int num = 29;
  if (isPrime(num)) {
    printf("%d is a prime number.\n", num);
  } else {
    printf("%d is not a prime number.\n", num);
  }
  return 0;
}
```

### 10.2. VIẾT HÀM ĐỂ HOÁN ĐỔI HAI SỐ
```c
#include <stdio.h>

void swap(int *a, int *b) {
  int temp = *a;
  *a = *b;
  *b = temp;
}

int main() {
  int x = 5, y = 10;
  printf("Before swap: x = %d, y = %d\n", x, y);
  swap(&x, &y);
  printf("After swap: x = %d, y = %d\n", x, y);
  return 0;
}
```

>💡 **Trick nâng cao:** Bạn cũng có thể sử dụng phép toán XOR để hoán đổi hai số mà không cần biến tạm. Tuy nhiên, cách này ít phổ biến và khó đọc hơn.
```c
void swap(int *a, int *b) {
  *a = *a ^ *b;
  *b = *a ^ *b;
  *a = *a ^ *b;
}
```

### 10.3. VIẾT HÀM ĐỂ TÍNH TỔNG CÁC PHẦN TỬ MẢNG
```c
#include <stdio.h>

int sumArray(int arr[], int size) {
  int sum = 0;
  for (int i = 0; i < size; i++) {
    sum += arr[i];
  }
  return sum;
}

int main() {
  int arr[] = {1, 2, 3, 4, 5};
  int size = sizeof(arr) / sizeof(arr[0]);
  printf("Sum of array elements: %d\n", sumArray(arr, size));
  return 0;
}
```

### 10.4. GỢI Ý BÀI TẬP
- Tạo hàm sử dụng vòng lặp và điều kiện để kiểm tra số nguyên tố.
- Tạo hàm sử dụng con trỏ để hoán đổi giá trị của hai biến.
- Tạo hàm sử dụng vòng lặp để tính tổng các phần tử của mảng.

## 11. LỖI THƯỜNG GẶP VÀ MẸO

| Lỗi Thường Gặp                          | Cách Khắc Phục                                                                 |
|-----------------------------------------|-------------------------------------------------------------------------------|
| **Quên khai báo hàm trước khi sử dụng** | Đảm bảo function được khai báo trước khi gọi chúng trong `main` hoặc các function khác. |
| **Kiểu dữ liệu trả về không đúng**      | Kiểm tra kỹ kiểu dữ liệu trả về của function để tránh lỗi biên dịch.          |
| **Lỗi trong việc truyền tham số**       | Đảm bảo số lượng và kiểu dữ liệu của tham số đúng khi gọi function.           |

- Đọc kỹ thông báo lỗi của trình biên dịch.
- Kiểm tra khai báo và định nghĩa function.
- Đảm bảo truyền tham số đúng khi gọi function.

## 12. KẾT LUẬN

### 12.1. TÓM TẮT CÁC ĐIỂM CHÍNH
- **Chức năng của hàm**: Giúp tổ chức mã thành các khối dễ quản lý.
- **Loại hàm**: Có nhiều loại hàm với các tham số và giá trị trả về khác nhau.
- **Truyền tham số**: Có thể truyền theo giá trị hoặc theo tham chiếu.

### 12.2. HÀM TRONG LẬP TRÌNH THỰC TẾ
Hàm là công cụ thiết yếu trong lập trình, giúp mã nguồn dễ quản lý và bảo trì.

### 12.3. BƯỚC TIẾP THEO SAU KHI HỌC HÀM
- **Thực hành**: Viết các hàm phức tạp hơn.
- **Khám phá**: Tìm hiểu các khái niệm nâng cao như con trỏ hàm và hàm bậc cao.

Hãy tiếp tục thực hành và khám phá thêm để nâng cao kỹ năng lập trình của bạn!