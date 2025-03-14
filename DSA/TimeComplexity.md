# Độ Phức Tạp Thời Gian (Time Complexity)

# Khái niệm cơ bản

Độ phức tạp thời gian là thước đo _số lượng phép toán_ mà một thuật toán thực hiện khi _kích thước đầu vào tăng lên_. Độ phức tạp càng lớn thì càng tốn nhiều thời gian và tài nguyên hệ thống để chạy hơn, dẫn đến tốn nhiều chi phí hơn.

> **Lưu ý**: Độ phức tạp thời gian:
>
> - Không phải thời gian thực thi chính xác của chương trình
> - Là ước lượng số lượng phép toán được thực hiện
> - Luôn phải tính độ phức tạp thời gian dựa trên trường hợp xấu nhất (worst case)
> - Giúp dự đoán cách thuật toán hoạt động với dữ liệu lớn

> **Bạn đã biết**: Trung bình máy tính xử lý được $2 \times 10^8$ phép tính trong 1s (số liệu tham khảo năm 2021, có thể thay đổi tùy cấu hình máy tính).

# Ký hiệu Big O

- Biểu thị: $O(f(n))$ với $f(n)$ là một hàm số, $n$ là kích thước đầu vào
- Mục đích: Mô tả tốc độ tăng trưởng của số lượng phép toán khi kích thước đầu vào tăng lên

# Các loại độ phức tạp phổ biến

| Độ phức tạp    | Ký hiệu       | Mô tả                                  |
| -------------- | ------------- | -------------------------------------- |
| Hằng số        | $O(1)$        | Không phụ thuộc vào kích thước đầu vào |
| Logarit        | $O(\log N)$   | Tăng chậm khi N tăng                   |
| Tuyến tính     | $O(N)$        | Tăng tuyến tính với N                  |
| Log-tuyến tính | $O(N \log N)$ | Kết hợp logarit và tuyến tính          |
| Bậc hai        | $O(N^2)$      | Tăng theo bình phương của N            |
| Hàm mũ         | $O(2^N)$      | Tăng theo cấp số nhân                  |

Đồ thị minh họa độ phức tạp với kích thước đầu vào N tăng dần.

![Alt text](https://www.ardanlabs.com/images/goinggo/183_figure1.png 'Đồ thị độ phức tạp')

# Tầm quan trọng của độ phức tạp thời gian

## 1. So sánh hiệu quả thuật toán

- Đánh giá và so sánh các giải pháp khác nhau
- Chọn thuật toán phù hợp cho từng tình huống

## 2. Dự đoán hiệu suất

- Ước tính thời gian xử lý
- Đánh giá khả năng xử lý dữ liệu lớn

## 3. Tối ưu hóa code

- Xác định điểm yếu trong code
- Cải thiện hiệu suất thuật toán

## 4. Quản lý tài nguyên

- Dự đoán nhu cầu CPU và bộ nhớ
- Lập kế hoạch phân bổ tài nguyên

## 5. Thiết kế hệ thống

- Đưa ra quyết định về kiến trúc
- Cấu trúc hệ thống hiệu quả

## 6. Khả năng mở rộng

- Đánh giá khả năng scale
- Dự đoán hiệu suất khi tăng tải

> **Độ phức tạp của thuật toán** là yếu tố quan trọng giúp **đánh giá hiệu suất** và **tối ưu hóa code**. Sự khác biệt giữa một **lập trình viên giỏi** và một **lập trình viên tốt** là khả năng hiểu và ứng dụng vào thực tế một cách hiệu quả để **giải quyết vấn đề**. Do đó, **DSA** là một trong những **môn học quan trọng nhất** trong ngành IT.

# Tính toán độ phức tạp thời gian

## 1. Quy tắc cơ bản

- Bỏ qua hằng số: $O(2N) = O(N)$
- Chỉ giữ lại thành phần lớn nhất: $O(N^2 + N) = O(N^2)$
- Biến đổi logarit: $O(\log_2 N) = O(\log N)$

## 2. Phân tích từng bước

```cpp
// Ví dụ 1: O(1)
int sum = a + b;
// - Chỉ thực hiện một phép cộng
// - Không phụ thuộc vào kích thước đầu vào
// - Độ phức tạp hằng số O(1)

// Ví dụ 2: O(N)
for(int i = 0; i < N; i++) {
    cout << i;    // Lệnh in thực hiện N lần
}
// - Vòng lặp chạy N lần
// - Mỗi lần lặp thực hiện 1 phép in
// - Tổng số phép toán: N → O(N)

// Ví dụ 3: O(N^2)
for(int i = 0; i < N; i++) {
    for(int j = 0; j < N; j++) {
        cout << i + j;    // Lệnh thực hiện N*N lần
    }
}
// - Vòng lặp ngoài chạy N lần
// - Mỗi lần của vòng ngoài, vòng trong chạy N lần
// - Tổng số phép toán: N * N = N^2 → O(N^2)
```

## 3. Một số trường hợp đặc biệt

- Vòng lặp lồng nhau: Nhân độ phức tạp
- Câu lệnh tuần tự: Lấy độ phức tạp lớn nhất
- Đệ quy: Phân tích số lần gọi đệ quy và độ phức tạp mỗi lần gọi

> Bạn nên vào trang web này để học chi tiết hơn về cách tính toán độ phức tạp thời gian: https://usaco.guide/bronze/time-comp
