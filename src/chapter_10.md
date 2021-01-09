## Methods

### Defining Methods

Methods are defined within `impl` blocks. Structs can have multiple `impl` blocks.

```rust,ignore
struct Rectangle {
    width: u32,
    height: u32,
}

impl Rectangle {
    fn area(&self) -> u32 {
        self.width * self.height
    }
}

fn main() {
    let rect1 = Rectangle {
        width: 30,
        height: 50,
    };

    println!(
        "The area of the rectangle is {} square pixels.",
        rect1.area()
    );
}
```

> Rust uses _automatic referencing_ and _dereferencing_ when calling methods.
> When you call a method with `object.something()`, Rust automatically adds in `&`, `&mut`, or `*` so object matches the signature of the method.
>
> ```rust,ignore
> p1.distance(&p2);
> (&p1).distance(&p2);
> ```
>
> Automatic referencing works because methods have a clear receiver—the type of _self_. Given the receiver and name of a method, Rust can figure out definitively whether the method is reading (_&self_), mutating (_&mut self_), or consuming (_self_).

### Methods with More Parameters

```rust,ignore
struct Rectangle {
    width: u32,
    height: u32,
}

impl Rectangle {
    fn can_hold(&self, other: &Rectangle) -> bool {
        self.width > other.width && self.height > other.height
    }
}

fn main() {
    let rect1 = Rectangle {
        width: 30,
        height: 50,
    };
    let rect2 = Rectangle {
        width: 10,
        height: 40,
    };
    let rect3 = Rectangle {
        width: 60,
        height: 45,
    };

    println!("Can rect1 hold rect2? {}", rect1.can_hold(&rect2));
    println!("Can rect1 hold rect3? {}", rect1.can_hold(&rect3));
}
```

### Associated Functions

Associated functions are often used for constructors that will return a new instance of the struct.

```rust,ignore
impl Rectangle {
    fn square(size: u32) -> Rectangle {
        Rectangle {
            width: size,
            height: size,
        }
    }
}
```

The `square` function is namespaced by the struct and called with the `::` syntax: `let sq = Rectangle::square(3);`
