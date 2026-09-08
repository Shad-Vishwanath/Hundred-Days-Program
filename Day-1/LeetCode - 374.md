# LeetCode 374: Guess Number Higher or Lower

## Question
We are playing the Guess Game. The game is as follows: I pick a number from `1` to `n`. You have to guess which number I picked. Every time you guess wrong, I will tell you whether the number picked is higher or lower than your guess via API `guess(int num)`.

## Approach
1. Perform standard binary search on range `[1, n]`.
2. Call `guess(mid)`.
3. If result is `0`, return `mid`.
4. If result is `-1`, picked number is lower: `right = mid - 1`.
5. If result is `1`, picked number is higher: `left = mid + 1`.

## Solution (Java)
```java
/** 
 * Forward declaration of guess API.
 * @param  num   your guess
 * @return 	     -1 if num is higher than the picked number
 *			      1 if num is lower than the picked number
 *               otherwise return 0
 * int guess(int num);
 */

public class Solution extends GuessGame {
    public int guessNumber(int n) {
        int left = 1, right = n;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            int res = guess(mid);
            if (res == 0) return mid;
            else if (res == -1) right = mid - 1;
            else left = mid + 1;
        }
        return -1;
    }
}
```

##  Complexity Analysis
Time Complexity: O(log N) — Binary reduction of range [1, n].  
Space Complexity: O(1) — Constant spatial overhead.
