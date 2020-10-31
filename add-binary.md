## Add Binary

https://leetcode.com/problems/add-binary/

## Solution 1:

In this solution we user the normal addition of bit numbers and move carry to the next bit location

```javascript
/**
 * @param {string} a
 * @param {string} b
 * @return {string}
 */
function addSingleBit(b1, b2, carry) {
    if (b1 === '0' && b2 === '0') {
        if (carry === '1') {
            return { sum: '1' , carry: '0'};
        }
        return { sum: '0', carry: '0' };
    } else if (b1 === '1' && b2 === '1') {
        if (carry === '1') {
            return { sum: '1' , carry: '1'};
        }
        return { sum: '0', carry: '1' }; 
    } else if (b1 === '1' || b2 === '1') {
        if(carry === '1') {
            return { sum: '0', carry: '1'}
        }
        return { sum: '1', carry: '0' };
    } else {
        if(carry === '1') {
            return { sum: '1', carry: '0' };
        }
        return { sum: '0', carry: '0' };
    }
}

var addBinary = function(a, b) {
    const aLength = a.length;
    const bLength = b.length;
    const maxLength = Math.max(aLength, bLength);
    let sumCarry = '0';
    let sumResult = '';
    for (let i = 0; i < maxLength; i++) {
        const { sum, carry } = addSingleBit(a[aLength - i - 1], b[bLength - i - 1], sumCarry);
        sumCarry = carry;
        sumResult = sum + sumResult;
    }

    if(sumCarry === '1') {
        sumResult = sumCarry + sumResult;
    }
    return sumResult;
};
```