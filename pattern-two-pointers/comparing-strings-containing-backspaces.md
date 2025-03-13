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
