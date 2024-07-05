# Traits: Defining shared behavior

Traits in Rust allow us to define shared behavior for a particular type and ensure that any concrete type implementing this trait provides the required functionality. This helps reduce duplication and improves code maintainability.

## Defining a trait

To define a trait, we use the `pub trait` keyword followed by the name of the trait. For example:
```rust
pub trait Summary {
    fn summarize(&self) -> String;
}
```
In this example, we're defining a trait called `Summary` that requires any implementing type to provide an implementation for the `summarize` method.

## Implementing a trait on a type

To implement a trait on a specific type, we use the `impl` keyword followed by the name of the trait. For example:
```rust
pub struct NewsArticle {
    headline: String,
    author: String,
    location: String,
}

impl Summary for NewsArticle {
    fn summarize(&self) -> String {
        format!("{} - {}", self.headline, self.author)
    }
}
```
In this example, we're implementing the `Summary` trait on the `NewsArticle` struct. The implementation provides a specific way to summarize a news article.

## Default implementations

Traits can also provide default implementations for methods. This allows us to provide a fallback behavior if a type doesn't implement the method itself. For example:
```rust
pub trait Summary {
    fn summarize(&self) -> String;
}

impl Summary for i32 {
    fn summarize(&self) -> String {
        "No summary available".to_string()
    }
}
```
In this example, we're providing a default implementation for the `Summary` trait on the `i32` type. If any concrete type implementing `Summary` doesn't provide its own implementation, it will fall back to this default behavior.

## Traits as parameters

Traits can also be used as parameters in functions and methods. This allows us to constrain the types that can be passed as arguments to a function or method. For example:
```rust
pub fn notify(item: &impl Summary) {
    println!("{}", item.summarize());
}
```
In this example, we're defining a `notify` function that takes an `item` of type `&impl Summary`, which means it can take any type that implements the `Summary` trait. The function then calls the `summarize` method on the item and prints the result.

Example Code:
```rust
pub trait Summary {
    fn summarize(&self) -> String;
}

pub struct NewsArticle {
    headline: String,
    author: String,
    location: String,
}

impl Summary for NewsArticle {
    fn summarize(&self) -> String {
        format!("{} - {}", self.headline, self.author)
    }
}

fn main() {
    let article = NewsArticle {
        headline: "Rust Programming Language".to_string(),
        author: "The Author".to_string(),
        location: "Location".to_string(),
    };

    println!("{}", article.summarize()); // Output: Rust Programming Language - The Author
}
```
Output:
```
Rust Programming Language - The Author
```
