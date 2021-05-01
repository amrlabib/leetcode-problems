## LRU Cache

https://leetcode.com/problems/lru-cache/


## Solution:

Solution is based on an ordered hash table we can implement the order inside hash table by using doubly linked list where each key in the hash table is pointing to the next saved key and the previous saved key


```javascript
var LRUCache = function(capacity) {
    this.maxCapacity = capacity;
    this.capacity = 0;
    this.cache = {};
    this.firstKeyPointer;
    this.lastKeyPointer;
};

LRUCache.prototype.remove = function(key) {
    const nextKey = this.cache[key].nextKeyPointer;
    const prevKey = this.cache[key].prevKeyPointer;

    nextKey && (this.cache[nextKey].prevKeyPointer = prevKey);
    prevKey && (this.cache[prevKey].nextKeyPointer = nextKey);

    if (key === this.firstKeyPointer) {
       this.firstKeyPointer = nextKey;
    }

    if (key === this.lastKeyPointer) {
        this.lastKeyPointer = prevKey;
    }

    delete this.cache[key];
    this.capacity--;
}

LRUCache.prototype.add = function(key, value) {
    this.cache[key] = {
        value,
        nextKeyPointer: null,
        prevKeyPointer: null,
    };

    if (this.capacity === 0) {
        this.firstKeyPointer = key;
        this.lastKeyPointer = key;
    } else {
        this.lastKeyPointer && (this.cache[this.lastKeyPointer].nextKeyPointer = key);
        this.cache[key].prevKeyPointer = this.lastKeyPointer;
        this.lastKeyPointer = key;
    }

    this.capacity++;
}

LRUCache.prototype.get = function(key) {
    if (this.cache[key] !== undefined) {
        const value = this.cache[key].value;
        this.remove(key);
        this.add(key, value);
        return value;
    }
    return -1;
};

LRUCache.prototype.put = function(key, value) {
    if (this.cache[key] !== undefined) {
        this.remove(key);
        this.add(key, value);
    } else if (this.capacity < this.maxCapacity) {
        this.add(key, value);
    } else {
        this.remove(this.firstKeyPointer);
        this.add(key, value);
    }
};

```