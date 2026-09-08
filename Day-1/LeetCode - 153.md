# LeetCode 153: Find Minimum in Rotated Sorted Array

## Question
Given the sorted rotated array `nums` of unique elements, return the minimum element of this array. You must write an algorithm that runs in $O(\log n)$ time.

## Approach
1. Key observation: Compare `nums[mid]` with `nums[right]`.
2. If `nums[mid] > nums[right]`, the minimum element must lie in the right unsorted half (`left = mid + 1`).
3. If `nums[mid] <= nums[right]`, `mid` could be the minimum or minimum is in the left half (`right = mid`).
4. Convergence occurs when `left == right`, returning `nums[left]`.

## Solution (Java)
```java
class Solution {
    public int findMin(int[] nums) {
        int left = 0, right = nums.length - 1;
        while (left < right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] > nums[right]) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }
        return nums[left];
    }
}
```

##  Complexity Analysis
Time Complexity: O(\log N) — Search space reduced by half in each iteration.  
Space Complexity: O(1) — Memory usage is constant.
