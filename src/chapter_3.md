## Types

### Scaler Types

Integers, floating-point numbers, Booleans, and characters

#### Integer

Integer Types

| Length   | Signed  | Unsigned |
| -------- | ------- | -------- |
| 8-bit    | `i8`    | `u8`     |
| 16-bit   | `i16`   | `u16`    |
| 32-bit   | `i32`   | `u32`    |
| 64-bit   | `i64`   | `u64`    |
| 128-bit  | `i128`  | `u128`   |
| arch dep | `isize` | `usize`  |

Integer Literals

| Number literals  | Example       |
| ---------------- | ------------- |
| Decimal          | `98_222`      |
| Hex              | `0xff`        |
| Octal            | `0o77`        |
| Binary           | `0b1111_0000` |
| Byte (`u8` only) | `b'A'`        |

#### Floating-Point

Defaults to `f64`

```rust,ignore
fn main() {
    let x = 2.0; // f64

    let y: f32 = 3.0; // f32
}
```

#### Boolean

```rust,ignore
fn main() {
    let t = true;

    let f: bool = false; // with explicit type annotation
}
```

#### Character

`char` literals specified with single quoates, as opposed to string literals using double quotes

```rust,ignore
fn main() {
    let c = 'z';
    let z = 'ℤ';
    let heart_eyed_cat = '😻';
}
```

Rust’s `char` type is four bytes in size and represents a Unicode Scalar Value from `U+0000` to `U+D7FF` and `U+E000` to `U+10FFFF`

### Compoound Types

Tuples and arrays

#### Tuple

```rust,ignore
fn main() {
    let tup: (i32, f64, u8) = (500, 6.4, 1);
}
```

Accessing tuple elements with `.` notation

```rust,ignore
fn main() {
    let x: (i32, f64, u8) = (500, 6.4, 1);

    let five_hundred = x.0;

    let six_point_four = x.1;

    let one = x.2;
}
```

#### Array

Arrays have fixed length and elements of the same type

```rust,ignore
let a: [i32; 5] = [1, 2, 3, 4, 5];
```

Initializing and filling an array with elements `3` and length `5`:

```rust,ignore
let a = [3; 5];
```

Accessing array elements:

```rust,ignore
fn main() {
    let a = [1, 2, 3, 4, 5];

    let first = a[0];
    let second = a[1];
}
```
