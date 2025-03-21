# Rearrange a LinkedList (medium)

## Problem Statement
Given the head of a Singly LinkedList, write a method to modify the LinkedList such that the nodes from the second half of the LinkedList are inserted alternately to the nodes from the first half in reverse order. 
So if the LinkedList has nodes `1 -> 2 -> 3 -> 4 -> 5 -> 6 -> null`, your method should return `1 -> 6 -> 2 -> 5 -> 3 -> 4 -> null`.

Your algorithm should use only constant space the input LinkedList should be modified in-place.

#### Example 1:
```
Input: head = 1->2->3->4
Output: 1->4->2->3
```

#### Example 2:
```
Input: 2 -> 4 -> 6 -> 8 -> 10 -> 12 -> null
Output: 2 -> 12 -> 4 -> 10 -> 6 -> 8 -> null
```

#### Constraints:
- The number of nodes in the list is in the range `[1, 5 * 10^4]`.
- `1 <= Node.val <= 1000`

Same as: https://leetcode.com/problems/reorder-list/description/

## Solution

```javascript
var reorderList = function(head) { // O(n) time and O(1) space
    // find middle node in the linked list
    let slow=head, fast=head, prev = null;
    while (fast) {
        prev = slow; // keeps track of node before middle node
        slow = slow.next;
        fast = fast?.next?.next;
    }
    prev.next = null; // to disconnect middle node from first haft
    // slow ends up in the middle
    // now we need to revers second haft
    prev = null;
    let curr = slow, next = null;
    while(curr) {
        next = curr.next;
        curr.next = prev;
        prev = curr;
        curr = next;
    }
    // prev is head of second haft
    curr = head;
    next = prev;
    while (next) {
        let currNext = curr.next, nextOfNext = next.next;
        curr.next = next;
        next.next = currNext;
        next = nextOfNext;
        curr = currNext;
    }
    return head;
};
```
