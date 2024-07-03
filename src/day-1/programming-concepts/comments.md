# Comments in Rust

In Rust, comments are used to provide additional explanation or context for code written by other developers.

There are two types of comments: single-line comments and multi-line comments.

### Single-Line Comments
------------------------

Single-line comments start with `//` and continue until the end of the line.

```rust
fn main() {
    let x = 5; // This is a single-line comment
}
```

### Multi-Line Comments
-------------------------

Multi-line comments start with `//` and can span multiple lines, ending when the next `//` or the end of the file is reached.

```rust
fn main() {
    // This is a multi-line comment that spans two lines
    // Comment line two
    // Comment line three
    let x = 5;
    let y = 10;
}
```

### Example Program with Comments
----------------------------------

Here's an example program that demonstrates how comments can be used to provide additional context:

```rust
fn main() {
    // This function calculates the sum of two numbers
    fn add(a: i32, b: i32) -> i32 {
        // Calculate the sum of a and b
        return a + b;
    }

    let result = add(2, 3);
    println!("The result is: {}", result);
}
```

In this example, the comments provide additional context about what each function does and how it works.