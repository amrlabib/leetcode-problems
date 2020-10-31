## Add Binary

https://leetcode.com/problems/add-binary/

## Solution 1:

In this solution we use the normal addition of bit numbers and move carry to the next bit location

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


## Solution 2:

In this solution we will use bit manipulation to be able to add both binary numbers.

1. Apply bitwise XOR `^` on a and b `a ^ b` this will return the sum result without considering carry
2. Apply bitwise AND `&` on a and b and then shift the result by 1 to the left `(a & b) << 1`
3. check if the result of step 2 is not 0 then add result from 1 and 2
4. repeat step 3 until result from step 2 is 0, now the final result will be the result from step 1 in last iteration

```javascript

var addBinary = function(a, b) {
    let firstNumber = BigInt('0b' + a);
    let secondNumber = BigInt('0b' + b);
    while(secondNumber) {
        const xOrResult = firstNumber ^ secondNumber;
        const carryResult = (firstNumber & secondNumber) << 1n;
        
        firstNumber = xOrResult;
        secondNumber = carryResult;
    }
    return firstNumber.toString(2);
};

```