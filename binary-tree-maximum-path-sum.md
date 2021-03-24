## Binary Tree Maximum Path Sum

https://leetcode.com/problems/binary-tree-maximum-path-sum/


### Solution:

```javascript

var maxPathSum = function(root) {
    let max = -1000;
    if (root.val === undefined) {
       return 0;
    }

    function dfs(node) {
        const leftVal = (node.left && dfs(node.left)) || 0;
        const rightVal = (node.right && dfs(node.right)) || 0;

        const leftSum = leftVal + node.val;
        const rightSum = rightVal + node.val
        const sum = leftVal + node.val + rightVal;

        max = Math.max(leftSum, node.val, rightSum, sum,  max);

        return Math.max(leftSum, node.val, rightSum);
    }

    dfs(root);
    return max;
};
```