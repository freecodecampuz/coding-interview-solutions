# Longest Substring with K Distinct Characters

## Problem Statement
Given a string, find the length of the longest substring in it with no more than K distinct characters.

You can assume that K is less than or equal to the length of the given string.

### Example 1:
```
Input: str="araaci", K=2  
Output: 4  
Explanation: The longest substring with no more than '2' distinct characters is "araa".
```
### Example 2:
```
Input: str="araaci", K=1  
Output: 2  
Explanation: The longest substring with no more than '1' distinct characters is "aa".
```
### Example 3:
```
Input: str="cbbebi", K=3  
Output: 5
```

### Constraints:
- `1 <= s.length <= 10^4`
- `str` consists of only lowercase English letters.
- `1 <= k <= 10^5`

## Solution

```javascript
var longestSubStrDistinct = function(str, k) {
    let left=0, right=0, seen = new Map(), max = 0;

    while(right < str.length) {
        seen.set(str[right], (seen.get(str[right]) ?? 0) + 1);

        while(seen.size > k) {
            seen.set(str[left], (seen.get(str[left]) ?? 0) - 1);
            if (seen.get(str[left]) <= 0) {
                seen.delete(str[left])
            }
            left++;
        }
        
        if (seen.size <=k) {
            max = Math.max(max, right-left+1);
        }

        right++;
    }
    return max;
};

console.assert(longestSubStrDistinct('araaci', 2)===4);
console.assert(longestSubStrDistinct('araaci', 1)===2);
console.assert(longestSubStrDistinct('cbbebi', 3)===5);
```

- Time complexity: O(n)
- Space complexity: O(n)
