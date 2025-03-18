# Start of LinkedList Cycle (medium)

## Problem Statement
Given the head of a Singly LinkedList that contains a cycle, write a function to find the starting node of the cycle.

Example 1:
```
Input: head = [3,2,0,-4], pos = 1
Output: 2 as tail connects to node index 1
Explanation: There is a cycle in the linked list, where tail connects to the second node.
```
Example 2:
```
Input: head = [1,2], pos = 0
Output: 1 as tail connects to node index 0
Explanation: There is a cycle in the linked list, where tail connects to the first node.
```
Example 3:
```
Input: head = [1], pos = -1
Output: no cycle
Explanation: There is no cycle in the linked list.
```

### Constraints:

The number of the nodes in the list is in the range `[0, 104].`
- -10^5 <= Node.val <= 10^5

Same as: https://leetcode.com/problems/linked-list-cycle-ii/

## Solution

```javascript
var detectCycle = function(head) { // Time: O(n), Space: O(1)
    if (!head) return null;
    let slow = head, fast = head;

    while (fast && fast.next) {        
        slow = slow.next;
        fast = fast.next.next;
        if (slow === fast) {
            break;
        }
    }

    if (!fast || !fast.next) {
        return null;
    }

    fast = head;
    while(slow != fast) {
        slow=slow.next;
        fast=fast.next;
    }

    return slow;
};
```
