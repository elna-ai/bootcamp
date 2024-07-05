# Writing Automated Tests in Rust

### How to write tests

In Rust, tests are functions that verify the expected behavior of non-test code. To create a test function, add the `#[test]` attribute before the `fn` declaration.

```rust
#[cfg(test)]
mod tests {
    // ...
}
```

### The anatomy of a test function

A typical test function performs three actions:

1. **Set up**: Initialize any necessary data or state.
2. **Run the code under test**: Execute the code being tested.
3. **Assert the results**: Verify that the expected outcome occurs.

### Checking Results with assert!

The `assert!` macro is used to verify that a condition is true. If the condition is false, the test will fail and print an error message.

```rust
#[test]
fn greeting_contains_name() {
    let result = greeting("Carol");
    assert!(result.contains("Carol"), "Greeting did not contain name, value was `{}`", result);
}
```

### Testing equality with `assert_eq!` and `assert_ne!`

The `assert_eq!` macro checks that two values are equal. The `assert_ne!` macro checks that two values are not equal.

```rust
#[test]
fn adder_test() {
    let result = add(2, 3);
    assert_eq!(result, 5);
}
```

### Adding custom failure messages

When a test fails, it's helpful to provide a descriptive error message. You can create custom failure messages using the `assert!` macro.

```rust
#[test]
fn greeting_contains_name() {
    let result = greeting("Carol");
    assert!(result.contains("Carol"), "Greeting did not contain name, value was `{}`", result);
}
```

### Checking for panics with should_panic

The `should_panic` attribute is used to test that a function panics under certain conditions.

```rust
#[test]
#[should_panic]
fn create_guess_with_invalid_value() {
    Guess::new(101);
}
```

**Example code and output**

Here's an example of testing the `greeting` function:

```rust
pub fn greeting(name: &str) -> String {
    format!("Hello, {}!", name)
}

#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn greeting_contains_name() {
        let result = greeting("Carol");
        assert!(result.contains("Carol"), "Greeting did not contain name, value was `{}`", result);
    }
}
```

**Output**

When you run the test with `cargo test`, you'll see the following output:

```bash
running 1 test

test tests::greeting_contains_name ... FAILED

failures:
    tests::greeting_contains_name

test result: FAILED. 0 passed; 1 failed; 0 ignored; 0 measured; 0 filtered out; finished in 0.00s
```

This output indicates that the test has failed, and provides a descriptive error message.

I hope this helps! Let me know if you have any questions or need further clarification.
