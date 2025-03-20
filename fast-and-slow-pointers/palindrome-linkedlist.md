# Palindrome LinkedList (medium)

## Problem Statement
Given the head of a Singly LinkedList, write a method to check if the LinkedList is a palindrome or not.
Your algorithm should use constant space and the input LinkedList should be in the original form once the algorithm is finished. The algorithm should have O(N) time complexity where ‘N’ is the number of nodes in the LinkedList.

#### Example 1:
```
Input: 2 -> 4 -> 6 -> 4 -> 2 -> null
Output: true
```
#### Example 2:
```
Input: 2 -> 4 -> 6 -> 4 -> 2 -> 2 -> null
Output: false
```

#### Example 3:
```
Input: 1->2->2->1
Output: true
```

####  Constraints:
- The number of nodes in the list is in the range `[1, 10^5]`.
- `0 <= Node.val <= 9`

Same as: https://leetcode.com/problems/palindrome-linked-list/

## Solution

```javascript
var isPalindrome = function(head) { // O(n) time and O(1) space
    // find mid
    let slow = head, fast = head;
    while(fast) {
        slow = slow.next;
        fast = fast?.next?.next;
    }
    let mid = slow;
    // reverse second haft from mid
    let prev = null, curr = mid;
    while (curr) {
        let next = curr.next;
        curr.next = prev;
        prev = curr;
        curr = next;
    }
    let left = head, right = prev;
    while(left && right) {
        if (left.val !== right.val) {
            return false;
        }
        left = left.next;
        right = right.next;
    }
    return true;
};
```
