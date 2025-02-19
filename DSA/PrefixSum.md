## VẤN ĐỀ

Bạn đã từng giải bài toán tính tổng đoạn con của một dãy số nguyên chưa?

> Ví dụ: cho mảng `a = [5, 5, 10, 20, 30]`<br/>Nhiệm vụ: Tính tổng đoạn con từ vị trí đầu tiên đến vị trí thứ 1, 3, 4 _(vị trí bắt đầu từ 0)_, tức là 3 truy vấn (query).

Vấn đề là làm thế nào để giải quyết bài toán này một cách hiệu quả nhất với **1 tỷ truy vấn (query)**?

## CÁCH TIẾP CẬN CƠ BẢN

### Sử dụng vòng lặp để duyệt qua từng phần tử của mảng và cộng dồn lại cho từng truy vấn:

1. Duyệt bắt đầu từ vị trí đầu tiên.
2. Kết thúc ở vị trí cần tính tổng.
3. Cộng dồn các giá trị của các phần tử lại với nhau.
> 💡 Đây là cách tiếp cận cơ bản và dễ hiểu nhất

```c
#include <stdio.h>
// Định nghĩa hàm để tính tổng đoạn con
/*
    a: mảng số nguyên
    size: kích thước của mảng
    start: vị trí bắt đầu
    end: vị trí kết thúc
*/
int sum(int *a, int size, int start, int end)
{
    int sum = 0;

    // Vòng lặp để cộng dồn các phần tử của mảng
    for (int i = start; i <= end; i++)
    {
        sum += a[i];
    }
    return sum;
}

int main() {
    // Khởi tạo mảng số nguyên
    int a[] = {5, 5, 10, 20, 30};
    int size = 5;

    // In ra kết quả
    printf("Sum from 0 to 1: %d\n", sum(a, size, 0, 1));  // 10
    printf("Sum from 0 to 3: %d\n", sum(a, size, 0, 3));  // 40
    printf("Sum from 0 to 4: %d\n", sum(a, size, 0, 4));  // 70

    return 0;
}
```
- **Ưu điểm:** _Dễ hiểu, dễ cài đặt._
- **Nhược điểm:**
    - _Độ phức tạp O(n) trong việc tính tổng đoạn con._
    - _Nếu đề bài yêu cầu 1 tỷ truy vấn (query) thì cách tiếp cận này không hiệu quả._

### Nếu dùng cách trên để giải quyết 1 tỷ truy vấn thì, máy tính cần xử lí:

-   Với kích thước mảng ban đầu (5) =>**10^9 \* 5 = 5 tỷ phép toán ~ 25s**
-   Nếu tăng kích thước mảng lên 10^6 => __10^9 \* 10^6 = 10^15 phép toán ~ 5*10^6s__.

## VẬY LÀM THẾ NÀO ĐỂ GIẢI QUYẾT VẤN ĐỀ QUÁ THỜI GIAN VỚI 1 TỶ QUERY?

Để giải quyết vấn đề này, chúng ta cần sử dụng một kỹ thuật tối ưu hóa gọi là **Prefix Sum**.

# PREFIX SUM

**Prefix Sum** (_Tổng tích lũy_) là kỹ thuật lập trình giúp tính nhanh tổng các phần tử trong một đoạn của mảng bằng cách sử dụng mảng đã được **tiền xử lý** gọi là mảng **cộng dồn**. Nhờ **tiền xử lý**, ta có thể truy vấn tổng đoạn con trong _O(1)_ thay vì _O(n)_ như cách trên.

Trong nội dung này, chúng ta chỉ giới thiệu và hướng dẫn về **Prefix Sum 1D** vì tính dễ hiểu và đặt nền móng cho các loại khác. Các loại khác bao gồm:

- **Prefix Sum 2D**: Áp dụng cho mảng hai chiều.
- **Prefix Sum 3D**: Áp dụng cho mảng ba chiều.
- **Prefix Sum với cập nhật động**: Sử dụng các cấu trúc dữ liệu như Fenwick Tree hoặc Segment Tree để hỗ trợ cập nhật động.

Bắt đầu với **Prefix Sum 1D** sẽ giúp bạn nắm vững khái niệm cơ bản trước khi tiến tới các kỹ thuật phức tạp hơn.

## ĐỊNH NGHĨA

Giả sử bạn có một mảng số nguyên:

```
A = [a₀, a₁, a₂, ..., aₙ₋₁]
```

Mảng **cộng dồn** của A được định nghĩa là một mảng chứa tổng tích lũy của các phần tử từ đầu đến mỗi vị trí i:

```
P[i] = a₀ + a₁ + ... + aᵢ, với i = 0, 1, 2, ..., n-1
```

Điều này có nghĩa là mỗi phần tử **P[i]** trong **mảng cộng dồn** là tổng của tất cả các phần tử từ **a₀** đến **aᵢ** trong mảng A.

## CÁCH THIẾT LẬP MẢNG CỘNG DỒN

Một cách đơn giản để tính mảng cộng dồn là:

1. Khởi tạo: `P[0] = A[0]`
2. Với mỗi `i` từ 1 đến n-1, thực hiện:
    ```
    P[i] = P[i-1] + A[i]
    ```

Thời gian thực hiện thuật toán này là O(n).

## VÍ DỤ

Giả sử mảng ban đầu là:

```
A = [1, 2, 3, 4, 5]
```

Quá trình tính mảng cộng dồn:

```
Giả định mảng cộng dồn là P = [0, 0, 0, 0, 0]:

1. P[0] = A[0] = 1
2. Dùng vòng lặp `for` với `i` bắt đầu từ `1` tới `4`:
    - i = 1: P[1] = P[0] + A[1] = 1 + 2 = 3
    - i = 2: P[2] = P[1] + A[2] = 3 + 3 = 6
    - i = 3: P[3] = P[2] + A[3] = 6 + 4 = 10
    - i = 4: P[4] = P[3] + A[4] = 10 + 5 = 15
```

Vậy mảng prefix là:

```
P = [1, 3, 6, 10, 15]
``` 

## ỨNG DỤNG

### Truy vấn tổng đoạn con mảng  

Sau khi có mảng cộng dồn, tổng của đoạn từ `i` đến `j` có thể được tính bằng công thức:

```
sum(i, j) = P[j] - P[i-1], với i > 0
sum(i, j) = P[j], với i = 0
```

> Chúng ta sẽ sử dụng hai mảng `A` và `P` đã đề cập ở trên.

Ví dụ:  

#### Tính tổng đoạn con từ vị trí `1` đến `3`  
(Tức là từ phần tử thứ `2` đến phần tử thứ `4` trong mảng `A`)

```plaintext
sum(1, 3) = P[3] - P[1 - 1] = 10 - 1 = 9
```

#### Tính tổng đoạn con từ vị trí `0` đến `4`  
(Tức là từ phần tử đầu tiên đến phần tử cuối cùng trong mảng `A`)

```plaintext
sum(0, 4) = P[4] = 15 - 0 = 15
```

## GIẢI QUYẾT VẤN ĐỀ BAN ĐẦU VỚI 1 TỶ QUERY
### Áp dụng kiến thức mới biết về prefix sum vào bài toán ban đầu:

```c
#include <stdio.h>

int main(){
    int a[] = {5, 5, 10, 20, 30};
    int P[] = {0, 0, 0, 0, 0};
    int arr_size = 5;

    // Tính mảng cộng dồn bằng các bước đã cho
    P[0] = a[0];
    for(int i = 1; i < arr_size; i++){
        P[i] = P[i-1] + a[i];
    }

    // In mảng cộng dồn để có cái nhìn trực quan
    for(int i = 0; i < arr_size; i++){
        printf("%d ", P[i]);
    }
    printf("\n");

    // Khi tìm từ phần tử đầu tiên tới i, ta chỉ cần lấy P[i], vì P[i] chính là tổng của các phần tử từ 0 đến i
    // Khi tìm từ phần tử i đến j, ta cần lấy P[j] - P[i]                           
    printf("Sum from 0 to 1: %d\n", P[1]);  // 10
    printf("Sum from 0 to 3: %d\n", P[3]);  // 40
    printf("Sum from 0 to 4: %d\n", P[4]);  // 70

    // Hãy chạy mã dưới để xem ví dụ với công thức sum(i, j) = P[j] - P[i-1], (i > 0)
    // printf("Sum from 1 to 3: %d\n", P[3] - P[1 - 1]);  // 35
    // printf("Sum from 2 to 4: %d\n", P[4] - P[2 - 1]);  // 60
    // printf("Sum from 1 to 4: %d\n", P[4] - P[1 - 1]);  // 65

    return 0;
}
```
### Độ phức tạp:
- Tiền xử lý mảng cộng dồn: O(n) (duyệt qua mảng một lần để tính tổng tích lũy).
- Mỗi truy vấn tính tổng đoạn con: O(1) (chỉ cần một phép trừ trên mảng cộng dồn).
- Ba lần truy vấn tổng đoạn con: O(1) (vì vẫn chỉ thực hiện ba phép trừ đơn giản).
- Tổng độ phức tạp: O(n) (tiền xử lý) + O(1) (mỗi truy vấn) → O(n) + O(q) ~ O(n + q) (với q là số truy vấn).

| Kích thước mảng (n) | Số truy vấn (q) | Tổng số phép toán ước tính | Thời gian ước tính |
|---------------------|-----------------|-----------------------------|---------------------|
| n bất kỳ            | q truy vấn      | O(n + q)                    | ~ O(n + q) / 2 * 10^8 |
| n = 5               | 10^9 truy vấn    | 5 + 10^9 = 1 tỷ lẻ 5 phép toán  | 5s |
| n = 10^6             | 10^9 truy vấn    | 10^6 + 10^9 = 1 tỷ 1 triệu phép toán  | 5.005s |

💡 Nhận xét:
- Ưu điểm: Phương pháp này rất hiệu quả khi có nhiều truy vấn vì mỗi truy vấn chỉ mất O(1) thời gian.
- Nhược điểm: Khi n và q đều rất lớn, có thể cần tối ưu hơn bằng các cấu trúc như Sparse Table (cho truy vấn min/max) hoặc Fenwick Tree / Segment Tree (cho cập nhật động).

- [**Bạn có thể tham khảo chi tiết hơn tại đây**](https://usaco.guide/silver/prefix-sums)
- [**Bạn có thể tìm hiểu nhiều hơn về Prefix Sum 2D và nhiều thứ thú vị tại đây**](https://usaco.guide/silver/more-prefix-sums)