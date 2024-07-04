# References and borrowing in rust

In Rust, a reference is an alias for a value. References are immutable by default and can't be changed after they're created. There are two types of references: shared references (`&`) and mutable references (`&mut`).

### Mutable references
--------------------

A mutable reference allows you to modify the original data. Here's an example:

```rust
let mut s = String::from("hello");
let r3 = &mut s; // no problem

println!("{r3}");
```

In this example, `s` is a mutable string and `r3` is a mutable reference to it.

### Dangling references
-------------------------

Rust ensures that references will never be dangling references. If you try to create a dangling reference, the compiler will prevent it:

```rust
fn dangle() -> &String {
    let s = String::from("hello");

    let r2 = &s;
}

// Error: cannot return a reference to a local data from `dangle`
```

### The rules of references
-----------------------------

The rules for combining mutable and immutable references are:

1. A value can have at most one owner (mutable reference) at any given time.
2. If you have a mutable reference to some data, you can't create another mutable reference to the same data until the first one goes out of scope.

Here's an example that demonstrates these rules:

```rust
fn main() {
    let mut s = String::from("hello");

    let r1 = &s; // no problem
    let r2 = &s; // no problem

    let r3 = &mut s; // BIG PROBLEM

    println!("{}, {}, and {}", r1, r2, r3);
}

// Error: cannot borrow `s` as mutable because it is also borrowed as immutable
```

In this example, the error message indicates that we can't create a new mutable reference (`r3`) until the previous immutable references (`r1` and `r2`) go out of scope.

To avoid these issues, you can use curly brackets to create a new scope:

```rust
fn main() {
    let mut s = String::from("hello");

    {
        let r1 = &mut s;
    } // r1 goes out of scope here, so we can make a new reference with no problems.

    let r2 = &s; // no problem
}
```

In this example, `r1` goes out of scope before we create the new mutable reference (`r2`), allowing us to create multiple references without issues.