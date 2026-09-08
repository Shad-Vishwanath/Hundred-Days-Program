# LeetCode 69: Sqrt(x)

## Question
Given a non-negative integer `x`, compute and return the square root of `x`. Since the return type is an integer, the decimal digits are truncated, and only the integer part of the result is returned.

## Approach
1. Handle edge cases `x < 2` directly.
2. Define search range `[1, x / 2]`.
3. Compute `mid` and evaluate `mid <= x / mid` (avoids integer overflow vs `mid * mid <= x`).
4. If `mid <= x / mid`, store `mid` as potential answer and try larger values (`left = mid + 1`).
5. Else, try smaller values (`right = mid - 1`).

## Solution (Java)
```java
class Solution {
    public int mySqrt(int x) {
        if (x < 2) return x;
        int left = 1, right = x / 2, ans = 0;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (mid <= x / mid) {
                ans = mid;
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        return ans;
    }
}
```

##Complexity Analysis
Time Complexity: O(log x) — Binary searching range [1, x/2].  
Space Complexity: O(1) — Auxiliary variables only.
