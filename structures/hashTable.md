# Hash Table

Hash Table is a data structure that stores key-value pairs and allows for fast data access using a hash function. The hash function takes a key as input and returns an index where the corresponding value is stored in an array.

## Characteristics

- **Fast Data Access:** lookup, insertion and deletion operations have an average time complexity of O(1).
- **Hashing:** a hash function maps keys to array indices.
- **Collision Handling:** when two keys hash to the same index, collision resolution techniques are used: chaining (each array index stores a linked list of items) or open addressing (the next available index is used).

## Use Cases

- **Fast Lookup and Data Access:** used in databases, caching systems and compilers for quick record retrieval by key.
- **Cache Implementation (LRU, LFU):** combined with a doubly linked list it enables fast lookup and updates of frequently used data.
- **Duplicate Detection and Frequency Counting:** applied in algorithms for detecting duplicates, text analysis (word count) and log processing.
- **Set Implementation:** efficiently stores unique elements and supports operations like union and intersection.
- **Routing and DNS Query Caching:** stores mappings of domain names to IP addresses for fast access.
- **Inverted Index in Search Engines:** speeds up search by mapping words to the documents containing them.

## Operations

- **Set**.
- **Get**
- **Remove**
- **Keys**
- **Values**

## Example Code

```js
class HashTable {
  constructor(size = 53) {
    this.table = new Array(size);
    this.size = size;
  }

  _hash(key) {
    let total = 0;
    const PRIME = 31;
    for (let i = 0; i < Math.min(key.length, 100); i++) {
      total = (total * PRIME + key.charCodeAt(i)) % this.size;
    }
    return total;
  }

  set(key, value) {
    const index = this._hash(key);
    if (!this.table[index]) {
      this.table[index] = [];
    }
    for (let pair of this.table[index]) {
      if (pair[0] === key) {
        pair[1] = value;
        return;
      }
    }
    this.table[index].push([key, value]);
  }

  get(key) {
    const index = this._hash(key);
    if (this.table[index]) {
      for (let pair of this.table[index]) {
        if (pair[0] === key) {
          return pair[1];
        }
      }
    }
    return undefined;
  }

  remove(key) {
    const index = this._hash(key);
    if (this.table[index]) {
      this.table[index] = this.table[index].filter((pair) => pair[0] !== key);
    }
  }

  keys() {
    const keys = [];
    for (let bucket of this.table) {
      if (bucket) {
        for (let pair of bucket) {
          keys.push(pair[0]);
        }
      }
    }
    return keys;
  }

  values() {
    const values = [];
    for (let bucket of this.table) {
      if (bucket) {
        for (let pair of bucket) {
          values.push(pair[1]);
        }
      }
    }
    return values;
  }
}

const hashTable = new HashTable();

hashTable.set("name", "Alice");
hashTable.set("age", 18);
console.log(hashTable.get("name")); // Output: Alice
console.log(hashTable.get("age")); // Output: 18
hashTable.set("age", 19);
console.log(hashTable.get("age")); // Output: 19
console.log(hashTable.keys()); // Output: ["name", "age"]
console.log(hashTable.values()); // Output: ["Alice", 19]
hashTable.remove("age");
console.log(hashTable.get("age")); // Output: undefined
```
