# :chart_with_upwards_trend: Data Structure : Hashing Concepts

##### DAT ~ Direct Address Table

Type of data structure used to represent a universe of keys explicitly. Each key has its unique slot in the table, and the value associated with a key is stored in its specific slot. This eliminates the need for any hashing function.

While DATs provide constant-time operations and are straightforward, they are only suitable for specific use cases due to their space requirements. It's essential to evaluate the application's needs and the universe of keys before choosing this data structure.

##### DAT: Algorithmic Complexity

- **Insertion**: O(1)
- **Deletion**: O(1)
- **Search**: O(1)

Since DAT uses direct addressing, it can achieve constant time complexity for these basic operations.

##### DAT: Applications

- The universe of possible keys is relatively small, making it feasible to allocate memory for all potential keys.
- Almost all keys from this universe are present, ensuring that the memory isn't wasted.
- We need constant-time operations for insertion, deletion, and search.
- There's no need for any advanced operations like predecessor, successor, etc.

##### DAT: Limitations

- DATs can be memory-intensive if the universe of keys is large but only a small subset is used.
- Not suitable when the universe of keys is dynamic or very large, as it can lead to a lot of wasted space.
