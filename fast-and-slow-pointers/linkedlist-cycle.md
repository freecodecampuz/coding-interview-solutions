# LinkedList Cycle (easy)

## Problem Statement
Given the head of a Singly LinkedList, write a function to determine if the LinkedList has a cycle in it or not.

### Constraints:

The number of the nodes in the list is in the range [0, 104].
- 10^5 <= Node.val <= 10^5

## Solution

```javascript
function hasCycle(head) { // O(n)
  if (!head) return false;

  let slow = head, fast = head.next;

  while(fast != null) {
    if (slow===fast) {
      return true;
    }
    slow = slow.next;
    fast = fast?.next?.next;
  }
  return false;
}
```

