# Cấu trúc rẽ nhánh (if-else)

Cấu trúc `if-else` cho phép lập trình viên quyết định khối lệnh nào được thi hành dựa vào điều kiện logic.

# Cú pháp căn bản

```c
if (điều_kiện) {
    // Khối lệnh thực thi nếu điều kiện đúng
} else {
    // Khối lệnh thực thi nếu điều kiện sai
}
```

# Lồng nhiều điều kiện

```c
if (điều_kiện_1) {
    // Khối lệnh 1
} else if (điều_kiện_2) {
    // Khối lệnh 2
} else {
    // Khối lệnh mặc định
}
```

# Toán tử điều kiện trong C

C hỗ trợ các toán tử điều kiện logic thông dụng:

- Nhỏ hơn: `a < b`
- Nhỏ hơn hoặc bằng: `a <= b`
- Lớn hơn: `a > b`
- Lớn hơn hoặc bằng: `a >= b`
- Bằng: `a == b`
- Khác: `a != b`

# Ví dụ minh họa

```c
#include <stdio.h>

int main() {
    int x = 10;
    if (x > 0) {
        printf("x là số dương\n");
    } else if (x < 0) {
        printf("x là số âm\n");
    } else {
        printf("x là số 0\n");
    }
    return 0;
}
```

# Toán tử ba ngôi (Ternary Operator)

Toán tử ba ngôi là cách viết rút gọn của câu lệnh `if-else`. Nó được gọi là toán tử ba ngôi vì có ba thành phần.

## Cú pháp

```c
biến = (điều_kiện) ? giá_trị_đúng : giá_trị_sai;
```

## Ví dụ minh họa

Thay vì viết:

```c
int time = 20;
if (time < 18) {
    printf("Chào ban ngày.");
} else {
    printf("Chào buổi tối.");
}
```

Bạn có thể viết gọn lại thành:

```c
int time = 20;
(time < 18) ? printf("Chào ban ngày.") : printf("Chào buổi tối.");
```

Một ví dụ khác về gán giá trị:

```c
int a = 10, b = 20;
int max = (a > b) ? a : b;  // max sẽ bằng 20
```

> **Lưu ý**: Mặc dù toán tử ba ngôi giúp code ngắn gọn hơn, nhưng nên sử dụng một cách hợp lý. Nếu logic quá phức tạp, nên dùng if-else thông thường để code dễ đọc hơn.

> **Mẹo**: Luôn kiểm tra tính chính xác của điều kiện trước khi viết khối lệnh, tránh lồng ghép `if-else` phức tạp gây khó đọc.

# Thủ thuật tối ưu câu lệnh điều kiện

## 1. Trả về trực tiếp điều kiện

Thay vì viết if-else để trả về giá trị boolean, hãy trả về điều kiện trực tiếp.

```c
// Cách thông thường
if (x > 0) {
    return 1;
} else {
    return 0;
}

// Cách tối ưu
return x > 0;
```

## 2. Gán giá trị mặc định

Gán giá trị mặc định trước, chỉ thay đổi khi điều kiện thỏa mãn.

```c
// Cách thông thường
int status;
if (connection) {
    status = 1;
} else {
    status = 0;
}

// Cách tối ưu
int status = 0;  // giá trị mặc định
if (connection) {
    status = 1;
}
```

## 3. Sử dụng switch thay cho nhiều if-else (bạn sẽ được học ở phía dưới)

Khi có nhiều điều kiện, switch có thể giúp code rõ ràng hơn:

```c
switch (grade) {
    case 'A':
        printf("Xuất sắc\n");
        break;
    case 'B':
        printf("Giỏi\n");
        break;
    default:
        printf("Đạt\n");
}
```

## 4. Tránh so sánh không cần thiết

```c
// Không cần thiết
if (isValid == 1)

// Tốt hơn
if (isValid)
```

## 5. Sử dụng toán tử ba ngôi (ternary operator)

```c
// Thay vì
int max;
if (a > b) {
    max = a;
} else {
    max = b;
}

// Có thể viết
int max = (a > b) ? a : b;
```

## 6. Sử dụng tư duy ngược trong `if-else`

Một cách tiếp cận hiệu quả là **tư duy ngược (reverse thinking)** hay **guard clause**. Thay vì lồng nhiều `if-else`, bạn kiểm tra các điều kiện không hợp lệ trước và trả về sớm. Điều này giúp mã nguồn rõ ràng, dễ bảo trì hơn.

**Ví dụ:**

```c

/*
- Nếu người dùng chưa đăng nhập, trả về thông báo "Bạn chưa đăng nhập."
- Nếu người dùng đã đăng nhập nhưng không có quyền truy cập, trả về thông báo "Bạn không có quyền truy cập."
- Nếu người dùng đã đăng nhập và có quyền truy cập, trả về thông báo "Truy cập thành công!"
*/

// Cách thông thường
if (!isLoggedIn) {
    printf("Bạn chưa đăng nhập.");
} else {
    if (!hasPermission) {
        printf("Bạn không có quyền truy cập.");
    } else {
        printf("Truy cập thành công!");
    }
}

// Cách tối ưu
if (!isLoggedIn) return "Bạn chưa đăng nhập.";
if (!hasPermission) return "Bạn không có quyền truy cập.";
return "Truy cập thành công!";
```

Cách này giúp mã gọn hơn, tránh lồng `if-else` sâu, dễ đọc và bảo trì hơn.

> **Lưu ý**: Mặc dù các thủ thuật này giúp code ngắn gọn hơn, nhưng cần đảm bảo tính rõ ràng và dễ đọc của code.

# Câu lệnh `switch` trong C

Câu lệnh `switch` trong ngôn ngữ lập trình C được sử dụng để chọn và thực thi một trong nhiều khối mã dựa trên giá trị của một biểu thức. Nó cung cấp một cách hiệu quả để thay thế cho việc sử dụng nhiều câu lệnh `if...else if` khi cần kiểm tra giá trị của một biến hoặc biểu thức.

**Cú pháp của câu lệnh `switch` trong C:**

```c
switch (biểu_thức) {
    case hằng_số_1:
        // khối mã 1
        break;
    case hằng_số_2:
        // khối mã 2
        break;
    // ...
    default:
        // khối mã mặc định
}
```

Trong đó, `biểu_thức` được đánh giá một lần và so sánh với các giá trị hằng số trong từng nhãn `case`. Nếu tìm thấy sự trùng khớp, khối mã tương ứng sẽ được thực thi. Từ khóa `break` được sử dụng để kết thúc việc thực thi trong cấu trúc `switch`, ngăn chặn việc tiếp tục thực thi các khối mã của các `case` tiếp theo. Nếu không có `break`, chương trình sẽ tiếp tục thực thi các khối mã dưới các nhãn `case` tiếp theo cho đến khi gặp `break` hoặc kết thúc cấu trúc `switch`. Nhãn `default` là tùy chọn và được thực thi khi không có trường hợp `case` nào khớp với giá trị của biểu thức.

**Ví dụ về sử dụng `switch` trong C:**

```c
#include <stdio.h>

int main() {
    int day = 4;
    switch (day) {
        case 1:
            printf("Monday\n");
            break;
        case 2:
            printf("Tuesday\n");
            break;
        case 3:
            printf("Wednesday\n");
            break;
        case 4:
            printf("Thursday\n");
            break;
        case 5:
            printf("Friday\n");
            break;
        case 6:
            printf("Saturday\n");
            break;
        case 7:
            printf("Sunday\n");
            break;
        default:
            printf("Invalid day\n");
    }
    return 0;
}
```

Trong ví dụ này, biến `day` có giá trị là 4. Khi được truyền vào cấu trúc `switch`, chương trình sẽ so sánh với từng nhãn `case` và tìm thấy sự trùng khớp ở `case 4`, do đó in ra "Thursday".

**Lưu ý:**

- Biểu thức trong câu lệnh `switch` phải trả về một giá trị nguyên hoặc một giá trị có thể chuyển đổi sang kiểu nguyên.
- Các nhãn `case` phải là các hằng số hoặc biểu thức hằng số.
- Sử dụng `break` để ngăn chặn việc "rơi qua" các `case` khác ngoài ý muốn.
- Nhãn `default` không bắt buộc nhưng nên được sử dụng để xử lý các trường hợp không khớp với bất kỳ `case` nào.

Việc sử dụng cấu trúc `switch` giúp mã nguồn trở nên rõ ràng và dễ bảo trì hơn khi cần kiểm tra nhiều giá trị của cùng một biểu thức.

# Chi tiết hơn về câu lệnh `switch`

## Phạm vi của `case`

Các nhãn `case` phải là duy nhất trong một câu lệnh `switch`. Tuy nhiên, bạn có thể lồng các câu lệnh `switch` bên trong nhau, và các nhãn `case` trong các câu lệnh `switch` lồng nhau có thể trùng nhau.

## Kiểu dữ liệu được hỗ trợ

Trong C, biểu thức trong câu lệnh `switch` phải có kiểu số nguyên (ví dụ: `int`, `char`, `short`, `long`) hoặc kiểu liệt kê (`enum`). `float` và `double` không được phép.

## Sự "rơi qua" (Fall-through)

Như đã đề cập, nếu bạn bỏ qua `break` ở cuối một `case`, việc thực thi sẽ "rơi qua" `case` tiếp theo. Đôi khi, đây là điều bạn muốn, nhưng thường là một lỗi.

Ví dụ về "rơi qua" có chủ ý:

```c
#include <stdio.h>

int main() {
    int month = 2;
    int days;
    switch (month) {
        case 1:
        case 3:
        case 5:
        case 7:
        case 8:
        case 10:
        case 12:
            days = 31;
            break;
        case 4:
        case 6:
        case 9:
        case 11:
            days = 30;
            break;
        case 2:
            days = 28; // Không xét năm nhuận
            break;
        default:
            printf("Tháng không hợp lệ\n");
            return 1;
    }
    printf("Tháng %d có %d ngày.\n", month, days);
    return 0;
}
```

Trong ví dụ này, các tháng có cùng số ngày được nhóm lại với nhau để tránh lặp lại code.

## `default` không phải lúc nào cũng là cuối cùng

Mặc dù thông thường `default` được đặt ở cuối câu lệnh `switch`, nhưng nó có thể xuất hiện ở bất kỳ đâu. Tuy nhiên, nếu `default` không phải là `case` cuối cùng, bạn cần đảm bảo có một câu lệnh `break` để tránh "rơi qua" vào các `case` khác.

## Sử dụng `enum` với `switch`

Sử dụng kiểu `enum` với `switch` có thể làm cho code của bạn dễ đọc và bảo trì hơn:

```c
#include <stdio.h>

typedef enum {
    RED,
    GREEN,
    BLUE
} Color;

int main() {
    Color myColor = GREEN;
    switch (myColor) {
        case RED:
            printf("Màu đỏ\n");
            break;
        case GREEN:
            printf("Màu xanh lá cây\n");
            break;
        case BLUE:
            printf("Màu xanh dương\n");
            break;
        default:
            printf("Màu không xác định\n");
    }
    return 0;
}
```

# Các lỗi thường gặp và cách tránh

1.  **Quên `break`:** Đây là lỗi phổ biến nhất khi sử dụng `switch`. Luôn kiểm tra kỹ xem bạn đã thêm `break` vào cuối mỗi `case` (trừ khi bạn có ý định "rơi qua").

2.  **Sử dụng sai kiểu dữ liệu:** Đảm bảo rằng biểu thức trong `switch` và các giá trị trong `case` có kiểu dữ liệu tương thích (thường là số nguyên hoặc `enum`).

3.  **Không có `default`:** Mặc dù không bắt buộc, việc thiếu `default` có thể khiến chương trình của bạn không xử lý được các giá trị không mong muốn. Hãy luôn cân nhắc việc thêm một `default` để xử lý các trường hợp ngoại lệ.

4.  **Nhầm lẫn giữa `=` và `==` trong `case`:** Các nhãn `case` sử dụng hằng số, không phải biểu thức điều kiện. Bạn không thể sử dụng `case x == 5:` mà phải sử dụng `case 5:`.

# Khi nào nên sử dụng `switch`?

- Khi bạn có một biến hoặc biểu thức mà bạn muốn so sánh với một số lượng lớn các giá trị hằng.
- Khi bạn muốn code của mình dễ đọc và bảo trì hơn so với việc sử dụng một loạt các câu lệnh `if...else if`.
- Khi hiệu suất là một yếu tố quan trọng (trong một số trường hợp, `switch` có thể nhanh hơn so với `if...else if`).

# Kết luận

Câu lệnh `switch` là một công cụ mạnh mẽ trong C để kiểm soát luồng chương trình dựa trên giá trị của một biểu thức. Bằng cách hiểu rõ cú pháp, cách hoạt động và các lỗi thường gặp, bạn có thể sử dụng `switch` một cách hiệu quả để viết code rõ ràng, dễ bảo trì và hiệu quả.

# Tổng kết

Tóm lại, cấu trúc `if-else` và câu lệnh `switch` là những công cụ quan trọng để kiểm soát luồng thực thi của chương trình dựa trên các điều kiện và giá trị khác nhau. `if-else` phù hợp với các điều kiện phức tạp và phạm vi rộng, trong khi `switch` tối ưu cho việc so sánh một biến với nhiều giá trị cụ thể. Việc nắm vững và áp dụng linh hoạt hai cấu trúc này giúp viết code rõ ràng, hiệu quả và dễ bảo trì hơn.
