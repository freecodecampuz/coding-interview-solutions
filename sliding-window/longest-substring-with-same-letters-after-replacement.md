# Longest Repeating Character Replacement

## Problem Statement

You are given a string s and an integer k. You can choose any character of the string and change it to any other uppercase English character. You can perform this operation at most k times.

Return the length of the longest substring containing the same letter you can get after performing the above operations.

 

### Example 1:
```
Input: s = "ABAB", k = 2
Output: 4
Explanation: Replace the two 'A's with two 'B's or vice versa.
```
### Example 2:
```
Input: s = "AABABBA", k = 1
Output: 4
Explanation: Replace the one 'A' in the middle with 'B' and form "AABBBBA".
The substring "BBBB" has the longest repeating letters, which is 4.
There may exist other ways to achieve this answer too.
 ```

### Constraints:

- `1 <= s.length <= 10^5`
- `s` consists of only uppercase English letters.
- `0 <= k <= s.length`

## Solution

```javascript
var characterReplacement = function(s, k) {
  const frequency = new Map();
  let left = 0, right = 0, max = 0, currentLength = 0, maxFrequency = 0;

  while(right < s.length) {
    frequency.set(s[right], (frequency.get(s[right]) || 0) + 1);
    maxFrequency = Math.max(...Array.from(frequency.values()));
    currentLength = right - left + 1
    if (currentLength - maxFrequency > k) {
      frequency.set(s[left], frequency.get(s[left]) - 1);
      left++;
    }
    right++;
  }
}
```

