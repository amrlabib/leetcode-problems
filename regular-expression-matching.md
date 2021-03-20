## Regular Expression Matching

https://leetcode.com/problems/regular-expression-matching/

## Solution:

Cleaner code

```javascript
var isMatch = function(s, p) {
    function match(i, j) {
        if (i >= s.length && j >= p.length) {
            return true;
        }

        const isMatch = i < s.length && (s[i] === p[j] || p[j] === '.');
        if (p[j + 1] === '*') {
            return ((isMatch && match(i + 1, j)) || match(i, j + 2));
        } else if (isMatch) {
            return match(i+1, j+1);
        }

        return false;
    }
    return match(0, 0);
};
```


## Solution:

My Code

```javascript
var isMatch = function(s, p) {
 if (s.length === 0 && p.length === 0) {
       return true;
    }

    if (s[0] !== p[0] && p[0] !== '.') {
        if (p[1] === '*') {
            return isMatch(s, p.slice(2));
        }
        return false;
    } else if (p[1] === '*') {
        if (s.length == 0) {
            return isMatch(s, p.slice(2));
        }
        return (isMatch(s.slice(1), p) || isMatch(s, p.slice(2)));
    } else if (s[0] === undefined && p[0] === '.') {
        return false;
    } else {
        return isMatch(s.slice(1), p.slice(1));
    }
}
```