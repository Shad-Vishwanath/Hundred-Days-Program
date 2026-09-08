# LeetCode 35: Search Insert Position

## Question
Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

## Approach
1. Standard binary search setup with `left = 0` and `right = nums.length - 1`.
2. If `nums[mid] == target`, target exists, return `mid`.
3. If `nums[mid] < target`, move right: `left = mid + 1`.
4. If `nums[mid] > target`, move left: `right = mid - 1`.
5. When `left > right`, `left` represents the correct insertion index.

## Solution (Java)
```java
class Solution {
    public int searchInsert(int[] nums, int target) {
        int left = 0, right = nums.length - 1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] == target) return mid;
            else if (nums[mid] < target) left = mid + 1;
            else right = mid - 1;
        }
        return left;
    }
}
```

##Complexity Analysis
Time Complexity: O(log N) — Halving array space each step.  
Space Complexity: O(1) — Constant memory overhead.
