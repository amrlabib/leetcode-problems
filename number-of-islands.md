## Number of Islands

https://leetcode.com/problems/number-of-islands/

## Solution:

This problem can be solved using BFS or DFS in graph where we mark each visited node as visited and we increment the number of island once the BFS for a specific "1" is ended, in this code we use BFS

```javascript
var numIslands = function(grid) {
    const visitedNodes = {};
    let numberOfIslands = 0;
    for (let i = 0; i < grid.length; i++) {
        for (let j = 0; j < grid[0].length; j++) {
            if (grid[i][j] === '1' && !visitedNodes[`${i}-${j}`]) {
                const queue = new Queue();
                queue.enqueue({ i, j });
                while (!queue.isEmpty()) {
                    const currentNode = queue.dequeue();
                    if (currentNode.i < 0 || currentNode.i >= grid.length || currentNode.j < 0 || currentNode.j > grid[0].length || visitedNodes[`${currentNode.i}-${currentNode.j}`]) {
                        continue;
                    } else if (grid[currentNode.i][currentNode.j] === '1') {
                        visitedNodes[`${currentNode.i}-${currentNode.j}`] = true;
                        queue.enqueue({i: currentNode.i + 1, j: currentNode.j });
                        queue.enqueue({i: currentNode.i - 1, j: currentNode.j });
                        queue.enqueue({i: currentNode.i, j: currentNode.j + 1 });
                        queue.enqueue({i: currentNode.i, j: currentNode.j - 1 });
                    }
                }
                numberOfIslands++;
            }
        }
    }
    return numberOfIslands;
};
```