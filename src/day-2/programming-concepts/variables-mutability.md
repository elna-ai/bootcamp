# Variables

Rust provides type safety via static typing. Variable bindings are made with
`let`:

```rust
fn main() {
  let x: i32 = 10;
  println!("x: {x}");
  // x = 20;
  // println!("x: {x}");
}
```

In RUST variables are immutable by default. 

When a variable is immutable, once a value is bound to a name, you can’t change that value.


However, you still have the option to make your variables mutable by adding mut in front of the variable name

```rust
fn main() {
  let mut x: i32 = 10;
  println!("x: {x}");
  x = 20;
  println!("x: {x}");
}
```


# Shadowing

If you declare a new variable with the same name as a previous variable. Rustaceans say that the first variable is shadowed by the second, which means that the second variable is what the compiler will see when you use the name of the variable.

```rust
fn main() {
  let x = 5;

  let x = x + 1;

  {
    let x = x * 2;
    println!("The value of x in the inner scope is: {x}");
  }

  println!("The value of x is: {x}");
}
```


