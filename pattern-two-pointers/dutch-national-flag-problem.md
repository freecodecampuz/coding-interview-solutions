# Dutch National Flag Problem (medium)

## Problem Statement
Given an array containing 0s, 1s and 2s, sort the array in-place. You should treat numbers of the array as objects, hence, we can’t count 0s, 1s, and 2s to recreate the array.

The flag of the Netherlands consists of three colors: red, white and blue; and since our input array also consists of three different numbers that is why it is called Dutch National Flag problem.

#### Example 1:
Input: `[1, 0, 2, 1, 0]`

Output: `[0 0 1 1 2]`

#### Example 2:
Input: `[2, 2, 0, 1, 2, 0]`

Output: `[0 0 1 2 2 2 ]`

#### Constraints:
- n == arr.length
- 1 <= n <= 300
- arr[i] is either 0, 1, or 2.

Same as: https://leetcode.com/problems/sort-colors/description/

## Solution

```javascript
function sort(nums) {
    let left=0, right=nums.length-1;
    let mid = 0
    // move 0s to left and 2s to right
    while (mid<=right) {
        if (nums[mid]===0) {
            [nums[left], nums[mid]] = [nums[mid], nums[left]];
            left++;
            mid++;
        } else if (nums[mid]===1) {
            mid++;
        } else if (nums[mid]===2) {
            [nums[right], nums[mid]] = [nums[mid], nums[right]];
            right--;
        }
    }
    
    return nums;
}
// sort([1, 0, 2, 1, 0]);
// sort([2, 2, 0, 1, 2, 0]);
// sort([2, 2, 0, 1, 2, 0, 2]);
// sort([0, 2, 0, 1, 2, 0, 2]);
```
