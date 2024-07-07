# Common Collections in Rust

### Storing Lists of Values with Vectors

Vectors are a fundamental data structure in Rust, allowing you to store a variable number of values next to each other. Unlike arrays, vectors can grow or shrink in size dynamically.

**Example Code:**
```rust
let mut scores = vec![10, 20, 30];
scores.push(40);
println!("{:?}", scores); // [10, 20, 30, 40]
```
### Storing UTF-8 Encoded Text with Strings

In Rust, the `String` type is a collection of characters that can store more than just ASCII. This is due to Rust's support for UTF-8 encoding.

**Example Code:**
```rust
let mut s = String::new();
s.push_str("hello");
println!("{}", s); // "hello"
```
### Storing Keys with Associated Values in Hash Maps

Hash maps, also known as hash tables or associative arrays, allow you to store keys associated with values. This structure is useful when you want to look up data based on a key rather than an index.

**Example Code:**
```rust
use std::collections::HashMap;

let mut scores = HashMap::new();
scores.insert("Blue", 10);
scores.insert("Yellow", 50);
println!("{:?}", scores); // {"Blue": 10, "Yellow": 50}
```
In summary, Rust provides three fundamental collections for storing and managing data: vectors for lists of values, strings for UTF-8 encoded text, and hash maps for storing keys with associated values.
