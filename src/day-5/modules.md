# Modules

We have seen how `impl` blocks let us namespace functions to a type.

Similarly, `mod` lets us namespace types and functions:

```rust
mod foo {
    pub fn do_something() {
        println!("In the foo module");
    }
}

mod bar {
    pub fn do_something() {
        println!("In the bar module");
    }
}

fn main() {
    foo::do_something();
    bar::do_something();
}
```
- Packages provide functionality and include a `Cargo.toml` file that describes
  how to build a bundle of 1+ crates.
- Crates are a tree of modules, where a binary crate creates an executable and a
  library crate compiles to a library.
- Modules define organization, scope, and are the focus of this section.

# Filesystem Hierarchy

Omitting the module content will tell Rust to look for it in another file:

```rust
mod garden;
```

This tells rust that the `garden` module content is found at `src/garden.rs`.
Similarly, a `garden::vegetables` module can be found at
`src/garden/vegetables.rs`.

The `crate` root is in:

- `src/lib.rs` (for a library crate)
- `src/main.rs` (for a binary crate)

Modules defined in files can be documented, too, using "inner doc comments".
These document the item that contains them -- in this case, a module.

```rust
//! This module implements the garden, including a highly performant germination
//! implementation.

// Re-export types from this module.
pub use garden::Garden;
pub use seeds::SeedPacket;

/// Sow the given seed packets.
pub fn sow(seeds: Vec<SeedPacket>) {
    todo!()
}

/// Harvest the produce in the garden that is ready.
pub fn harvest(garden: &mut Garden) {
    todo!()
}

```
#### Details
- Before Rust 2018, modules needed to be located at `module/mod.rs` instead of
  `module.rs`, and this is still a working alternative for editions after 2018.

- The main reason to introduce `filename.rs` as alternative to `filename/mod.rs`
  was because many files named `mod.rs` can be hard to distinguish in IDEs.

- Deeper nesting can use folders, even if the main module is a file:

```
src/
├── main.rs
├── top_module.rs
└── top_module/
    └── sub_module.rs
```

- The place rust will look for modules can be changed with a compiler directive:

```rust
#[path = "some/path.rs"]
mod some_module;
```

  This is useful, for example, if you would like to place tests for a module in
  a file named `some_module_test.rs`, similar to the convention in Go.

# Visibility

Modules are a privacy boundary:

- Module items are private by default (hides implementation details).
- Parent and sibling items are always visible.
- In other words, if an item is visible in module `foo`, it's visible in all the
  descendants of `foo`.

```rust
mod outer {
    fn private() {
        println!("outer::private");
    }

    pub fn public() {
        println!("outer::public");
    }

    mod inner {
        fn private() {
            println!("outer::inner::private");
        }

        pub fn public() {
            println!("outer::inner::public");
            super::private();
        }
    }
}

fn main() {
    outer::public();
}
```

#### Details

- Use the `pub` keyword to make modules public.

Additionally, there are advanced `pub(...)` specifiers to restrict the scope of
public visibility.

- See the
  [Rust Reference](https://doc.rust-lang.org/reference/visibility-and-privacy.html#pubin-path-pubcrate-pubsuper-and-pubself).
- Configuring `pub(crate)` visibility is a common pattern.
- Less commonly, you can give visibility to a specific path.
- In any case, visibility must be granted to an ancestor module (and all of its
  descendants).

# use, super, self

A module can bring symbols from another module into scope with `use`. You will
typically see something like this at the top of each module:

```rust
use std::collections::HashSet;
use std::process::abort;
```

## Paths

Paths are resolved as follows:

1. As a relative path:
   - `foo` or `self::foo` refers to `foo` in the current module,
   - `super::foo` refers to `foo` in the parent module.

2. As an absolute path:
   - `crate::foo` refers to `foo` in the root of the current crate,
   - `bar::foo` refers to `foo` in the `bar` crate.

#### Details

- It is common to "re-export" symbols at a shorter path. For example, the
  top-level `lib.rs` in a crate might have

  ```rust
  mod storage;

  pub use storage::disk::DiskStorage;
  pub use storage::network::NetworkStorage;
  ```

  making `DiskStorage` and `NetworkStorage` available to other crates with a
  convenient, short path.

- For the most part, only items that appear in a module need to be `use`'d.
  However, a trait must be in scope to call any methods on that trait, even if a
  type implementing that trait is already in scope. For example, to use the
  `read_to_string` method on a type implementing the `Read` trait, you need to
  `use std::io::Read`.

- The `use` statement can have a wildcard: `use std::io::*`. This is discouraged
  because it is not clear which items are imported, and those might change over
  time.
