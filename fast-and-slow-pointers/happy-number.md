# Happy Number (medium)

## Problem Statement
Any number will be called a happy number if, after repeatedly replacing it with a number equal to the sum of the square of all of its digits, leads us to the number 1. All other (not-happy) numbers will never reach 1. Instead, they will be stuck in a cycle of numbers that does not include 1.

Given a positive number n, return true if it is a happy number otherwise return false.

#### Example 1:
```
Input: 23
Output: true (23 is a happy number)
Explanations: Here are the steps to find out that 23 is a happy number:

2^2 + 3^2 = 4 + 9 = 13
1^2 + 3^2 = 10
1^2 + 0^2 = 1
```

#### Example 2:
```
Input: n = 19
Output: true
Explanation:
12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1
```

#### Example 3:
```
Input: n = 2
Output: false
```

### Constraints:
- `1 <= n <= 2^31 - 1`

## Solution

```javascript
var isHappy = function(n) {
    let slow = n, fast = n;

    do {
        slow = calculateSquare(slow);
        fast = calculateSquare(calculateSquare(fast));
    } while(slow != fast);

    return slow === 1;
};

function calculateSquare(num) {
    let sum = 0;
    while (num>0) {
        let rem = num % 10;
        sum += rem**2;
        num = Math.trunc(num/10);
    }
    return sum;
}
```
