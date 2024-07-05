# Command line arguments

### Accepting command line arguments
Rust provides a way to accept command-line arguments through the `std::env::args` function, which returns an iterator of command-line arguments passed to the program.

### Reading the argument values
To read the values of command-line arguments, we can use the `collect` method on the iterator returned by `std::env::args`, and specify that we want a vector of strings. This will store all the command-line arguments in a single vector.

### Saving the argument values in variables
Once we have collected the command-line arguments into a vector, we can access each argument individually using indexing or iteration.

Here is an example code snippet:
```rust
use std::env;

fn main() {
    let args: Vec<String> = env::args().collect();
    
    println!("{:?}", args);
}
```
Output:
```
$ cargo run -- hello world
hello
world
[src/main.rs:4] args = ["target/debug/minigrep", "hello", "world"]
```
Note that the first element in the vector is always the name of the executable, so you may want to skip this if you're not interested in it.
