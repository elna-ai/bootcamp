# Packages and Crates

In Rust, packages and crates are fundamental concepts for organizing and distributing your code.

### Packages

A package is a collection of related libraries, executables, or other assets that can be used together to build a larger project. Think of it as a directory containing multiple Rust files, along with their corresponding dependencies.

Example:
```rust
[package]
name = "my_package"
version = "0.1.0"

[dependencies]
log = "0.4.14"
serde = "1.0.126"
```
In this example, `my_package` is a package with two dependencies: `log` and `serde`.

### Crates

A crate is a single library or executable that can be used in your project. Think of it as a single file containing code you want to use elsewhere.

Example:
```rust
use log::info;
use serde::{Deserialize, Serialize};

#[derive(Debug, Serialize, Deserialize)]
struct MyStruct {
    foo: String,
}

fn main() {
    info!("Hello from my crate!");
}
```
In this example, `my_crate` is a crate with a single executable that prints a message to the console.

### Benefits

* Organize your code into logical groups
* Share code between projects and teams
* Leverage existing libraries and dependencies

**Example Code**

Let's create a simple package and crate:
```rust
[package]
name = "my_package"
version = "0.1.0"

[dependencies]
log = "0.4.14"
```
```rust
use log::info;

fn main() {
    info!("Hello from my crate!");
}
```
**Output**

When you run the above code, you should see:
```
INFO: my_crate: Hello from my crate!
```

By using packages and crates, you can efficiently manage your Rust projects and share code with others.
