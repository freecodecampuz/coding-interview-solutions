# Maximum Sum Subarray of Size K

## Problem Statement
Given an array of positive numbers and a positive number 'k,' find the maximum sum of any contiguous subarray of size 'k'.

#### Example 1:
```
Input: arr = [2, 1, 5, 1, 3, 2], k=3 
Output: 9
Explanation: Subarray with maximum sum is [5, 1, 3].
```

#### Example 2:
```
Input: arr = [2, 3, 4, 1, 5], k=2 
Output: 7
Explanation: Subarray with maximum sum is [3, 4].
```

#### Constraints:

- `1 <= k <= nums.length <= 10^5`
- `1 <= nums[i] <= 10^5`

Similar to: https://leetcode.com/problems/maximum-sum-of-distinct-subarrays-with-length-k/description/

## Solution

```javascript
var maximumSubarraySum = function(nums, k) {
    let sum = 0, left = 0, ans = 0;    

    for (let right = 0; right < nums.length; right++) {
        
        while(right-left > k - 1) {
            sum -= nums[left];
            left++;
        }
        
        sum += nums[right];        

        if (right-left === k - 1) {
            ans = Math.max(sum, ans);
        }
    }
    return ans;
};

console.assert(maximumSubarraySum([2, 1, 5, 1, 3, 2], 3)===9);
console.assert(maximumSubarraySum([2, 3, 4, 1, 5], 2)===7);
```

- Time complexisty O(n)
- Space complexity O(1)

### Second version
In case we need to meet the following conditions: 
- **All the elements of the subarray are distinct.**

```javascript

var maximumSubarraySum = function(nums, k) {
    let sum = 0, left = 0, ans = 0;
    let seen = new Set();

    for (let right = 0; right < nums.length; right++) {
        
        while(right-left > k - 1 || seen.has(nums[right])) {
            seen.delete(nums[left]);
            sum -= nums[left];
            left++;
        }

        sum += nums[right];
        seen.add(nums[right]);

        if (seen.size === k) {
            ans = Math.max(sum, ans);
        }
    }
    return ans;
};

```
- Time complexisty O(n)
- Space complexity O(k)
