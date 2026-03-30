# 🌧️ Trapping Rain Water (Java)

## 📌 Problem Statement
Given an array `arr[]` representing the height of bars, find the total amount of water that can be trapped after raining.

---

## 💡 Approach (Two Pointer - Optimized)

We use the **two-pointer technique** to achieve:
- ⏱️ Time Complexity: `O(n)`
- 📦 Space Complexity: `O(1)`

### 🧠 Idea:
- Maintain two pointers: `left` and `right`
- Track:
  - `lfmax` → maximum height from left
  - `rtmax` → maximum height from right
- Move the pointer with smaller boundary
- Calculate trapped water at each step

---

## 🚀 Algorithm Steps

1. Initialize:
   - `l = 0`, `r = n - 1`
   - `lfmax = 0`, `rtmax = 0`
2. Traverse while `l < r`
3. Update:
   - `lfmax = max(lfmax, arr[l])`
   - `rtmax = max(rtmax, arr[r])`
4. If `lfmax < rtmax`:
   - Add `lfmax - arr[l]`
   - Move `l++`
5. Else:
   - Add `rtmax - arr[r]`
   - Move `r--`
6. Return total water

---

## ✅ Java Implementation

```java
class Solution {
    public int maxWater(int arr[]) {
        int n = arr.length;
        int l = 0, r = n - 1;
        int lfmax = 0, rtmax = 0;
        int units = 0;

        while (l < r) {
            lfmax = Math.max(lfmax, arr[l]);
            rtmax = Math.max(rtmax, arr[r]);

            if (lfmax < rtmax) {
                units += lfmax - arr[l];
                l++;
            } else {
                units += rtmax - arr[r];
                r--;
            }
        }
        return units;
    }
}

Author
 Sanjeev Sharma
