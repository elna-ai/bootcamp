# Defining and instantiating structs in rust

### Defining structs

In Rust, a struct is a way to group related data together. To define a struct, you start with the `struct` keyword followed by the name of the struct. Inside the curly brackets, you specify the fields and their types.

```rust
struct User {
    active: bool,
    username: String,
    email: String,
    sign_in_count: u64,
}
```

### Instantiating structs

To create an instance of a struct, you use the same name as the struct followed by curly brackets containing key-value pairs. The keys are the names of the fields and the values are the data to be stored in those fields.

```rust
let user = User {
    active: true,
    username: "john_doe".to_string(),
    email: "johndoe@example.com".to_string(),
    sign_in_count: 10,
};
```

### Using field init shorthand

Rust provides a shorthand way to initialize fields using the following syntax:

```rust
fn build_user(email: String, username: String) -> User {
    User {
        active: true,
        username,
        email,
        sign_in_count: 1,
    }
}
```

### Creating instances from other instances with struct update syntax

You can create a new instance of a struct by updating an existing one using the following syntax:

```rust
let mut user = User {
    active: true,
    username: String::from("john_doe"),
    email: String::from("johndoe@example.com"),
    sign_in_count: 10,
};

let updated_user = User {
    ..user,
    email: String::from("new_email@example.com"),
};
```

### Using tuple structs without named fields

Tuple structs allow you to define a struct with unnamed fields. This is useful when you want to give the whole tuple a name and make it a different type from other tuples.

```rust
struct Point(i32, i32);
let point = Point(10, 20);
```

### Unit-like structs without any fields

You can define a struct without any fields using the following syntax:

```rust
struct AlwaysEqual;

fn main() {
    let subject = AlwaysEqual;
}
```

### Ownership of struct data

In Rust, each instance of a struct owns its own data. This means that when you create an instance of a struct, you are responsible for managing the memory of its fields.

For example:

```rust
let user = User {
    active: true,
    username: "john_doe".to_string(),
    email: "johndoe@example.com".to_string(),
    sign_in_count: 10,
};
```

In this example, `user` owns the data stored in its fields.