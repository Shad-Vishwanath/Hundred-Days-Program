# LeetCode 744: Find Smallest Letter Greater Than Target

## Question
You are given an array of characters `letters` that is sorted in non-decreasing order, and a character `target`. There are at least two distinct characters in `letters`. Return the smallest character in `letters` that is lexicographically greater than `target`. If such a character does not exist, return the first character in `letters`.

## Approach
1. If target is greater than or equal to the last element `letters[letters.length - 1]`, return `letters[0]` (circular wrap-around condition).
2. Run binary search with `left = 0` and `right = letters.length - 1`.
3. If `letters[mid] > target`, `mid` is a potential answer, search left side: `right = mid - 1`.
4. Else (`letters[mid] <= target`), search right side: `left = mid + 1`.
5. Return `letters[left]`.

## Solution (Java)
```java
class Solution {
    public char nextGreatestLetter(char[] letters, char target) {
        int left = 0, right = letters.length - 1;
        if (target >= letters[right]) return letters[0];

        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (letters[mid] > target) {
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        }
        return letters[left];
    }
}
```
## Complexity Analysis
Time Complexity: O(log N) — Standard binary search over array length.  
Space Complexity: O(1) — Auxiliary variables only.
