# Enums and pattern matching in rust

### Defining an enum
An enum (short for "enumeration") is a user-defined type that represents a set of named values. In Rust, you can define an enum using the `enum` keyword.

Example:
```rust
enum Coin {
    Penny,
    Nickel,
    Dime,
    Quarter(UsState),
}
```
### Enum values

An enum can have multiple values, each with its own unique name. These values are called "variants". In the example above, `Penny`, `Nickel`, and `Dime` are the variants of the `Coin` enum.

### The Option Enum and Its Advantages Over Null Values

Rust's `Option<T>` enum is a special type that represents either Some value or None. This allows you to explicitly handle the absence of a value, rather than relying on null values. Using `Option<T>` can help prevent runtime errors and make your code more robust.

Example:
```rust
let maybe_int = Some(5);
match maybe_int {
    Some(i) => println!("Value: {}", i),
    None => println!("No value"),
}
```
### The match Control Flow Construct
The `match` control flow construct is used to execute different blocks of code based on the value of an expression. In Rust, you can use `match` with enums and pattern matching to extract values from enum variants.

Example:
```rust
enum Coin {
    Penny,
    Nickel,
    Dime,
    Quarter(UsState),
}

let coin = Coin::Quarter(UsState::Alabama);
match coin {
    Coin::Penny => println!("Penny!"),
    Coin::Nickel => println!("Nickel!"),
    Coin::Dime => println!("Dime!"),
    Coin::Quarter(state) => println!("Quarter from {state:?}!"),
}
```
### Patterns that bind to values
Patterns are used in `match` expressions to bind values to variables. You can use patterns like literals, identifiers, and tuple structs to match enum variants.

Example:
```rust
enum Coin {
    Penny,
    Nickel,
    Dime,
    Quarter(UsState),
}

let coin = Coin::Quarter(UsState::Alabama);
match coin {
    Coin::Penny => println!("Penny!"),
    x => println!("Other: {x:?}"), // x binds to the value
}
```
### Matching with Option<T>
You can use `Option<T>` in a `match` expression to handle the absence of a value.

Example:
```rust
let maybe_int = Some(5);
match maybe_int {
    Some(i) => println!("Value: {}", i),
    None => println!("No value"),
}
```
### Matches are exhaustive
Rust's `match` expressions are exhaustive, meaning that every possible variant of an enum must be handled. If you don't handle all the variants, the compiler will error.

Example:
```rust
enum Coin {
    Penny,
    Nickel,
    Dime,
}

let coin = Coin::Quarter(UsState::Alabama); // Error: Quarter is not handled!
match coin {
    Coin::Penny => println!("Penny!"),
    Coin::Nickel => println!("Nickel!"),
    _ => println!("Other"), // Not exhaustive!
}
```
### Catch-all Patterns and the _ Placeholder
The `_` placeholder can be used as a catch-all pattern to handle any variant that doesn't match the previous patterns.

Example:
```rust
enum Coin {
    Penny,
    Nickel,
    Dime,
    Quarter(UsState),
}

let coin = Coin::Quarter(UsState::Alabama);
match coin {
    Coin::Penny => println!("Penny!"),
    x => println!("Other: {x:?}"), // x binds to the value
}
```
### Concise control flow with if let
The `if let` statement is a concise way to handle enums and pattern matching. It combines an `if` statement with a `match` expression.

Example:
```rust
enum Coin {
    Penny,
    Nickel,
    Dime,
    Quarter(UsState),
}

let coin = Coin::Quarter(UsState::Alabama);
let mut count = 0;
if let Coin::Quarter(state) = coin {
    println!("State quarter from {state:?}!");
} else {
    count += 1;
}
```
Output:
```text
State quarter from Alabama!
```
