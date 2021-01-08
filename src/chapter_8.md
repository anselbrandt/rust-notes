## Slice Type

Slices reference a contiguous sequence of elements in a collection. Slices do not have ownership.

### String Slice

A _string slice_ is a reference to part of a `String`.

```rust,ignore
 let s = String::from("hello world");

    let hello = &s[0..5];
    let world = &s[6..11];
```

Starting and trailing indices are optional:

```rust,ignore
let s = String::from("hello");

let slice = &s[0..2];
let slice = &s[..2];

let slice = &s[3..len];
let slice = &s[3..];

let slice = &s[0..len];
let slice = &s[..];
```

Example function returning string slice, `&str`:

```rust,ignore
fn first_word(s: &String) -> &str {
    let bytes = s.as_bytes();

    for (i, &item) in bytes.iter().enumerate() {
        if item == b' ' {
            return &s[0..i];
        }
    }

    &s[..]
}
```

Where `enumerate` returns a tuple of `i` and `&item`

### String Literals are Slices

String literals are stored inside the binary and are slices pointing to a specific point of the binary.

```rust,ignore
let s = "Hello, world!";
```

Therefore `s` is of type `&str` and is immutable, as string slices are immutable references.

### Other Slices

Array slices:

```rust,ignore
let a = [1, 2, 3, 4, 5];

let slice = &a[1..3];
```

This slice has type `&[i32]`
