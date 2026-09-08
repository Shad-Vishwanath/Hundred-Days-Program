# LeetCode 34: Find First and Last Position of Element in Sorted Array

## Question
Given an array of integers `nums` sorted in non-decreasing order, find the starting and ending position of a given `target` value. If `target` is not found in the array, return `[-1, -1]`.

## Approach
1. Use two separate binary searches: one to find the first occurrence (left bound) and another for the last occurrence (right bound).
2. For first occurrence: when `nums[mid] == target`, record position and continue searching left (`right = mid - 1`).
3. For last occurrence: when `nums[mid] == target`, record position and continue searching right (`left = mid + 1`).

## Solution (Java)
```java
class Solution {
    public int lowerbound(int[] nums, int x){
        int low = 0;
        int high = nums.length-1;
        int ans = -1;
        while(low<=high){
            int mid = low +(high-low)/2;
            if(nums[mid]==x){
                ans = mid;
                high = mid-1;
            }
            else if(nums[mid] < x) low = mid+1;
            else high = mid-1;
        }
        return ans;

    }

    public int upperbound(int[] nums, int x){
        int low = 0;
        int high = nums.length-1;
        int ans = -1;
        while(low<=high){
            int mid = low +(high-low)/2;
            if(nums[mid]==x){
                ans = mid;
                low = mid+1;
            }
            else if(nums[mid] < x) low = mid+1;
            else high = mid-1;
        }
        return ans;
    }

    public int[] searchRange(int[] nums, int target) {
        return new int[]{lowerbound(nums,target),upperbound(nums,target)};
    }
}
```

## Complexity Analysis
Time Complexity: O(log N) — Runs two standard binary searches.  
Space Complexity: O(1) — In-place pointer manipulation.
