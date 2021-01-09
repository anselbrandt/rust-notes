## Enums and Pattern Matching

#### Defining Enumerations

```rust,ignore
enum IpAddrKind {
    V4,
    V6,
}
```

Variations of enums are namespaced under their identifier.

```rust,ignore
 let four = IpAddrKind::V4;
 let six = IpAddrKind::V6;
```

#### Enum Associated Values

```rust,ignore
    enum IpAddr {
        V4(String),
        V6(String),
    }

    let home = IpAddr::V4(String::from("127.0.0.1"));

    let loopback = IpAddr::V6(String::from("::1"));
```

Enum variants can have different types and amounts of associated data.

```rust,ignore
   enum IpAddr {
        V4(u8, u8, u8, u8),
        V6(String),
    }

    let home = IpAddr::V4(127, 0, 0, 1);

    let loopback = IpAddr::V6(String::from("::1"));
```

or

```rust,ignore
enum Message {
    Quit,
    Move { x: i32, y: i32 },
    Write(String),
    ChangeColor(i32, i32, i32),
}
```

- `Quit` has no data associated with it at all.
- `Move` includes an anonymous struct inside it.
- `Write` includes a single `String`.
- `ChangeColor` includes three `i32` values.

#### Methods on Enums

```rust,ignore
    impl Message {
        fn call(&self) {
            // method body would be defined here
        }
    }

    let m = Message::Write(String::from("hello"));
    m.call();
```

### Option Enum

Rust does not have null, but has `Option` type, which can be something or nothing.

It is defined by the standard library as follows:

```rust,ignore
enum Option<T> {
    Some(T),
    None,
}
```

`Option<T>`, `Some` and `None` are included in the prelude and do not need to be brought into scope, and therefore do not require the `Option::` prefix.

```rust,ignore
    let some_number = Some(5);
    let some_string = Some("a string");

    let absent_number: Option<i32> = None;
```

If a variable is initialized with `None` a type needs to be specified in the generic.

#### Does not compile:

```rust,ignore
    let x: i8 = 5;
    let y: Option<i8> = Some(5);

    let sum = x + y;
```

#### \*`Option<T>` must be converted to `T` before performing `T` operations with it.
