# Minimum Size Subarray Sum

## Problem Statement
Given an array of positive integers nums and a positive integer target, return the minimal length of a subarray whose sum is greater than or equal to target. If there is no such subarray, return 0 instead.

Example 1:
```
Input: target = 7, nums = [2,3,1,2,4,3]
Output: 2
Explanation: The subarray [4,3] has the minimal length under the problem constraint.
```

Example 2:
```
Input: target = 4, nums = [1,4,4]
Output: 1
```
Example 3:
```
Input: target = 11, nums = [1,1,1,1,1,1,1,1]
Output: 0
```

Constraints:
```
1 <= target <= 109
1 <= nums.length <= 105
1 <= nums[i] <= 104
```

Same as: https://leetcode.com/problems/minimum-size-subarray-sum/

## Solution 

```javascript
var minSubArrayLen = function(target, nums) {
    let anws = Number.MAX_SAFE_INTEGER;
    let i = 0, sum=0;

    for(let j=0; j<nums.length; j++) {
        sum+=nums[j];
        if (sum >= target) {            
            while(sum >= target) {
                anws = Math.min(anws, j-i+1);
                if (anws===1) {
                    return 1;
                }
                sum -= nums[i];
                i++;
            }
        }
    }
    return anws===Number.MAX_SAFE_INTEGER ? 0 : anws;
};
```

- Time complexity: O(n)
- Space compexisty: O(1)
