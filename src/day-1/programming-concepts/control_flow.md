# Control flow in rust

### If expressions

In Rust, `if` expressions are used to branch code depending on conditions. The basic syntax is:

```rust
fn main() {
    let number = 3;
    if condition {
        // code block for datisfied condition
    } else {
        // code block for unsatisfied condition
    }
}
```

### Using if in a let statement

You can also use `if` expressions on the right side of a `let` statement to assign the outcome to a variable:

```rust
fn main() {
    let condition = true;
    let number = if condition { 5 } else { 6 };
    println!("The value of number is: {number}");
}
```

### Repetition with loops

Rust provides three types of loops: `loop`, `while`, and `for`. Let's explore each:

#### Repeating code with loop

The `loop` keyword tells Rust to execute a block of code repeatedly until you explicitly tell it to stop.

```rust
fn main() {
    loop {
        println!("again!");
    }
}
```

#### Conditional loops with while

A `while` loop runs as long as the condition is true:

```rust
fn main() {
    let mut number = 3;
    while number != 0 {
        println!("{number}!");

        number -= 1;
    }

    println!("LIFTOFF!!!");
}
```

#### Looping through a collection with for

You can use `for` to loop over the elements of a collection, such as an array:

```rust
fn main() {
    let a = [10, 20, 30, 40, 50];
    let mut index = 0;

    while index < 5 {
        println!("the value is: {}", a[index]);

        index += 1;
    }
}
```

### Returning values from loops

In Rust, you can return values from loops using the `return` statement.

```rust
fn main() {
    let mut sum = 0;

    loop {
        let input = std::io::stdin().read_line(&mut String::new())
            .expect("Failed to read line");

        if input.trim() == "quit" {
            break;
        }

        let num: u32 = input.trim().parse()
            .expect("Please type a number!");

        sum += num;

    }

    println!("The sum is: {sum}");
}
```

### Loop labels to disambiguate between multiple loops

To disambiguate between multiple loops, you can use labels:

```rust
fn main() {
    'outer: for i in 1..3 {
        'inner: for j in 1..3 {
            if i == 2 && j == 2 {
                break 'outer;
            }
            println!("{} * {} = {}", i, j, i * j);
        }
    }
}
```