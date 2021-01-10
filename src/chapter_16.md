## Modules

Using a semicolon after mod `front_of_house` rather than using a block tells Rust to load the contents of the module from another file with the same name as the module.

src/lib.rs

```rust,ignore
mod front_of_house;

pub use crate::front_of_house::hosting;

pub fn eat_at_restaurant() {
    hosting::add_to_waitlist();
    hosting::add_to_waitlist();
    hosting::add_to_waitlist();
}
```

src/front_of_house.rs

```rust,ignore
pub mod hosting {
    pub fn add_to_waitlist() {}
}
```

Module filenames may also be the name of the module as a directory with the contents in a file named `mod.rs` within that directory.
