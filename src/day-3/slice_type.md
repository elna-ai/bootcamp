# The slice type in rust

### String slices

In Rust, a string slice is a reference to a contiguous sequence of elements in a collection. It does not have ownership and allows you to reference part of a larger string without copying the entire string.

Example:
```rust
let s = "hello";
let hello = &s[0..4];
println!("{}", hello); // Output: "hello"
```
In this example, `hello` is a string slice that references the first 5 characters of the string `s`.

### String literals as slices

String literals can be treated as slices. This means you can use the same syntax to create a slice from a string literal as you would for a regular string.

Example:
```rust
let hello = "hello";
let world = &hello[1..4];
println!("{}", world); // Output: "ello"
```
In this example, `world` is a string slice that references the characters 6-10 of the string literal `"hello"`.

### Other slices

Slices are not limited to strings. You can create slices for other collection types such as vectors and arrays.

Example:
```rust
let arr = [1, 2, 3, 4, 5];
let slice = &arr[1..3];
println!("{:?}", slice); // Output: [2, 3]
```
In this example, `slice` is a reference to the second and third elements of the array `arr`.

Note that string slices must occur at valid UTF-8 character boundaries. Attempting to create a slice in the middle of a multibyte character will result in an error.
