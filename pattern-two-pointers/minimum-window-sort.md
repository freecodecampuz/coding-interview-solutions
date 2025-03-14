# Minimum Window Sort (medium)

## Problem Statement
Given an array, find the length of the smallest subarray in it which when sorted will sort the whole array.

#### Example 1:
```
Input: [1, 2, 5, 3, 7, 10, 9, 12]
Output: 5
Explanation: We need to sort only the subarray [5, 3, 7, 10, 9] to make the whole array sorted
```
#### Example 2:
```
Input: [1, 3, 2, 0, -1, 7, 10]
Output: 5
Explanation: We need to sort only the subarray [1, 3, 2, 0, -1] to make the whole array sorted
```
#### Example 3:
```
Input: [1, 2, 3]
Output: 0
Explanation: The array is already sorted
```
####  Example 4:
```
Input: [3, 2, 1]
Output: 3
```

#### Constraints:

- `1 <= nums.length <= 10^4`
- `-10^5 <= nums[i] <= 10^5`

Same as https://leetcode.com/problems/shortest-unsorted-continuous-subarray/

## Solution 

```javascript
var findUnsortedSubarray = function(nums) {
    // let's find the end by comparing max to the current element
    let end = -1, max=nums[0];
    for(let i=1; i<nums.length; i++) {
        if (max <= nums[i]) {
            max = nums[i];
        } else {
            end = i;
        }
    }
    // let's find the start by comparing min to the current element
    let start = -1, min = nums[nums.length-1];
    for(let i=nums.length-2; i>=0; i--) {
        if (min >= nums[i]) {
            min = nums[i];
        } else {
            start = i;
        }
    }

    return end-start === 0 ? 0 : end-start+1;
};

console.assert(findUnsortedSubarray([2,6,4,8,10,9,15])===5);
console.assert(findUnsortedSubarray([1,2,3,4])===0);
console.assert(findUnsortedSubarray([1])===0);
console.assert(findUnsortedSubarray([1, 2, 5, 3, 7, 10, 9, 12])===5);
console.assert(findUnsortedSubarray([1, 3, 2, 0, -1, 7, 10])===5);
console.assert(findUnsortedSubarray([3, 2, 1])===3);
console.assert(findUnsortedSubarray([1,2,3,3,3])===0);
```
