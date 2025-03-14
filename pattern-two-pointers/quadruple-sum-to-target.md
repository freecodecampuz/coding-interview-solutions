# Quadruple Sum to Target (medium)

## Problem Statement
Given an array of unsorted numbers and a target number, find all unique quadruplets in it, whose sum is equal to the target number. Such that:

- `0 <= a, b, c, d < n`
- `a, b, c, and d are distinct.`
- `nums[a] + nums[b] + nums[c] + nums[d] == target`

Example 1:
```
Input: [4, 1, 2, -1, 1, -3], target=1
Output: [-3, -1, 1, 4], [-3, 1, 1, 2]
Explanation: Both the quadruplets add up to the target.
```
Example 2:
```
Input: [2, 0, -1, 1, -2, 2], target=2
Output: [-2, 0, 2, 2], [-1, 0, 1, 2]
Explanation: Both the quadruplets add up to the target.
```

### Constraints:
- 1 <= nums.length <= 200
- -109 <= nums[i] <= 109
- -109 <= target <= 109

Same as: https://leetcode.com/problems/4sum/description/

## Solution

```javascript
function searchQuadruplets(arr, target) { //O(n^3)
    nums.sort((a, b)=> a - b); // O(nlogn)
    
    const n = nums.length;
    const res = [];
    
    for(let i=0; i < n-3; i++) { // O(n)

        for(let j=i+1; j < n-2; j++) { // O(n)

            let left=j+1, right=n-1;

            while(left < right) { // O(n)

                let sum = nums[i]+nums[j]+nums[left]+nums[right];

                if (sum === target) {
                    res.push([nums[i],nums[j],nums[left],nums[right]]);
                    // res.push([i,j,left,right]);
                    left++;
                    while(left < right && nums[left]===nums[left-1]) { // skip all the same numbers
                        left++;
                    }
                    right--;
                    while(left < right && nums[right]===nums[right+1]) { // skip all the same numbers
                        right--;
                    }
                } else if (sum > target) {
                    right--;
                } else {
                    left++;
                }
            }
            while(j < n-1 && nums[j]===nums[j+1]) { // skip all the same numbers
                j++;
            }
        }
        while(i < n-1 && nums[i]===nums[i+1]) { // skip all the same numbers
            i++;
        }
    }

    return res;
}
```
