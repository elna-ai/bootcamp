# Data Types

Rust is a statically typed language, which means that it must know the types of all variables at compile time. The compiler can usually infer what type we want to use based on the value and how we use it.

## **Scalar Types**

A scalar type represents a single value. Rust has four primary scalar types: integers, floating-point numbers, Booleans, and characters. You may recognize these from other programming languages. Let’s jump into how they work in Rust.




Here are some basic built-in types, and the syntax for literal values of each
type.

|                        | Types                                      | Literals                       |
| ---------------------- | ------------------------------------------ | ------------------------------ |
| Signed integers        | `i8`, `i16`, `i32`, `i64`, `i128`, `isize` | `-10`, `0`, `1_000`, `123_i64` |
| Unsigned integers      | `u8`, `u16`, `u32`, `u64`, `u128`, `usize` | `0`, `123`, `10_u16`           |
| Floating point numbers | `f32`, `f64`                               | `3.14`, `-10.0e20`, `2_f32`    |
| Unicode scalar values  | `char`                                     | `'a'`, `'α'`, `'∞'`            |
| Booleans               | `bool`                                     | `true`, `false`                |

The types have widths as follows:

- `iN`, `uN`, and `fN` are _N_ bits wide,
- `isize` and `usize` are the width of a pointer,
- `char` is 32 bits wide,
- `bool` is 8 bits wide.

```rust
fn main() {
  let x = 2.0; // f64

  let y: f32 = 3.0; // f32
}
```

```rust
fn main() {
  let t = true;

  let f: bool = false; // with explicit type annotation
}

```

## **Numeric Operations**

Rust supports the basic mathematical operations: addition, subtraction, multiplication, division, and remainder.

```rust
fn main() {
  // addition
  let sum = 5 + 10;

  // subtraction
  let difference = 95.5 - 4.3;

  // multiplication
  let product = 4 * 30;

  // division
  let quotient = 56.7 / 32.2;
  let truncated = -5 / 3; // Results in -1

  // remainder
  let remainder = 43 % 5;
}

```



## **Compound Types**

Compound types can group multiple values into one type. Rust has two primitive compound types: tuples and arrays.

1. **The Tuple Type:**

tuple is a general way of grouping together a number of values with a variety of types into one compound type. Tuples have a fixed length: once declared, they cannot grow or shrink in size.

```rust
fn main() {
  let tup: (i32, f64, u8) = (500, 6.4, 1);
}
```

Destructuring of Tuple

```rust 
fn main() {
  let tup = (500, 6.4, 1);
  let (x, y, z) = tup;
  println!("The value of y is: {y}");
}
```

We can also access a tuple element directly by using a period `(.)` followed by the index of the value we want to access. 

For example:


```rust
fn main() {
  let x: (i32, f64, u8) = (500, 6.4, 1);
  
  let five_hundred = x.0;
  
  let six_point_four = x.1;
  
  let one = x.2;
}
```

2. **Array Type**

Unlike a tuple, every element of an *array* must have the same type. Unlike arrays in some other languages, arrays in Rust have a fixed length.

We write the values in an array as a comma-separated list inside *square brackets*:

```rust
fn main() {
  let a = [1, 2, 3, 4, 5];
}
```

An array is a single chunk of memory of a known, fixed size that can be allocated on the stack. You can access elements of an array using indexing, like this:

```rust
fn main() {
  let a = [1, 2, 3, 4, 5];
  let first = a[0];
  let second = a[1];
}
```

<details>

There are a few syntaxes which are not shown above:

- All underscores in numbers can be left out, they are for legibility only. So
  `1_000` can be written as `1000` (or `10_00`), and `123_i64` can be written as
  `123i64`.

</details>
