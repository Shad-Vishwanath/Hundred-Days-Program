# Day 01: Binary Search Essentials

## Overview
Day 1 focused on mastering **Binary Search** and its core variants. The key takeaway is that binary search applies not just to sorted arrays, but to any search space that exhibits a monotonic property (where a condition holds `false` up to a boundary and `true` afterwards).

## Problems Covered

| # | Problem | Difficulty | Key Pattern / Insight |
|---|---|---|---|
| 704 | [Binary Search](./704_binary_search.md) | Easy | Classic `left <= right` boundary condition |
| 69 | [Sqrt(x)](./69_sqrt_x.md) | Easy | Searching over an implicit numerical range `[0, x]` |
| 35 | [Search Insert Position](./35_search_insert_position.md) | Easy | `left` point points to insertion index on termination |
| 278 | [First Bad Version](./278_first_bad_version.md) | Easy | Minimizing search space with boolean API condition |
| 34 | [First & Last Position in Sorted Array](./34_find_first_and_last.md) | Medium | Biased binary search for left and right boundaries |
| 374 | [Guess Number Higher or Lower](./374_guess_number.md) | Easy | Standard binary search with custom API returns |
| 744 | [Smallest Letter Greater Than Target](./744_smallest_letter.md) | Easy | Binary search with circular wrap-around fallback |
| 153 | [Find Minimum in Rotated Sorted Array](./153_find_min_rotated.md) | Medium | Comparing `mid` against `right` boundary |
