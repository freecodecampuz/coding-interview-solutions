# Middle of the LinkedList (easy)

## Problem Statement
Given the head of a Singly LinkedList, write a method to return the middle node of the LinkedList.

If the total number of nodes in the LinkedList is even, return the second middle node.

Example 1:
```
Input: 1 -> 2 -> 3 -> 4 -> 5 -> null
Output: 3
```
Example 2:
```
Input: 1 -> 2 -> 3 -> 4 -> 5 -> 6 -> null
Output: 4
```
Example 3:
```
Input: 1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7 -> null
Output: 4
```
### Constraints:
The number of nodes in the list is in the range `[1, 100]`.
- `1 <= Node.val <= 100`

Same as: https://leetcode.com/problems/middle-of-the-linked-list/

## Solution

```javascript
function middleNode(head) { // O(n)
    // [1, 2, 3, 4, 5] => i,j where j is twice faster than i
    //  ij
    //     i  j
    //        i     j
    let slow=head, fast=head;

    while (fast && fast.next) {
        slow=slow.next;
        fast = fast.next.next;
    }
    return slow;
};
```
