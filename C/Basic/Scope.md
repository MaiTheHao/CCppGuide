# Phạm vi Biến trong C 

Trong lập trình C, phạm vi của một biến quyết định nơi nó có thể được truy cập và sử dụng. Có ba loại phạm vi chính: phạm vi cục bộ (local scope), phạm vi toàn cục (global scope) và phạm vi khối (block scope). 🌎🔍

---

## 1. Phạm vi cục bộ (Local Scope) 🔒📍📝

Biến được khai báo bên trong một hàm có phạm vi cục bộ và chỉ có thể được truy cập trong hàm đó.

## Ví dụ:

```c
void myFunction() {
    int x = 5; // Biến cục bộ
    printf("%d", x);
}

int main() {
    myFunction();
    return 0;
}
```

Nếu cố gắng truy cập biến cục bộ từ bên ngoài hàm, trình biên dịch sẽ báo lỗi:

```c
void myFunction() {
    int x = 5;
}

int main() {
    myFunction();
    printf("%d", x); // Lỗi: x không tồn tại ở đây
    return 0;
}
```

---

## 2. Phạm vi toàn cục (Global Scope) 🌍🔄📌

Biến được khai báo bên ngoài tất cả các hàm có phạm vi toàn cục và có thể được truy cập từ bất kỳ đâu trong chương trình.

## Ví dụ:

```c
int x = 5; // Biến toàn cục

void myFunction() {
    printf("%d", x);
}

int main() {
    myFunction();
    printf("%d", x);
    return 0;
}
```

Biến toàn cục có thể bị thay đổi bởi bất kỳ hàm nào trong chương trình, điều này có thể gây ra lỗi khó kiểm soát nếu không được sử dụng cẩn thận.

---

## 3. Xung đột tên biến ⚠️🚨🔍

Khi một biến cục bộ có cùng tên với một biến toàn cục, biến cục bộ sẽ được ưu tiên trong phạm vi của nó.

## Ví dụ:

```c
int x = 5; // Biến toàn cục

void myFunction() {
    int x = 22; // Biến cục bộ
    printf("%d\n", x); // In giá trị của biến cục bộ
}

int main() {
    myFunction();
    printf("%d\n", x); // In giá trị của biến toàn cục
    return 0;
}
```

Việc sử dụng biến toàn cục có cùng tên với biến cục bộ có thể gây nhầm lẫn, do đó nên hạn chế. ⚠️🔍

---

## 4. Phạm vi khối (Block Scope) 🏗️📦🛠️

Phạm vi khối đề cập đến các biến được khai báo trong một cặp dấu ngoặc nhọn `{}`. Biến này chỉ tồn tại trong khối chứa nó.

## Ví dụ:

```c
int main() {
    {
        int y = 10; // Biến có phạm vi khối
        printf("%d\n", y);
    }
    printf("%d\n", y); // Lỗi: y không tồn tại ở đây
    return 0;
}
```

---

## 5. Tham số hàm (Function Parameters) 🎯📌

Tham số hàm được coi như các biến cục bộ bên trong hàm và không thể truy cập từ bên ngoài.

## Ví dụ:

```c
#include <stdio.h>

int add(int a, int b) {
    return a + b;
}

int main() {
    int sum = add(5, 10);
    printf("Tong = %d\n", sum);
    return 0;
}
```

Trong ví dụ trên, `a` và `b` là các tham số của hàm `add()` và chỉ tồn tại bên trong hàm này.

---

## 6. Thay đổi biến toàn cục từ hàm 🔄⚙️🔥

Một hàm có thể thay đổi giá trị của biến toàn cục bằng cách tham chiếu trực tiếp đến nó.

## Ví dụ:

```c
int x = 5; // Biến toàn cục

void myFunction() {
    x++; // Tăng giá trị của x
    printf("%d\n", x);
}

int main() {
    myFunction();
    printf("%d\n", x);
    return 0;
}
```

Sau khi gọi `myFunction()`, giá trị của `x` sẽ thay đổi vĩnh viễn. 🔄💡

---

## 7. Kết luận 🏁🎯📌

- **Biến cục bộ** giúp chương trình dễ hiểu, tránh xung đột và quản lý bộ nhớ tốt hơn.
- **Biến toàn cục** có thể hữu ích trong một số trường hợp nhưng nên hạn chế sử dụng để tránh lỗi không mong muốn.
- **Phạm vi khối** giúp giới hạn biến trong một phạm vi cụ thể, tránh lỗi truy cập ngoài phạm vi.
- **Tham số hàm** hoạt động như biến cục bộ và chỉ có thể được sử dụng bên trong hàm.
- **Đặt tên biến hợp lý** giúp tránh xung đột và làm mã dễ đọc hơn.

Việc hiểu rõ phạm vi biến giúp lập trình viên kiểm soát tốt hơn cách dữ liệu được sử dụng trong chương trình. 🎯📌
