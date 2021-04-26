## Robot Bounded In Circle

https://leetcode.com/problems/robot-bounded-in-circle/

## Solution:

Solution is based on the fact that a circular path will always return to point (0,0) if the path is executed 4 times

```javascript
var isRobotBounded = function(instructions) {
    let x = 0;
    let y = 0;
    let xDir = 0;
    let yDir = 1;
    let count = 0;
    while (count < 4) {
        count++;
        for (let i = 0; i < instructions.length; i++) {
            if (instructions[i] === 'G') {
                if (xDir) {
                    x += xDir;
                } else if (yDir) {
                    y += yDir;
                }
            } else if (instructions[i] === 'L' && xDir !== 0) {
                yDir = xDir > 0 ? 1 : -1;
                xDir = 0;
            } else if (instructions[i] === 'L' && yDir !== 0) {
                xDir = yDir > 0 ? -1 : 1;
                yDir = 0;
            } else if (instructions[i] === 'R' && xDir !== 0) {
                yDir = xDir > 0 ? -1 : 1;
                xDir = 0;
            } else if (instructions[i] === 'R' && yDir !== 0) {
                xDir = yDir > 0 ? 1 : -1;
                yDir = 0;
            }
        }
    }


    if (x === 0 && y === 0) {
        return true;
    }

    return false;
};
```