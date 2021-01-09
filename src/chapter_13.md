## Concise Control Flow with `if let`

```rust,ignore
    let some_u8_value = Some(0u8);
    match some_u8_value {
        Some(3) => println!("three"),
        _ => (),
    }
```

equivalent to:

```rust,ignore
    if let Some(3) = some_u8_value {
        println!("three");
    }
```

`if let` is more concise than `match` but does not provide exhaustive checking

Combining `if let` with `else`

```rust,ignore
    if let Some(3) = some_u8_value {
        println!("three");
    } else {
        println!("not three");
    }
```
