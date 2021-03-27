## Binary Tree Vertical Order Traversal

https://leetcode.com/problems/binary-tree-vertical-order-traversal/

## Solution:

Solution is based on bfs where we check current node and then the next two children and then we go deeper while doing that we need to keep track of the column value everytime we go to left child we decrement 1 and everytime we move to right child we increment one.

Here we know that max col count will 100 so we push arrays in result array with 100 - col this way we preserve order and we are sure we will not be adding items in negative index in array.

```javascript
function bfs(node) {
    const maxColVal = 100;
    const result = [];
    const queue = [{ node, col: 0 }];
    let current;
    while (queue.length > 0) {
        current = queue.shift();
        if (result[maxColVal + current.col]) {
            result[maxColVal + current.col].push(current.node.val);
        } else  {
            result[maxColVal + current.col] = [current.node.val];
        }
        current.node.left && queue.push({ node: current.node.left, col: current.col - 1 });
        current.node.right && queue.push({ node: current.node.right, col: current.col + 1 });
    }
    return result;
}

var verticalOrder = function(root) {
    if (root === undefined || root === null || root.val === undefined) {
        return [];
    }

    return bfs(root).filter(arr => arr);
};
```