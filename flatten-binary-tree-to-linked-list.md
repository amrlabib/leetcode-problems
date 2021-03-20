## Flatten Binary Tree to Linked List

https://leetcode.com/problems/flatten-binary-tree-to-linked-list/

## Solution:

```javascript
function dfs(node, result) {
    result.push(node);
    node.left && dfs(node.left, result);
    node.right && dfs(node.right, result);
}

var flatten = function(root) {
    const result = [];
    if (!root) {
        return;
    }

    dfs(root, result);
    for (let i = 0; i < result.length; i++) {
        result[i].left = null;
        if (i + 1 < result.length) {
            result[i].right = result[i + 1]
        } else {
            result[i].right = null;
        }
    }
};
```