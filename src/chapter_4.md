## Functions

#### Return Values

Return values are expressions without end of line semicolons. Semicolons denote statements.

```rust,ignore
fn main() {
    let x = plus_one(5);

    println!("The value of x is: {}", x);
}

fn plus_one(x: i32) -> i32 {
    x + 1
}
```
