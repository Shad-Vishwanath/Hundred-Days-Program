# LeetCode 704: Binary Search

## Question
Given an array of integers `nums` which is sorted in ascending order, and an integer `target`, write a function to search `target` in `nums`. If `target` exists, then return its index. Otherwise, return `-1`.

## Approach
1. Initialize two pointers: `left = 0` and `right = nums.length - 1`.
2. Compute `mid = left + (right - left) / 2` to prevent potential integer overflow.
3. If `nums[mid] == target`, return `mid`.
4. If `nums[mid] < target`, shift search space right: `left = mid + 1`.
5. If `nums[mid] > target`, shift search space left: `right = mid - 1`.
6. Return `-1` if loop terminates without finding target.

## Solution (Java)
```java
class Solution {
    public int search(int[] nums, int target) {
        int low = 0;
        int high = nums.length-1;
        while(low<=high){
        int mid = low + (high - low)/2;
        if(nums[mid] == target) return mid;
        else if(nums[mid]<target) low = mid+1;
        else high = mid-1;
        }
        return -1;
    }
}
```

## Complexity Analysis
Time Complexity: O(log N) — Search space halves in each step.
Space Complexity: O(1) — Iterative approach uses constant space.
