# LeetCode 278: First Bad Version

## Question
You are a product manager and currently leading a team to develop a new product. Since the latest version fails the quality check, all the versions after a bad version are also bad. Find the first bad version given an API `isBadVersion(version)`.

## Approach
1. Search range is `[1, n]`.
2. If `isBadVersion(mid)` is `true`, `mid` could be the first bad version or a version after it. Keep `mid` in range: `right = mid`.
3. If `isBadVersion(mid)` is `false`, first bad version must be strictly after `mid`: `left = mid + 1`.
4. Loop until `left == right`, which converges to the first bad version.

## Solution (Java)
```java
/* The isBadVersion API is defined in the parent class VersionControl.
      boolean isBadVersion(int version); */

public class Solution extends VersionControl {
    public int firstBadVersion(int n) {
        int left = 1, right = n;
        while (left < right) {
            int mid = left + (right - left) / 2;
            if (isBadVersion(mid)) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return left;
    }
}
```

## Complexity Analysis
Time Complexity: O(log N) — Number of API calls is logarithmic.  
Space Complexity: O(1) — No extra memory allocated.
