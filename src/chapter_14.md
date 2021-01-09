## Packages, Crates and Modules

- **Packages:** A Cargo feature that lets you build, test, and share crates
- **Crates:** A tree of modules that produces a library or executable
- **Modules** and **use:** Let you control the organization, scope, and
  privacy of paths
- **Paths:** A way of naming an item, such as a struct, function, or module

### Packages and Crates

Crates are binary packages or library packages.

Binary packages are created with `cargo new` and have `src/main.rs` as the crate root.

Library crates are created with `cargo new --lib` and have ` src/lib.rs` as the crate root.

### Modules

src/lib.rs

```rust,ignore
mod front_of_house {
    mod hosting {
        fn add_to_waitlist() {}

        fn seat_at_table() {}
    }

    mod serving {
        fn take_order() {}

        fn serve_order() {}

        fn take_payment() {}
    }
}
```

The crate's _module tree_:

```text
crate
 └── front_of_house
     ├── hosting
     │   ├── add_to_waitlist
     │   └── seat_at_table
     └── serving
         ├── take_order
         ├── serve_order
         └── take_payment
```

### Paths

- _absolute path_ starts from a crate root by using a crate name or a
  literal `crate`.
- _relative path_ starts from the current module and uses `self`, `super`, or
  an identifier in the current module.

```rust,ignore
mod front_of_house {
    mod hosting {
        pub fn add_to_waitlist() {}
    }
}

pub fn eat_at_restaurant() {
    // Absolute path
    crate::front_of_house::hosting::add_to_waitlist();

    // Relative path
    front_of_house::hosting::add_to_waitlist();
}
```

Prefer to specify absolute paths because it’s more likely to move code definitions and item calls independently of each other.

### Exposing Paths with `pub` Keyword

Items in modules are private by default.

The `pub` keyword on a module only lets code in its ancestor modules refer to it.

### Starting Relative Paths with `super`

Similar to filesystem `..`, wen can construct relative paths that begin in the parent module by using `super`.

```rust,ignore
fn serve_order() {}

mod back_of_house {
    fn fix_incorrect_order() {
        cook_order();
        super::serve_order();
    }

    fn cook_order() {}
}
```

### Making Structs and Enums Public

Fields in a `struct` are made public on a case-by-case basis.

If an `enum` is made public, all its variants are then public.

```rust,ignore
mod back_of_house {
    pub struct Breakfast {
        pub toast: String,
        seasonal_fruit: String,
    }

    pub enum Appetizer {
        Soup,
        Salad,
    }
}
```
