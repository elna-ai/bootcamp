# Ownership in Rust

### What Is Ownership?

Ownership is a concept in Rust that manages memory through a system of rules. The compiler checks these rules, ensuring the program won't compile if they're violated. This approach eliminates runtime errors related to memory management.

### Ownership Rules

Ownership follows three main rules:

* Each value has an owner.
* There can be only one owner at a time.
* When the owner goes out of scope, the value will be dropped and freed.

### Variable Scope

In Rust, variables have scope. When a variable goes out of scope, it is dropped, releasing any resources it held. This ensures memory safety by preventing dangling pointers.

### The String Type

The `String` type in Rust represents a sequence of characters. It's implemented as a growable array on the heap, allowing for dynamic memory allocation and manipulation.

### Memory and Allocation

Rust uses **move** semantics to transfer ownership of data between variables or functions. This ensures that data is properly managed and released when no longer needed.

### Variables and Data Interacting with Move

When assigning a value to another variable using the `=` operator, Rust performs a move operation. This transfers ownership of the data from the original variable to the new one.

```rust
let s = String::from("hello"); // s owns the string
let t = s; // s moves its ownership to t
```

### Variables and Data Interacting with Clone

Some types, like `String`, implement the `Clone` trait. This allows for creating a copy of the data using the `clone()` method.

```rust
use std::string::String;

fn main() {
    let s = String::from("hello"); // s owns the string
    let t = s.clone(); // s clones its ownership to t
}
```

### Stack-Only Data: Copy

Some types, like `i32`, are stored on the stack and can be copied using the `=` operator.

```rust
let x = 5; // x is a copy of 5
```

### Ownership and Functions

Ownership rules apply to functions in Rust. When calling a function, any variables passed as arguments will transfer ownership to the function.

```rust
fn takes_ownership(some_integer: i32) {
    println!("{some_integer}");
}

let s = String::from("hello"); // s owns the string
takes_ownership(s); // s moves its ownership to the function
```

### Return Values and Scope

Return values in Rust can transfer ownership. When a function returns a value, it will move its ownership to the caller.

```rust
fn gives_ownership() -> String {
    String::from("hello");
}

let s = gives_ownership(); // gives_ownership moves its return value into s
```

These notes provide an overview of ownership in Rust, including its rules, scope, and interactions with variables and functions.
