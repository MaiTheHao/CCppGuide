# 1. Giới thiệu về chuỗi trong C

Trong ngôn ngữ lập trình C, chuỗi không phải là một kiểu dữ liệu riêng biệt như trong các ngôn ngữ khác (Python, Java, v.v.). Thay vào đó, chuỗi trong C được biểu diễn dưới dạng một mảng các ký tự (`char array`) kết thúc bằng ký tự null (`\0`).

Ví dụ một chuỗi trong C:

```c
char str[] = "Hello, world!";
```

Ở đây, `str` là một mảng ký tự chứa nội dung "Hello, world!" và kết thúc bằng ký tự `\0`.

Vì luôn kết thúc bằng `\0` nên độ dài của chuỗi luôn phải lớn hơn số ký tự thực tế 1. Ví dụ: chuỗi "die" dài 3 ký tự, nhưng cần một mảng có kích thước ít nhất 4 để chứa `\0`.

Chuỗi trong C có thể được sử dụng trong nhiều ứng dụng như xử lý văn bản, lưu trữ thông tin người dùng, hoặc giao tiếp với tệp tin. Do C không có kiểu dữ liệu chuỗi riêng, lập trình viên phải cẩn thận khi thao tác trên chuỗi để tránh lỗi bộ nhớ.

---

# 2. Khai báo và khởi tạo chuỗi

Có nhiều cách để khai báo chuỗi trong C:

## a) Khai báo bằng mảng ký tự

```c
char str1[] = "Hello";
```

## b) Khai báo bằng con trỏ ký tự

```c
char *str2 = "Hello";
```

Lưu ý: `str2` trỏ đến một vùng nhớ không thể thay đổi được.

## c) Khai báo và nhập từ bàn phím

```c
char str3[100];
printf("Nhập chuỗi: ");
gets(str3); // Không khuyến khích sử dụng do có thể gây tràn bộ nhớ
```

Cách tốt hơn để nhập chuỗi là sử dụng `fgets`:

```c
fgets(str3, sizeof(str3), stdin);
```

- **str3**: mảng chứa chuỗi nhập vào.
- **sizeof(str3)**: kích thước tối đa của mảng.
- **`stdin`**: luồng nhập từ bàn phím.

`fgets()` an toàn hơn `gets()` vì nó giới hạn số ký tự nhập vào, giúp tránh lỗi tràn bộ nhớ.

# 3. Tránh lỗi nhập bị bỏ qua do `\n`

Một lỗi phổ biến khi sử dụng `scanf()` để nhập chuỗi hoặc ký tự là `\n` còn sót lại trong bộ đệm, dẫn đến việc bỏ qua nhập liệu sau đó. Để khắc phục, ta có thể sử dụng `scanf("%c%*c", &biến);`, trong đó `%*c` giúp loại bỏ ký tự `\n` dư thừa.

Ví dụ:

```c
char name[50];
int age;
printf("Nhập tuổi: ");
scanf("%d%*c", &age); // %*c giúp loại bỏ \n còn lại
printf("Nhập tên: ");
fgets(name, sizeof(name), stdin);
printf("Tên: %s, Tuổi: %d\n", name, age);
```

Nếu không sử dụng `%*c`, các lệnh nhập sau sẽ tự động nhận ký tự `\n`, giúp tránh lỗi sót lại trong bộ đệm:

- **gets**
- **fgets**

# 4. Các thao tác trên chuỗi

## a) In chuỗi ra màn hình

```c
printf("%s", str);
```

Chuỗi có thể in ra trực tiếp bằng `printf()`, nhưng cần cẩn thận với các ký tự đặc biệt.

## b) Sao chép chuỗi

```c
char src[] = "Hello";
char dest[20];
strcpy(dest, src); // Sao chép nội dung src vào dest
```

Lưu ý rằng `strcpy()` không kiểm tra kích thước mảng đích, có thể gây tràn bộ nhớ.

## c) Nối chuỗi

```c
char str4[20] = "Hello, ";
char str5[] = "world!";
strcat(str4, str5);
printf("%s", str4); // Kết quả: "Hello, world!"
```

Sử dụng `strncat()` để đảm bảo không vượt quá kích thước mảng đích.

## d) So sánh chuỗi

```c
if (strcmp(str1, str2) == 0) {
    printf("Hai chuỗi giống nhau");
} else {
    printf("Hai chuỗi khác nhau");
}
```

Có thể dùng `strncmp()` nếu chỉ muốn so sánh một số ký tự đầu tiên.

---

# 5. Một số hàm xử lý chuỗi quan trọng

| Hàm                      | Chức năng                                     |
| ------------------------ | --------------------------------------------- |
| `strlen(str)`            | Trả về độ dài chuỗi (không tính `\0`)         |
| `strcpy(dest, src)`      | Sao chép chuỗi `src` vào `dest`               |
| `strncpy(dest, src, n)`  | Sao chép tối đa `n` ký tự từ `src` vào `dest` |
| `strcat(dest, src)`      | Nối chuỗi `src` vào `dest`                    |
| `strncat(dest, src, n)`  | Nối tối đa `n` ký tự của `src` vào `dest`     |
| `strcmp(str1, str2)`     | So sánh hai chuỗi                             |
| `strncmp(str1, str2, n)` | So sánh `n` ký tự đầu tiên của hai chuỗi      |
| `strchr(str, c)`         | Tìm ký tự `c` trong chuỗi `str`               |
| `strstr(str1, str2)`     | Tìm chuỗi con `str2` trong `str1`             |

Ngoài ra, còn có thể dùng `sprintf()` để định dạng chuỗi một cách linh hoạt.

---

# 6. Lưu ý khi làm việc với chuỗi trong C

- Chuỗi trong C luôn kết thúc bằng `\0`, nên cần đảm bảo đủ kích thước mảng chứa chuỗi.
- Khi dùng con trỏ chuỗi (`char *str = "Hello";`), không thể thay đổi nội dung của chuỗi.
- Dùng `fgets()` thay vì `gets()` để tránh lỗi tràn bộ nhớ.
- Khi thao tác trên chuỗi cần kiểm tra kích thước bộ nhớ để tránh lỗi buffer overflow.
