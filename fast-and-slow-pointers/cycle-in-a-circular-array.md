# Cycle in a Circular Array (medium)

## Problem Statement
We are given an array containing positive and negative numbers. Suppose the array contains a number ‘M’ at a particular index. Now, if ‘M’ is positive we will move forward ‘M’ indices and if ‘M’ is negative move backwards ‘M’ indices. You should assume that the array is circular which means two things:

- If, while moving forward, we reach the end of the array, we will jump to the first element to continue the movement.
- If, while moving backward, we reach the beginning of the array, we will jump to the last element to continue the movement.

Return true if there is a cycle in nums, or false otherwise.
#### Example 1:
```
Input: nums = [2,-1,1,2,2]
Output: true
Explanation: The graph shows how the indices are connected. White nodes are jumping forward,
while red is jumping backward.
We can see the cycle 0 --> 2 --> 3 --> 0 --> ...,
and all of its nodes are white (jumping in the same direction).
```

#### Example 2:
```
Input: nums = [-1,-2,-3,-4,-5,6]
Output: false
Explanation: The graph shows how the indices are connected.
White nodes are jumping forward, while red is jumping backward.
The only cycle is of size 1, so we return false.
```

#### Example 3:
```
Input: nums = [1,-1,5,1,4]
Output: true
Explanation: The graph shows how the indices are connected. White nodes are jumping forward,
while red is jumping backward.
We can see the cycle 0 --> 1 --> 0 --> ..., and while it is of size > 1,
it has a node jumping forward and a node jumping backward, so it is not a cycle.
We can see the cycle 3 --> 4 --> 3 --> ...,
and all of its nodes are white (jumping in the same direction).
```

#### Constraints:
- `1 <= nums.length <= 5000`
- `-1000 <= nums[i] <= 1000`
- `nums[i] != 0`

Same as: https://leetcode.com/problems/circular-array-loop/description/

## Solution
```javascript
var circularArrayLoop = function(nums) {    
    let slow = 0, fast = 0;
    const length = nums.length;
    const nextFn = (i) => ((i + nums[i] % length) + length) % length;

    for(let i = 0; i < length; i++ ) {
        slow = i;
        fast = nextFn(i);

        while(nums[slow]*nums[fast] > 0 &&
        nums[slow] * nums[nextFn(fast)] > 0) {
            if (slow === fast) {
                if (slow != nextFn(slow)) {
                    return true;
                }
                break;
            }
            slow = nextFn(slow);
            fast = nextFn(nextFn(fast));
        }
    }
    return false;
};
```
