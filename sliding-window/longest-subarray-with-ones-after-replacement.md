# Longest Subarray with Ones after Replacement

## Problem Statement
Given an array containing 0s and 1s, if you are allowed to replace no more than ‘k’ 0s with 1s, find the length of the longest contiguous subarray having all 1s.

### Example 1:
```
Input: Array=[0, 1, 1, 0, 0, 0, 1, 1, 0, 1, 1], k=2  
Output: 6  
Explanation: Replace the '0' at index 5 and 8 to have the longest contiguous subarray of 1s having length 6.
```

### Example 2:
```
Input: Array=[0, 1, 0, 0, 1, 1, 0, 1, 1, 0, 0, 1, 1], k=3  
Output: 9
```

### Constraints:

- `1 <= nums.length <= 10^5`
- `nums[i] is either 0 or 1.`
- `0 <= k <= nums.length`

The same as: https://leetcode.com/problems/max-consecutive-ones-iii/description/

## Solution

``` javascript
var longestOnes = function(nums, k) {
    let left = 0, right = 0, max = 0, replacements = 0;


    while(right < nums.length) {

        if (nums[right]===0) {
            replacements++;
        }

        while(replacements > k && left < nums.length) {
            if (nums[left]===0) {
                replacements--;
            }
            left++;
        }

        max = Math.max(right - left + 1, max);
        right++;
    }
    return max;
};
```

- Time complexity: O(n)
- Space complexity: O(1)

