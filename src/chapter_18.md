## Strings

String slices `str`, in the core language, usually used in borrowed form `&str`, are references to UTF-8 encoded string data.

String literals, stored in the binary, are string slices.

The `String` type, from the standard library, is a growable, mutable, owned UTF-8 encoded string type.

The standard library also includes `OsString`, `OsStr`, `CString` and `CStr`.

### Creating a New String

```rust,ignore
    let mut s = String::new();
```

#### Creating a `String` from a string literal

```rust,ignore
    let data = "initial contents";

    let s = data.to_string();

    // the method also works on a literal directly:
    let s = "initial contents".to_string();
```

```rust,ignore
    let hello = String::from("Hello");
    let hello = String::from("こんにちは");
    let hello = String::from("你好");
```

### Updating a String

```rust,ignore
    let mut s1 = String::from("foo");
    let s2 = "bar";
    s1.push_str(s2);
    println!("s2 is {}", s2);
```

`push_str` takes a string slice and does not assume ownership of the parameter.

```rust,ignore
    let mut s = String::from("lo");
    s.push('l');
```

`push` takes a single character

### Concatenation with the `+` Operator or the `format!` Macro

```rust,ignore
    let s1 = String::from("Hello, ");
    let s2 = String::from("world!");
    let s3 = s1 + &s2; // note s1 has been moved here and can no longer be used
```

The `+` operator requires a _reference_ to a `str` as the second parameter because the function signature for `add` looks like this:

```rust,ignore
fn add(self, s: &str) -> String {
```

Event though `s2` is a `String` Rust can _coerce_ `&String` into a `&str`. When calling `add`, Rust uses a _deref coercion_ to turn `&s2` into `&s2[..]`.

For more complicated string combining, we can use the `format!` macro:

```rust,ignore
    let s1 = String::from("tic");
    let s2 = String::from("tac");
    let s3 = String::from("toe");

    let s = format!("{}-{}-{}", s1, s2, s3);
```

`format!` does not take ownership of any parameters.

### Indexing into Strings

Because `String` is a wrapper over a `Vec<u8>` you cannot access individual characters by referencing them by index as UTF-8 characters may be 1 or more bytes.

### Slicing Strings

If it is necessary to use indices to create string slices, a range `[]` must be specified:

```rust,ignore
let hello = "Здравствуйте";

let s = &hello[0..4];
```

\*If the range does not line up with a character boundary, the program will panic.

### Iterating Over Strings

`char`

```rust,ignore
for c in "नमस्ते".chars() {
    println!("{}", c);
}
```

`bytes`

```rust,ignore
for b in "नमस्ते".bytes() {
    println!("{}", b);
}
```
