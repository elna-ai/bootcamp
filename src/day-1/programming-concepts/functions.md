# Functions
### Introduction to Rust Functions
Functions are a fundamental concept in Rust programming.
They enable you to organize your code into reusable blocks of logic,
making your programs more efficient and easier to maintain.

```rust
fn main() {
    println!("Hello, world!");
}
```
Functions can take arguments, return values, and be reused throughout
your program. The syntax for defining a function is as follows:

```rust
fn function_name(parameters) -> return_type {
    // function body
}
```
In Rust, functions are executed in the order they are defined.
When you call a function, the code within its block is executed
until it reaches the end or returns a value.

Rust also supports higher-order functions, which allow you to pass functions
as arguments to other functions or return them from functions. This enables
more complex and powerful programming patterns.

## Passing arguments to rust functions

When declaring a function in Rust, you must specify the type of each parameter. For example:
```rust
fn another_function(x: i32) {
    println!("The value of x is: {x}");
}
```
In this example, another_function takes one argument x which is specified as an i32.

When calling a function with arguments, you must provide the correct types. For instance:
```rust
fn main() {
    another_function(5); // Passes an i32 value to the function
}
```

In this example, we pass the value 5 to the another_function, which is an i32. The function will receive this value and use it as needed.

## Passing multiple parameters

You can also define a function with multiple parameters by separating them with commas:

```rust
fn print_labeled_measurement(value: i32, label: char) {
    println!("{}: {}", label, value);
}
```

To call such a function, you would provide both values as arguments:
```rust
fn main() {
    print_labeled_measurement(5, 'h'); // Passes an i32 and a char to the function
}
```
In this example, we pass the values 5 (an i32) and 'h' (a char) to the print_labeled_measurement function.

This note will be useful for taking a live session on passing arguments to Rust functions.

## Functions with return values

In Rust, functions can return values to the code that calls them. We don't name return values, but we must declare their type after an arrow (->). In Rust, the return value of a function is synonymous with the value of the final expression in the block of the function body.

Here's an example:

```rust
fn five() -> i32 {
    5
}

fn main() {
    let x = five();
}
```

n this example, the five function returns an i32 value. The return value is implicit and is evaluated to be the result of the final expression in the function body.

### Returning early from a function

You can also use the return keyword to explicitly return a value from a function:

```rust
fn five() -> i32 {
    5
    // You can add more code here, but since we've already returned,
    // it won't be executed.
    return 5;
}
```
However, most functions implicitly return the result of the final expression in their body.

This note will be used to take a live session.