## Decode ways

https://leetcode.com/problems/decode-ways/

## Solution:

```javascript
var numDecodings = function(s) {
    let memo = [];
    function decodeLength(s, i) {
        let result;
        if (memo[i] !== undefined) {
           return memo[i];
        } else if (i === 0) {
            result = s[i] !== '0' ? 1 : 0;
        } else {
            let firstGroup = 0;
            let secondGroup = 0;
            if (s[i] !== '0') {
                firstGroup = decodeLength(s, i - 1);
            }

            if (s[i - 1] !== '0' && parseInt(`${s[i - 1]}${s[i]}`) <= 26) {
                secondGroup = i - 2 < 0 ? 1 : decodeLength(s, i - 2);
            }
            result = firstGroup + secondGroup;
        }

        memo[i] = result;
        return result;
    }

    return decodeLength(s, s.length - 1);
};
```