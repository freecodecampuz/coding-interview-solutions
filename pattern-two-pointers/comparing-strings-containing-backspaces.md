# Comparing Strings containing Backspaces (medium)

### Problem Statement
Given two strings containing backspaces (identified by the character ‘#’), check if the two strings are equal.

Example 1:
```
Input: str1="xy#z", str2="xzz#"
Output: true
Explanation: After applying backspaces the strings become "xz" and "xz" respectively.
```
Example 2:
```
Input: str1="xy#z", str2="xyz#"
Output: false
Explanation: After applying backspaces the strings become "xz" and "xy" respectively.
```
Example 3:
```
Input: str1="xp#", str2="xyz##"
Output: true
Explanation: After applying backspaces the strings become "x" and "x" respectively.
```


```javascript
var backspaceCompare = function(s, t) { // Time Complexity: O(n+m), Space Complexity: O(1).
    const itrOfs = trimBackspaces(s); // O(n)
    const itrOft = trimBackspaces(t); // O(m)

    let nextOfs = itrOfs.next();
    let nextOft = itrOft.next();

    while(!nextOfs.done && !nextOft.done) {
        if (nextOfs.value === nextOft.value) {
            nextOfs = itrOfs.next();
            nextOft = itrOft.next();
        } else {
            return false;
        }
    }
    return nextOfs.done===nextOft.done;
};

function* trimBackspaces(str) {
    let backspaces = 0;
    for(let i=str.length-1; i>=0;i--) {
        if (str[i]==='#') {
            backspaces++;
        } else if (backspaces>0) {
            backspaces--;
        } else {
            yield str[i]; 
        }
    }
}
```
