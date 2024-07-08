# Program Memory


In Rust programming, memory can be categorized primarily into stack memory and heap memory, each serving different purposes and having different characteristics.

Here’s a breakdown of the different types of memory in Rust:

### 1. **Stack Memory**
- **Characteristics:**
  - Continuous area of memory for local variables.
  - Fast allocation and deallocation.
  - Data is stored in a Last-In-First-Out (LIFO) manner.
  - Limited in size.
  - Suitable for data with a known, fixed size at compile time.
- **Usage:**
  - Local variables.
  - Function arguments.
  - Return values.


### 2. **Heap Memory**
- **Characteristics:**
  - Slower allocation and deallocation compared to the stack.
  - Data can be of dynamic size.
  - Larger in size than the stack.
  - Suitable for data that needs to live beyond the scope of a function.
- **Usage:**
  - Dynamic data structures like vectors, strings, and hash maps.
  - Data that needs to be shared or transferred across different parts of a program.


### Examples:

####Stack Allocation:

```rust
fn main() {
  let x = 5;
  let y = x; // Both x and y are on the stack
}
```

#### Heap Allocation:

```rust
fn main() {
  let s = String::from("hello"); // s is on the heap
}
```
