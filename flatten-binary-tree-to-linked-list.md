## Flatten Binary Tree to Linked List

https://leetcode.com/problems/flatten-binary-tree-to-linked-list/

## Solution 1:

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


## Solution 2:

```javascript
function dfs(node, leftMost) {
    if (node.left && node.left.left === null && node.left.right === null) { // left leaf node
        let temp = node.right;
        node.right = node.left;
        node.right.right = temp;
        node.left = null;
    }

    if (node.left === null && node.right === null) { // final right leaf
        return node;
    }

    const leftLeaf = (node.left && dfs(node.left));
    const rightLeaf = (node.right && dfs(node.right));

    if (leftLeaf && node.left) {
        let temp = node.right;
        node.right = node.left;
        leftLeaf.right = temp;
        node.left = null;
    }

    return rightLeaf || leftLeaf;
}

var flatten = function(root) {
    if (!root) {
        return;
    }
    dfs(root);
};
```