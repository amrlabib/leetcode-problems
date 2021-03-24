## Binary Tree Paths

https://leetcode.com/problems/binary-tree-paths/

### Solution:

```javascript
var binaryTreePaths = function(root) {
    const result = [];

    if (root.val === undefined) {
        return result;
    }

    function dfs(node, currentPath) {
        const path = currentPath ? `${currentPath}->${node.val}` : `${node.val}`;
        node.left && dfs(node.left, path);
        node.right && dfs(node.right, path);

        if(node.left === null && node.right === null) {
            result.push(path);
        }
    }

    dfs(root, '');

    return result;
};
```