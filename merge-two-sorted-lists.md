## Merge Two Sorted Lists

## Solution: 

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */

function ListNode(val, next) {
    this.val = (val===undefined ? 0 : val);
    this.next = (next===undefined ? null : next);
}

var mergeTwoLists = function(l1, l2) {
    if(!l1 && !l2) {
        return null;
    }
    let l1Pointer = l1;
    let l2Pointer = l2;
    let resultPointer = new ListNode();
    let currentPointer = resultPointer;
    while (true) {
        if (l1Pointer && (l1Pointer.val <= (l2Pointer && l2Pointer.val))) {
            currentPointer.val = l1Pointer.val;
            l1Pointer = l1Pointer.next;
        } else if (l2Pointer && (l2Pointer.val < (l1Pointer && l1Pointer.val))) {
            currentPointer.val = l2Pointer.val;
            l2Pointer = l2Pointer.next;
        } else if (l1Pointer) {
            currentPointer.val = l1Pointer.val;
            l1Pointer = l1Pointer.next;
        } else if (l2Pointer) {
            currentPointer.val = l2Pointer.val;
            l2Pointer = l2Pointer.next;
        }
        if ((l1Pointer === undefined || l1Pointer === null) &&
            (l2Pointer === undefined || l2Pointer === null)) {
            break;
        }

        const nextNode = new ListNode();
        currentPointer.next = nextNode;
        currentPointer = nextNode;
    }

    return resultPointer;
};
```