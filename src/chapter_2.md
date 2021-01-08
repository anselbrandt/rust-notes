## Variables and Mutability

### Mutability

```rust,ignore
fn main() {
    let mut x = 5;
    println!("The value of x is: {}", x);
    x = 6;
    println!("The value of x is: {}", x);
}
```

### Constants

```rust,ignore
const MAX_POINTS: u32 = 100_000;
```

### Shadowing

```rust,ignore
fn main() {
    let x = 5;

    let x = x + 1;

    let x = x * 2;

    println!("The value of x is: {}", x);
}
```

Shadowing permits type mutation:

```rust,ignore
 let spaces = "   ";
 let spaces = spaces.len();
```
