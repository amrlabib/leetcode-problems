## Shortest Distance from All Buildings

https://leetcode.com/problems/shortest-distance-from-all-buildings/

## Solution:

Solution is based on BFS in graph where we check all adjacent nodes first and then we check deeper nodes to get the shortest path between empty land and a building

```javascript
function getNumberOfHouses(grid) {
    let houses = 0;
    for (let i = 0; i < grid.length; i++) {
        for (let j = 0; j < grid[0].length; j++) {
            if (grid[i][j] === 1) {
                houses++;
            }
        }
    }
    return houses;
}


function getShortestSumForLand(grid, row, col) {
    let queue = [{ i: row, j: col, step: 0 }];
    let visited = {};
    let minDistanceToBuildings = {};
    while(queue.length > 0) {
        const current = queue.shift();
        if(current.i < 0 || current.i >= grid.length || current.j < 0 || current.j >= grid[0].length || visited[`${current.i}-${current.j}`]) {
            continue;
        } else if (grid[current.i][current.j] === 1) {
            const currentMin = minDistanceToBuildings[`${current.i}-${current.j}`];
            if (!currentMin || current.step < currentMin) {
                minDistanceToBuildings[`${current.i}-${current.j}`] = current.step;
            }
            continue;
        } else if (grid[current.i][current.j] === 2) {
            continue;
        }
        visited[`${current.i}-${current.j}`] = true;

        queue.push({ i: current.i - 1, j: current.j, step: current.step + 1})
        queue.push({ i: current.i + 1, j: current.j, step: current.step + 1})
        queue.push({ i: current.i, j: current.j - 1, step: current.step + 1})
        queue.push({ i: current.i, j: current.j + 1, step: current.step + 1})
    }

    const distancesArray = Object.entries(minDistanceToBuildings);
    const distance = distancesArray.reduce((sum, [ key, value ]) => (sum + value), 0);
    return { distance, numberOfHouses: distancesArray.length };
}

var shortestDistance = function(grid) {
    let minDistance;
    const totalNumberOfHouses = getNumberOfHouses(grid);
    for (let i = 0; i < grid.length; i++) {
        for (let j = 0; j < grid[0].length; j++) {
            if (grid[i][j] === 0) {
                const { distance, numberOfHouses } = getShortestSumForLand(grid, i, j);
                if ((!minDistance || minDistance > distance) && numberOfHouses === totalNumberOfHouses) {
                    minDistance = distance;
                }
            }
        }
    }
    return minDistance || -1;
};
```