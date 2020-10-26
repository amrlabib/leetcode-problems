## Add Two Numbers

https://leetcode.com/problems/add-two-numbers/

## Solution O(n):

In this solution we should keep in mind that the linked list number can contain up to 100 numbers, this exceed the max number in javascript Number, so we will need to make the addition on each digit and handle the carry to the next digit.

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
    this.val = (val===undefined ? 0 : val)
    this.next = (next===undefined ? null : next)
}


var addTwoNumbers = function(l1, l2) {
    let firstList = l1;
    let secondList = l2;

    let resultFirstNode = undefined;
    let resultCurrentNode = undefined;
    let resultCarry = 0;
    while(true) {
        if(!firstList && !secondList) {
            break;
        }

        const sumResult = ((firstList && firstList.val) || 0) + ((secondList && secondList.val) || 0) + resultCarry;
        const { num, carry } = sumResult >= 10 ? { num: sumResult - 10, carry: 1 } : { num: sumResult, carry: 0 };
        const node = new ListNode(num);
        if(resultFirstNode === undefined) {
            resultFirstNode = node;
        } else {
            resultCurrentNode.next = node;
        }
        resultCurrentNode = node;
        resultCarry = carry;

        firstList = firstList && firstList.next;
        secondList = secondList && secondList.next;
    }

    if(resultCarry) {
        resultCurrentNode.next = new ListNode(resultCarry);
    }

    return resultFirstNode;
};
```