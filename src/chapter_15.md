## Bringing Paths into Scope with `use`

```rust,ignore
mod front_of_house {
    pub mod hosting {
        pub fn add_to_waitlist() {}
    }
}

use crate::front_of_house::hosting;
// or relative path:
// use self::front_of_house::hosting;

pub fn eat_at_restaurant() {
    hosting::add_to_waitlist();
    hosting::add_to_waitlist();
    hosting::add_to_waitlist();
}
```

When bringing in structs, enums, and other items with `use`, it’s idiomatic to specify the full path:

```rust,ignore
use std::collections::HashMap;

fn main() {
    let mut map = HashMap::new();
    map.insert(1, 2);
}
```

### Providing New Names with the `as` Keyword

```rust,ignore
use std::fmt::Result;
use std::io::Result as IoResult;

fn function1() -> Result {
    // --snip--
}

fn function2() -> IoResult<()> {
    // --snip--
}
```

### Re-exporting Names with `pub use`

```rust,ignore
mod front_of_house {
    pub mod hosting {
        pub fn add_to_waitlist() {}
    }
}

pub use crate::front_of_house::hosting;

pub fn eat_at_restaurant() {
    hosting::add_to_waitlist();
    hosting::add_to_waitlist();
    hosting::add_to_waitlist();
}
```

### Nested Paths

```rust,ignore
// --snip--
use std::cmp::Ordering;
use std::io;
// --snip--
```

becomes:

```rust,ignore
// --snip--
use std::{cmp::Ordering, io};
// --snip--
```

If items share subpath:

```rust,ignore
use std::io;
use std::io::Write;
```

becomes:

```rust,ignore
use std::io::{self, Write};
```

### Glob Operator

```rust,ignore
use std::collections::*;
```

Glob can obfuscate what names are in scope and where a name used in your program was defined.
