# flatmap

Fast and efficient linear map and set for small collections.

## Features

- `FlatMap<K, V>` - Dynamic linear map with O(n) operations
- `FlatSet<K>` - Dynamic linear set with O(n) operations
- `ConstantFlatMap<K, V, N>` - Fixed-size map with compile-time capacity
- `ConstantFlatSet<K, N>` - Fixed-size set with compile-time capacity

## Usage

```rust
use flatmap::{FlatMap, FlatSet, ConstantFlatMap, ConstantFlatSet};

// Dynamic map
let mut map = FlatMap::new();
map.insert("key", 42);
assert_eq!(map.get(&"key"), Some(&42));

// Dynamic set
let mut set = FlatSet::new();
set.insert("item");
assert!(set.has(&"item"));

// Fixed-size map
let const_map = ConstantFlatMap::from([("a", 1), ("b", 2)]);
assert_eq!(const_map.get(&"a"), Some(&1));

// Fixed-size set
let const_set = unsafe { ConstantFlatSet::from_entries_unchecked([1, 2, 3]) };
assert!(const_set.has(&2));
```

## Performance

Optimized for small collections where linear search is faster than hash-based lookups due to better cache locality and lower overhead.

## License

MIT