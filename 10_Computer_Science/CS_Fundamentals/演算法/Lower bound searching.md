# Lower Bound Searching

# 一句話比喻定義

搜尋的下界（Lower Bound）：在最理想的情況下，你搜尋資料所需的最少操作次數（時間複雜度）。換句話說，就算你是神，你也不可能比這個更快。

## 概念

- 在已排序序列中，找到第一個 >= x 的位置；若無，則為插入點。

## 演算法

```pseudo
function lowerBound(arr, x):
    left  = 0
    right = len(arr)        // 半開區間 [left, right)
    while left < right:
        mid = left + (right - left) // 2
        if arr[mid] < x:
            left = mid + 1         // 排除 mid 及其左側所有 < x 的元素
        else:
            right = mid            // mid 可能就是解，保留右端
    return left    // 此時 left == right == lower bound index
```

- 時間複雜度 O(log n)，空間 O(1)。迴圈不變式：答案在 [left, right)。

## 與 Upper Bound 的差異

|          | lower_bound               | upper_bound                          |     |
| -------- | ------------------------- | ------------------------------------ | --- |
| 判斷條件 | `>= x`                    | `> x`                                |     |
| 回傳值   | 第一個滿足條件的位置      | 第一個大於 `x` 的位置                |     |
| 常見用途 | 插入點、檢查 `x` 是否存在 | 計算區間內元素次數 (`cnt = ub - lb`) |     |

## 標準函式庫（範例程式碼）

### C# (.NET)

```csharp
using System;

class Program
{
    static void Main()
    {
        int[] arr = { 1, 3, 3, 5, 8 };
        int x = 3;

        // 1. 內建 Array.BinarySearch
        int idx = Array.BinarySearch(arr, x);
        if (idx < 0)
            idx = ~idx;   // 若未找到，~idx 為插入點（lower bound）
        Console.WriteLine(idx); // 1

        // 2. 自行實作 lower bound
        Console.WriteLine(LowerBound(arr, x)); // 1
    }

    static int LowerBound(int[] arr, int x)
    {
        int left = 0;
        int right = arr.Length; // 半開區間 [left, right)
        while (left < right)
        {
            int mid = left + ((right - left) >> 1);
            if (arr[mid] < x)
                left = mid + 1;
            else
                right = mid;
        }
        return left; // lower bound index
    }
}
```

## 範例

arr = [1, 3, 3, 5, 8] → lower_bound(3) = 1, upper_bound(3) = 3

## 典型應用

1. LIS patience sorting。
2. 計數：upper_bound(x) - lower_bound(x)。
3. 二分搜尋優化（如最小最大值分配）。

## C# 特定實作細節

- **泛型支援**：可使用 `IComparer<T>` 自訂比較邏輯。
- **List<T> 的 BinarySearch**：

  ```csharp
  using System;
  using System.Collections.Generic;

  class Program
  {
      static void Main()
      {
          List<int> list = new List<int> { 1, 3, 3, 5, 8 };
          int x = 3;
          int idx = list.BinarySearch(x);
          if (idx < 0) idx = ~idx;
          Console.WriteLine(idx); // 1
      }
  }
  ```

- **邊界案例**：
  - 空陣列：回傳 0（插入點）。
  - x 小於所有元素：回傳 0。
  - x 大於所有元素：回傳陣列長度。
  - 多個相等元素：回傳第一個等於 x 的索引。

## 注意事項

- 前提：序列遞增排序（降序需調整）。
- 避免溢位：mid = left + (right - left) / 2。
- 泛型容器使用 IComparer。

## 參考資料

- C++ Reference – [`std::lower_bound`](https://en.cppreference.com/w/cpp/algorithm/lower_bound)
- 《Introduction to Algorithms》, 3rd ed. (CLRS) – 9.1 Binary Search
