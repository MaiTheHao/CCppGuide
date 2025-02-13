## Giới thiệu
Thuật toán brute force (vét cạn), còn được gọi là **Basic Complete Search** hoặc **"code trâu"** trong cộng đồng lập trình Việt Nam, là một chiến lược tìm kiếm đơn giản, toàn diện, khám phá có hệ thống mọi khả năng để tìm ra câu trả lời cho vấn đề.

### "Code trâu" là gì?
"Code trâu" là thuật ngữ dân gian chỉ cách lập trình:
- 🔸 Sử dụng sức mạnh phần cứng thay vì tối ưu thuật toán
- 🔸 Giải quyết vấn đề theo cách trực tiếp, đơn giản nhất
- 🔸 Thường dùng các vòng lặp lồng nhau thay vì thuật toán phức tạp
- 🔸 Ưu tiên tính dễ hiểu và dễ maintain hơn hiệu suất

> 💡 **Châm ngôn code trâu**: "If it looks stupid but works, it ain't stupid"

### Ví dụ tìm kiếm số trong mảng
So sánh cách tiếp cận brute force với tối ưu khi tìm số x trong mảng đã sắp xếp:

```c
// Code trâu - Linear Search O(n)
int bruteForceSearch(int arr[], int n, int x) {
    for(int i = 0; i < n; i++) {
        if(arr[i] == x) return i;
    }
    return -1;
}

// Code tối ưu - Binary Search O(log n)
int binarySearch(int arr[], int n, int x) {
    int left = 0, right = n-1;
    while(left <= right) {
        int mid = (left + right)/2;
        if(arr[mid] == x) return mid;
        if(arr[mid] < x) left = mid + 1;
        else right = mid - 1;
    }
    return -1;
}
```

Ví dụ trên cho thấy:
- Brute force (Linear Search):
    - Độ phức tạp trường hợp xấu nhất: **O(n)** (phần tử ở cuối hoặc không tồn tại)
    - Độ phức tạp trường hợp tốt nhất: **O(1)** (phần tử ở đầu mảng)
    - Độ phức tạp trung bình: **O(n/2)** ≈ **O(n)** (hãy xem lại quy tắc tính toán độ phức tạp ở [đây](TimeComplexity.md))
- Binary Search:
    - Độ phức tạp trường hợp xấu nhất: **O(log n)** (phần tử ở ngoài cùng)
    - Độ phức tạp trường hợp tốt nhất: **O(1)** (phần tử ở giữa mảng)
    - Độ phức tạp trung bình: **O(log n)**


## Đặc điểm chính

### Phương pháp liệt kê có hệ thống
- 🔸 Xem xét tất cả các giải pháp khả thi
- 🔸 Kiểm tra từng tùy chọn theo trình tự nhất định  
- 🔸 Đảm bảo không bỏ sót bất kỳ trường hợp nào

### Phạm vi áp dụng
- ✅ Thích hợp cho các bài toán có không gian trạng thái nhỏ
- ✅ Dễ dàng thực hiện trong thời gian hợp lý
- ⚠️ [Độ phức tạp thời gian](TimeComplexity.md) thường thuộc nhóm O(n!) hoặc O(2ⁿ)

### Không áp dụng kỹ thuật tối ưu hóa
- 🔸 Không loại trừ bất kỳ khả năng nào trước khi thử nghiệm
- 🔸 Không sử dụng phương pháp cắt tỉa để giảm số lần kiểm tra
- 🔸 Xem xét toàn bộ không gian trạng thái một cách toàn diện

## Ví dụ thực tế
Hãy xem một ví dụ về bài toán tìm khoảng cách Euclid lớn nhất:

> **Đề bài**: Cho N điểm trên mặt phẳng tọa độ (3≤N≤5000). Tìm bình phương khoảng cách Euclid lớn nhất giữa hai điểm bất kỳ.
>
> **Input**: 
> - Dòng 1: số nguyên N
> - Dòng 2: N số nguyên x₁,x₂,...,xₙ (-1000≤xᵢ≤1000)
> - Dòng 3: N số nguyên y₁,y₂,...,yₙ (-1000≤yᵢ≤1000)
>
> **Output**: Một số nguyên - bình phương khoảng cách Euclid lớn nhất

So sánh hai cách tiếp cận:

```c
// Cách 1: Brute Force - O(N²)
long long bruteForceMaxDist(int x[], int y[], int n) {
    long long max_dist = 0;
    for(int i = 0; i < n; i++) {
        for(int j = i + 1; j < n; j++) {
            long long dx = x[j] - x[i];
            long long dy = y[j] - y[i];
            max_dist = max(max_dist, dx*dx + dy*dy);
        }
    }
    return max_dist;
}

// Cách 2: Convex Hull + Rotating Calipers - O(N log N)
// Đừng lo lắng nếu bạn chưa hiểu code này, vì kiến thức này rất nâng cao
long long optimizedMaxDist(int x[], int y[], int n) {
    Point hull[5001];
    int m = convexHull(x, y, n, hull);
    return rotatingCalipers(hull, m);
}
```

### Nhận xét:
- Brute Force: 
    - Duyệt qua mọi cặp điểm có thể
    - Độ phức tạp O(N²)
    - Code đơn giản, dễ hiểu
    - Phù hợp với N ≤ 5000

- Tối ưu:
    - Sử dụng thuật toán hình học nâng cao
    - Độ phức tạp O(N log N)
    - Code phức tạp hơn
    - Phù hợp với N lớn

    > 💡 **Điều cần suy ngẫm**: Đó bạn thấy sự khác biệt giữa một lập trình viên tốt và giỏi chưa? Đó là một kho tàng kiến thức đồ sộ để xây dựng hệ thống hiệu quả và tiết kiệm chi phí

## Ưu điểm và nhược điểm

### Ưu điểm
- ✅ Đảm bảo tìm ra giải pháp đúng
- ✅ Dễ hiểu và dễ cài đặt
- ✅ Phù hợp với vấn đề có không gian nhỏ
- ✅ Dùng làm chuẩn để so sánh với các thuật toán khác

### Nhược điểm
- ❌ Hiệu suất kém với bộ dữ liệu lớn
- ❌ Độ phức tạp thời gian cao (thường là O(n!) hoặc O(2^n))
- ❌ Tiêu tốn nhiều tài nguyên hệ thống
- ❌ Không phù hợp với ứng dụng thời gian thực

## Kết luận
Brute Force là thuật toán cơ bản nhất trong khoa học máy tính. Mặc dù đơn giản và kém hiệu quả, nó vẫn là điểm khởi đầu tốt để hiểu vấn đề và phát triển các giải pháp tối ưu hơn.

> 💡 **Mẹo**: Trước khi áp dụng các thuật toán phức tạp, hãy xem xét liệu Brute Force có đủ tốt cho vấn đề của bạn không. Nhưng nếu đã có giải pháp thì đừng dùng Brute Force nhé.